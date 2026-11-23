Title: Parallelism moves the bottleneck

[Read HTML](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/parallelism-moves-the-bottleneck/)

Author: Harsh Joshi

<a id="parallelism-moves-the-bottleneck"></a>

# Parallelism moves the bottleneck

A model does not fit on one device. Adding another seems obvious, until we ask what the two devices should share: a copy of the model, its state, parts of a layer or successive stages of the computation.

Each arrangement makes a different resource available. It also creates a different conversation between devices. More memory can make the experiment possible while the new exchanges make it slow; a faster division can make recovery harder. Parallelism is interesting because it changes the shape of the work, not merely the number of machines doing it.

<a id="copies-state-and-model-size"></a>

## Copies, state and model size

In ordinary data-parallel training, workers process different portions of the data with copies of the model, then coordinate the updates. That can increase the amount of data processed per step. It does not, by itself, make a model fit when the state of each full copy exceeds a device's memory. The state matters. Parameters are not the whole training footprint: gradients, optimiser state and activations also consume memory. A model-size comparison that counts only parameter bytes can therefore predict a feasible run that cannot actually start.

The [ZeRO paper](https://arxiv.org/abs/1910.02054) addresses redundant model state through partitioning across workers. That provides a different route from simply keeping full copies everywhere. Its value comes from the memory and communication trade, not from a general promise that sharding removes every bottleneck.

Consider a stipulated mixed-precision training layout for one billion parameters: two bytes each for working parameters and gradients, four for a master parameter copy, and four each for two optimiser moments. That is 16 billion bytes, or about 14.9 GiB, before activations, buffers and temporary workspace. Ordinary data parallelism retains that state on each worker. Ideally partitioning just the master copy and optimiser moments across four workers reduces this part of each worker's accounting to 4 + 12/4 = 7 billion bytes. It does not divide every byte of the actual peak by four. State must still be exchanged when needed, and the activations have not disappeared. The example describes an accounting layout, not the memory guarantee of a particular framework.

<a id="splitting-a-layer-makes-communication-more-frequent"></a>

## Splitting a layer makes communication more frequent

Tensor parallelism divides work within model layers. The resulting pieces need to exchange information as the layers execute. The relevant topology is therefore the one used repeatedly within a step, not merely the route used once to load the model.

Pipeline parallelism divides the model into stages. Data passes through those stages, and a schedule keeps different portions of the batch moving. Stage imbalance and the periods spent filling and draining the pipeline can leave devices waiting. A model that fits across stages can still use the devices poorly.

Even a forward-only toy pipeline shows the scheduling cost. With four equal stages, eight microbatches and one time unit per stage, the last microbatch exits after 8 + 4 - 1 = 11 units. Useful work occupies 32 of the 44 available stage-time slots, about 73%. This is not a training schedule, which must also place backward work and manage stored activations. It isolates the fill-and-drain loss: equal stages and perfect communication do not remove it, and an imbalanced stage makes the toy assumption less favourable.

The occupancy is visible in the schedule. Each number identifies a microbatch; a dot is an idle stage-time slot.

| Stage / time unit | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Stage 1 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | · | · | · |
| Stage 2 | · | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | · | · |
| Stage 3 | · | · | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | · |
| Stage 4 | · | · | · | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |

The twelve dots are not slow kernels. They come from the order in which work becomes available and leaves the pipeline. With m microbatches and the same four-stage assumptions, the occupied fraction is $m/(m+3)$. Sixteen microbatches would give 16/19, about 84%, but sending more pieces through this forward-only sketch does not settle the activation storage, backward schedule or batch-size consequences of real training. It reveals which loss the schedule creates before those other costs enter.

The [Megatron-LM large-scale training study](https://arxiv.org/abs/2104.04473) examines combinations of data, tensor and pipeline parallelism rather than treating them as interchangeable. Its reported system is evidence that a deliberate combination can scale. It is not a guarantee that a chosen combination will scale on another topology or workload.

| Division of work | What each worker holds or does | Coordination introduced |
| --- | --- | --- |
| Data parallel | A model copy processing different examples | Combine updates across replicas |
| State sharding | A partition of selected model state | Gather or exchange the state required for the next computation |
| Tensor parallel | A portion of a layer's computation | Exchanges inside the layer's execution |
| Pipeline parallel | Successive model stages | Activation transfer and a schedule across stages |

These descriptions expose why the choices can be combined. They divide different objects. A proposal to “split across eight GPUs” remains incomplete until it says which of these objects is split and where the resulting exchanges run.

<a id="the-constraint-determines-the-useful-division"></a>

## The constraint determines the useful division

Suppose a job fails because optimiser state exhausts memory. A state-sharding approach directly addresses that constraint. Suppose instead that activations dominate at the required sequence length. The same change may leave the main problem intact; recomputation, activation handling or another division of the work might need investigation. Now suppose a fitting model spends much of each step waiting for communication. Increasing the number of workers can make the situation worse. A memory solution can become a communication problem, just as a communication-saving choice can retain more memory. These are illustrative diagnoses, not recommended configurations for a particular model.

An experiment can isolate the constraint by holding the model, data and acceptance conditions stable while changing the division. Memory, step time and the full run then reveal different consequences of that change. A successful first step makes a fitting arrangement worth investigating further, including the checkpoint and recovery costs that appear later.

<a id="from-fast-steps-to-learning"></a>

## From fast steps to learning

Changing batch sizes and schedules can change how training progresses. A comparison based only on step time can reward a configuration that needs more steps or reaches a different quality result. The relevant endpoint is the agreed experiment, not the fastest isolated loop. There are two legitimate measurements here. A controlled systems comparison can hold a workload fixed and measure execution. An end-to-end training comparison can ask how long each configuration takes to reach a quality condition. Neither should borrow the other's conclusion without the missing evidence.

<a id="recovery-is-part-of-the-design"></a>

## Recovery is part of the design

The way state is divided also affects how it is checkpointed and restored. A checkpoint is useful only if the intended recovery path can consume it. Restarting with another device count, topology or environment may need support that an ordinary same-shape restart does not prove. That matters when [capacity ends with its window](https://rawthoughts.in/collections/useful-compute/a-capacity-promise-needs-a-clock/). A configuration that squeezes into memory and runs quickly can still be a poor procurement choice if it cannot preserve progress before that window ends.

Parallelism is best understood as a set of explicit trades between memory, communication, scheduling and recovery. Once those trades are visible, [efficiency](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/a-busy-gpu-is-not-an-efficient-model/) becomes something to investigate rather than a percentage to imitate.


Reading path: [Useful compute](https://rawthoughts.in/collections/useful-compute/) > [Making the cluster useful](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/) > [Parallelism moves the bottleneck](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/parallelism-moves-the-bottleneck/)

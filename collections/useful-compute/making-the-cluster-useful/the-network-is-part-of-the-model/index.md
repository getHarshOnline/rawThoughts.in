Title: The network is part of the model

[Read HTML](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/the-network-is-part-of-the-model/)

Author: Harsh Joshi

<a id="the-network-is-part-of-the-model"></a>

# The network is part of the model

Imagine sixteen fast accelerators waiting on one another. Nothing in their individual specifications explains why the combined machine is slow. The missing description is how the work travels among them.

Once a model is distributed, a transfer can sit inside every layer or happen only at the end of a batch. A short synchronisation repeated thousands of times can matter more than an impressive transfer of one giant buffer. The network becomes part of the model's operating proposition through these patterns: not part of its learned parameters, but part of the system that turns those parameters into a completed experiment.

<a id="not-every-transfer-uses-the-same-path"></a>

## Not every transfer uses the same path

Communication within a host, between hosts, to storage and to the user can traverse different links. A fast link inside a server does not establish the rate between servers. An aggregate node figure does not establish the capacity of every path, especially under contention. The same nominal link rate can also carry different workloads. Many small operations expose latency and coordination overhead. Large transfers expose sustained bandwidth. A topology that looks strong under one test can be weak at the sizes and patterns used by a particular training step.

Consider a hypothetical job that repeats a short synchronisation thousands of times. Reducing transfer time for one giant buffer may barely improve it. Conversely, a job dominated by large exchanges may care much more about sustained bandwidth than the time of one tiny operation. The useful benchmark reproduces the pattern that consumes the workload's time.

<a id="collective-bandwidth-needs-its-own-interpretation"></a>

## Collective bandwidth needs its own interpretation

Distributed training often uses collective operations, in which a group coordinates a reduction or exchange. The output size of the operation is not always the total traffic that traverses the links. [NVIDIA's NCCL tests documentation](https://github.com/NVIDIA/nccl-tests/blob/master/doc/PERFORMANCE.md) distinguishes algorithm bandwidth, the operation's data size divided by time, from bus bandwidth, which applies an operation-dependent correction. For all-reduce the correction includes the number of ranks. Neither value should be read as a raw internet speed or compared indiscriminately with an unrelated aggregate hardware figure.

The benchmark needs its operation, message sizes, rank count, placement and configuration. Without them, a large number is difficult to reproduce and almost impossible to interpret. A chart of peak bandwidth can be useful evidence, but it is not yet a claim about training time.

For the all-reduce convention in the same NCCL tests documentation, let S be the operation's byte count, t its measured duration and n its ranks. Then:

$$
B_{\text{algorithm}}=\frac{S}{t},\qquad
B_{\text{bus}}=\frac{S}{t}\frac{2(n-1)}{n}.
$$

An illustrative one-GB operation taking 0.02 seconds has algorithm bandwidth 50 GB/s. With four ranks the correction is 1.5, giving 75 GB/s bus bandwidth. Those are two descriptions of the same stipulated operation, not two measured links. Changing the collective changes the correction; changing message size can change how much fixed overhead matters.<sup><a id="fnref-note-6e63636c"></a>[1](#fn-note-6e63636c)</sup>

<a id="the-physical-path-beneath-the-library"></a>

## The physical path beneath the library

When communication is slow, a software switch may help. It may also conceal a bad link, an unexpected route or a placement problem. [NVIDIA's performance guidance](https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/troubleshooting/performance_and_tuning.html) separates low-level bandwidth checks from NCCL-level behaviour. The order is useful: establish what the selected physical paths can deliver, then investigate how the collective library uses them. A diagnostic should retain enough configuration to make the result comparable. If node placement or software versions change between runs, an apparent tuning gain may have another explanation. If a test fails, keep the failure rather than averaging only the successful runs.

No single library test verifies the complete workload. The next step is a representative training step, with its data path and communication overlap, followed by enough of the run to expose stability and recovery. Each layer answers a narrower question that supports the next one.

<a id="topology-and-parallelism-must-be-chosen-together"></a>

## Topology and parallelism must be chosen together

If parts of each model layer need frequent exchanges, placing them across a slow boundary can impose that boundary repeatedly. If the work can be grouped so that most frequent exchanges stay local, a different division may perform better. But changing the division can increase memory, alter scheduling or create other communication.

That is why [parallelism moves the bottleneck](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/parallelism-moves-the-bottleneck/). A topology is not good in isolation. It is good for the ways the workload uses it. A procurement comparison should connect those two descriptions before deriving a completion time from a device count.

<a id="the-job-is-the-final-test"></a>

## The job is the final test

A bandwidth test tells us something about an operation under specified conditions. A workload test tells us how that operation interacts with computation and other dependencies. An accepted output tells us whether the faster system still completed the intended work. The connected measurements make an improvement intelligible. A stronger physical path matters through the exchanges it accelerates; faster exchanges matter through the workload they help complete. The network is part of the model's operating proposition because this chain connects a hardware choice to the experiment someone actually wants to finish.

1. 
   
   <a id="fn-note-6e63636c"></a>
   
   [NCCL tests' operation-specific definitions](https://github.com/NVIDIA/nccl-tests/blob/master/doc/PERFORMANCE.md). [↩](#fnref-note-6e63636c)


Reading path: [Useful compute](https://rawthoughts.in/collections/useful-compute/) > [Making the cluster useful](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/) > [The network is part of the model](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/the-network-is-part-of-the-model/)

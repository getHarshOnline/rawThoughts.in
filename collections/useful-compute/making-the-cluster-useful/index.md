Title: Making the cluster useful

[Read HTML](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/)

Author: Harsh Joshi

A model finally fits across the devices, but the run barely advances. The memory problem was real; solving it exposed a different limit. This is what makes a cluster more interesting than a multiplication of accelerator specifications: its parts have to carry one computation together.

[The division of work](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/parallelism-moves-the-bottleneck/) determines which exchanges happen inside a step. [Their physical paths](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/the-network-is-part-of-the-model/) determine where that step waits. Saving memory by recomputing activations can add activity without adding the same amount of [model progress](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/a-busy-gpu-is-not-an-efficient-model/). Each change solves a particular problem and changes what the next measurement means.

The useful comparison follows those changes through the same experiment: can it fit, advance, preserve progress and reach the intended quality? The experiment's design remains part of that question. [Model size and training exposure](https://rawthoughts.in/blog/what-should-a-training-budget-buy/) decide what work the cluster receives. [A changing learner receiving distributed trajectories](https://rawthoughts.in/blog/distributed-rollouts-and-the-learning-loop/) adds a reason that genuinely completed work might no longer be useful. A faster cluster matters through the learning it can carry, not through a percentage detached from that purpose.


Reading path: [Useful compute](https://rawthoughts.in/collections/useful-compute/) > [Making the cluster useful](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/)


## Collection contents

- [What is the GPU busy doing?](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/a-busy-gpu-is-not-an-efficient-model/)
- [The network is part of the model](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/the-network-is-part-of-the-model/)
- [Parallelism moves the bottleneck](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/parallelism-moves-the-bottleneck/)

Title: What should a training budget buy?

[Read HTML](https://rawthoughts.in/blog/what-should-a-training-budget-buy/)

Author: Harsh Joshi

<a id="what-should-a-training-budget-buy"></a>

# What should a training budget buy?

A training budget does not buy model size alone. It buys a combination of the model being trained and the amount of training it receives. Making the model larger spends more of the budget on each token, leaving fewer tokens available within the same computational limit. This is a different question from making an existing run execute efficiently. Before asking how quickly a cluster can perform the work, we have to decide which work should occupy the budget. A well-executed experiment can still be an unhelpful allocation between size and training exposure.

This is one technical question within [Beyond the Mirage’s wider argument about intelligence](https://causality.in/blog/beyond-the-mirage/) (on Causality). That essay asks what scaling can and cannot establish about causal understanding. Here the question is narrower: given a fixed budget and a specified objective, how should we divide the training work? A result about that allocation does not settle the wider architectural proposal.

<a id="the-important-comparison-holds-compute-fixed"></a>

## The important comparison holds compute fixed

Hoffmann and colleagues' 2022 [Chinchilla paper](https://arxiv.org/abs/2203.15556) investigated how to allocate a fixed training-compute budget between parameter count and training tokens. Their empirical fits favoured increasing both in roughly equal proportions as the budget grew. They tested the prediction with a 70-billion-parameter model trained on 1.4 trillion tokens, reporting better performance than the much larger Gopher under a comparable training budget.

The finding changes how a training investment can be described. Parameter count alone misses the exposure that lets a model use its capacity. The result is an empirical allocation rule under the paper's conditions, with concrete limits: two comparable large-scale runs, an assumed power-law frontier and experiments processing less than one epoch of the available data. Repeated passes through a limited corpus introduce a different condition, while a different architecture or objective may produce a different frontier.

<a id="three-ways-to-spend-the-same-simplified-budget"></a>

## Three ways to spend the same simplified budget

For a deliberately simplified dense-transformer example, approximate model training work as:

$$
C \approx 6ND, \qquad D \approx \frac{C}{6N}.
$$

Here C is a count of floating-point operations, N is the parameter count and D is the number of training tokens processed. This common approximation is compared with a more detailed operation count in the [paper's Appendix F](https://arxiv.org/html/2203.15556v1).

**Note**

**This approximation is not a universal formula for every architecture or a measurement of hardware energy and elapsed time.**

For an illustrative budget of $3.6\times10^{21}$ operations, ignoring the differences the approximation leaves out, these three allocations fit it:

| Illustrative allocation | Parameters | Training tokens processed | Approximate training work |
| --- | --: | --: | --: |
| Smaller model, longer exposure | 3 billion | 200 billion | 3.6 × 10²¹ operations |
| Middle allocation | 6 billion | 100 billion | 3.6 × 10²¹ operations |
| Larger model, shorter exposure | 12 billion | 50 billion | 3.6 × 10²¹ operations |

For the first row, $6\times(3\times10^9)\times(200\times10^9)=3.6\times10^{21}$. Doubling N and halving D leaves that product unchanged. The final row spends four times as much per token on parameter-dependent work as the first, but processes one-quarter as many tokens.

The three rows are equally expensive under this approximation. What makes the choice interesting is the missing quality curve: the table contains no measured loss from which to choose an optimum. Its apparently balanced middle row has no special claim on the budget, and its largest model has given up three-quarters of the smaller model's exposure.

<a id="a-budget-constraint-cannot-supply-the-missing-quality-curve"></a>

## A budget constraint cannot supply the missing quality curve

To choose an allocation, we need evidence about how performance changes with both variables under the intended training conditions. We also need an objective. Lower predictive loss on one distribution, better performance on a particular downstream task and lower cost for an accepted deployed response are different targets.

The quality curve could favour a smaller model that receives enough useful exposure over a larger one whose capacity remains undertrained. But if the material is poorly matched to the intended task, increasing exposure may buy repetition rather than the missing behaviour. These possibilities explain why an experiment needs both a defined objective and data suited to it; the arithmetic alone cannot distinguish them.

Experiments should distinguish allocation changes from other changes. If the learning-rate schedule, dataset mixture or evaluation also changes, an improved score cannot be attributed to size and token count alone. A small-scale result can guide a larger experiment, but the extrapolation still needs to be examined at the new scale.

<a id="a-token-count-does-not-describe-the-data"></a>

## A token count does not describe the data

D counts exposure in this simplified account. It does not tell us how many distinct, relevant examples the model encountered. Repeating the same material can increase processed tokens without increasing the diversity of information in the same proportion. The tokenizer and mixture also matter to interpretation. Two corpora with the same token count can represent different languages, structures and tasks. The comparison needs a permitted corpus whose contents support the intended use, and an evaluation independent of the training material. Only then does a token count describe exposure worth allocating compute to.

<a id="equal-model-work-does-not-mean-equal-wall-clock-cost"></a>

## Equal model work does not mean equal wall-clock cost

The three illustrative rows may fit the same operation budget while interacting differently with memory, communication and scheduling. One model may require a different division across devices. One configuration may run its operations more efficiently. Setup, checkpointing and recovery can change the time needed to complete the experiment.

[Model FLOPs utilisation](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/a-busy-gpu-is-not-an-efficient-model/) measures the rate of defined model work against a stated capacity benchmark. The allocation question concerns which model work is worth executing. An improvement in the first can enlarge what fits a time window, but it does not by itself establish the best answer to the second. A budget expressed as money or a booked period therefore needs another translation. The nominal operations the hardware could perform are not the operations the completed experiment will actually obtain. That translation should be measured rather than hidden inside the word "compute".

<a id="the-deployed-model-has-a-different-budget"></a>

## The deployed model has a different budget

Suppose two training candidates both meet the application's quality requirement, but one is cheaper to serve repeatedly. Its deployment advantage may justify a training choice that does not minimise pre-training loss per training operation. Conversely, a candidate with excellent training efficiency may fail the application's required behaviour or response time.

The problem changes when the objective includes repeated use. Training may happen once; the service may answer many requests. How many, with what lengths, latency and quality, affects the comparison. The cost of [serving those requests](https://rawthoughts.in/blog/serving-tokens-is-a-service-problem/) depends on their arrival pattern, live memory and the capacity held ready for them, not just the model's token throughput.

Training allocation is therefore connected to the life of the model after training. A model that meets the required quality with a smaller serving footprint may repay its training investment over millions of requests. A larger model may justify its cost through behaviour the smaller one cannot supply. The useful frontier is the one defined by that objective, the available data and the operating conditions, not by parameter count in isolation.

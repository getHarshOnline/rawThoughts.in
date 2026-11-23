Title: What is the GPU busy doing?

[Read HTML](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/a-busy-gpu-is-not-an-efficient-model/)

Author: Harsh Joshi

<a id="what-is-the-gpu-busy-doing"></a>

# What is the GPU busy doing?

The GPUs are busy, the model is progressing slowly, and much of the fleet has no paying work. There is no contradiction in that picture. Each observation follows a different part of the system.

A utilisation dashboard becomes useful when it lets us decide where to intervene. Is time disappearing into data movement? Is the device repeating operations to save memory? Is an efficient run surrounded by long periods without a job? The answer changes whether we should improve the workload, alter its placement or find a better way to use the capacity we already hold.

<a id="activity-recomputation-and-model-progress"></a>

## Activity, recomputation and model progress

A device-activity measure can tell us that work was running. It does not by itself tell us whether the work was useful, whether the arithmetic units were near their relevant limit or whether the completed result was acceptable. For training, a bottleneck may sit in the input pipeline, memory traffic, communication or kernel execution. An active device might be doing extra computation to reduce memory use. That can be a sensible trade even though more of its work does not directly advance the model's required forward and backward passes.

The [PaLM paper's training-efficiency discussion](https://arxiv.org/html/2204.02311v5) makes this distinction explicit. Model FLOPs utilisation, or MFU, relates achieved token throughput to a theoretical rate based on the model's required operations and the system's peak. Hardware FLOPs utilisation also counts implementation work such as recomputation. PaLM reported 46.2% MFU and 57.8% hardware FLOPs utilisation for its 540B run. The two values describe different quantities, not conflicting measurements of the same one.

With P denoting the selected system's peak FLOPs per second, F the defined model FLOPs per token and r the achieved tokens per second, the accounting can be written as:

$$
\mathrm{MFU}=\frac{rF}{P},\qquad
\mathrm{HFU}=\frac{r(F+F_{\text{extra}})}{P}.
$$

Here the second expression adds implementation work per token, such as recomputation. It explains why a memory-saving implementation can raise hardware activity without producing a corresponding rise in the model's useful progress. The selected definitions of F and P remain part of the comparison.

For a stipulated workload, let the system peak at 100 trillion FLOPs per second at the selected precision, let the model require one billion FLOPs per token, and let the run achieve 40,000 tokens per second. Its model work is 40 trillion FLOPs per second, giving 40% MFU. If the implementation repeats another half-billion FLOPs per token to save memory, its accounted work rises to 60 trillion FLOPs per second and HFU to 60%. The run still advances at 40,000 tokens per second. The extra activity bought a memory trade, not 20 percentage points of extra model progress.

<a id="the-denominator-has-to-match-the-experiment"></a>

## The denominator has to match the experiment

Comparing a rate with a hardware peak requires the relevant arithmetic precision and operation assumptions. Dense and sparse peaks are not interchangeable. A model's architecture and sequence length also affect the calculation of its required operations. A convenient formula is not a universal account of every training workload.

The comparison must preserve the experiment. If a configuration processes more tokens by changing sequence lengths, quality conditions or the training plan, the resulting rate is not automatically an improvement for the original job. Faster execution is useful only when the work being executed remains the work we need. This is also why one published run should not become a universal procurement threshold. It is evidence for that model, system, software and measurement. It can motivate a test on another system; it cannot replace the test.

<a id="relative-improvement-and-cost-reduction-are-different"></a>

## Relative improvement and cost reduction are different

Take an arithmetic illustration in which the same workload on the same paid hardware moves from 40% to 50% MFU. Under fixed model work and otherwise unchanged conditions, throughput rises by 25%, because 50 divided by 40 is 1.25. Time falls by 20%, because the reciprocal is 0.8. Those are not two ways of saying a 25% cost reduction. If accelerator billing is proportional to run duration, the accelerator charge can fall with that time. A prepaid window may not yield an immediate cash saving, though it can free time for another experiment. Setup, storage and engineering costs may remain unchanged. The performance claim and the financial consequence therefore need separate calculations.

$$
\frac{r_{\text{new}}}{r_{\text{old}}}=\frac{0.50}{0.40}=1.25,
\qquad
\frac{T_{\text{new}}}{T_{\text{old}}}=\frac{0.40}{0.50}=0.80.
$$

<a id="fleet-occupancy-asks-another-question"></a>

## Fleet occupancy asks another question

A supplier can keep most of its devices allocated while customers run inefficient jobs. A customer can run an efficient model on a fleet that spends much of the month unallocated. The supplier's capacity planning and the customer's optimisation need different interventions.

Multiplying occupancy by a training-efficiency ratio can sometimes help build a deliberately defined aggregate model. It does not create a new observed quantity, and it is misleading if the workloads or time boundaries differ. A mixed fleet running training, inference and other tasks needs more than one model of useful output.

<a id="efficiency-as-an-operating-question"></a>

## Efficiency as an operating question

A low efficiency measure opens an operating question: where does the workload spend time, and what changes that path? Comparing the same work and quality condition after one justified change can reveal the contribution of [communication](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/the-network-is-part-of-the-model/) or [parallelism](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/parallelism-moves-the-bottleneck/). The useful intervention follows the measured constraint.

For serving, the question changes again. A configuration can improve aggregate throughput while making individual users wait too long. [Service conditions](https://rawthoughts.in/blog/serving-tokens-is-a-service-problem/) belong alongside the rate. The ambition should be more useful completed work from the same resources. A higher percentage helps only when it makes that ambition measurable rather than replacing it.


Reading path: [Useful compute](https://rawthoughts.in/collections/useful-compute/) > [Making the cluster useful](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/) > [What is the GPU busy doing?](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/a-busy-gpu-is-not-an-efficient-model/)

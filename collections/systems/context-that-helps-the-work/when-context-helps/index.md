Title: When context helps

[Read HTML](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/)

Author: Harsh Joshi

<a id="when-context-helps"></a>

# When context helps

A context system learns very little from knowing that an agent opened a document. The document might have resolved an uncertainty, confirmed something already known or supplied a convincing distraction. The agent might quote it because it helped, or because it was the only thing returned. Useful memory begins with a harder question: what difference did this context make to the work?

That question drives the learning design for [Scope](https://rawthoughts.in/scope/). The aim is a system that gets better at choosing a small, useful account of a task, without accumulating every previous selection as evidence that the selection was good. Retrieval is part of a larger process. Its value appears in the understanding, decision or completed work that follows.

<a id="four-events-four-possible-stories"></a>

## Four events, four possible stories

Imagine a support task. A product rule is required context. Two optional sources are also eligible: a recent troubleshooting note and a worked example for a particular device. The system returns the rule and the note; the agent reads both, quotes the note and resolves the issue.

The record establishes that the note was offered, consumed and mentioned. A separately observed resolution establishes that the task ended successfully. It does not yet establish that the note caused the success. The agent may already have known the answer. The note may have been redundant with the rule. The unseen device example may have led to the same result more quickly.

Those alternatives matter to learning. A model trained to predict what the incumbent retrieves can reproduce the incumbent's habits, including its mistakes. A model trained on mentions can reward sources that are easy to quote. A model trained on consumption can favour attractive opening material over the quiet qualification that prevents an error. Each target is learnable; none is automatically the target we wanted.

The record therefore needs the eligible alternatives and the information available when the choice was made, alongside the later use and outcome. An unselected item remains an unobserved alternative, not a failed source. The timing also matters: a feature known only after the task ended cannot explain a choice that must be made before it begins.

For this task, a compact learning record would retain these separate observations:

| At selection time | During the attempt | At evaluation |
| --- | --- | --- |
| Required product rule; eligible note and device example; chooser and its choice probability where defined | Returned bundle; passages consumed; passages mentioned | Resolution result; independently checked errors; elapsed time and resources |

The chooser needs a record too. A deterministic rule selecting the note every time gives that choice probability one and the alternative zero. An experiment could deliberately give each alternative a nonzero chance of selection, after deciding which tasks and assignments are safe to try. These histories support different comparisons even if both end with a successful task.

<a id="the-missing-observation"></a>

## The missing observation

Suppose the same deterministic rule always returns the troubleshooting note for this kind of task. A thousand successful cases can tell us something about that complete workflow. They cannot show what those cases would have looked like with the device example instead. There are no outcomes for that choice in those cases.

Off-policy evaluation studies precisely this partial-feedback problem: using decisions made by one policy to assess another. [Li and colleagues' offline evaluation work](https://arxiv.org/abs/1003.5956) uses randomised logging to make a principled comparison possible. [Wang, Agarwal and Dudík](https://proceedings.mlr.press/v70/wang17a.html) examine the statistical limits and trade-offs of contextual-bandit evaluation. A retrieval bundle is more complicated than choosing one news article, so the assumptions and action definition cannot simply be borrowed unchanged.

The elementary obstacle survives that difference. In an inverse-propensity calculation, an observed outcome is weighted according to how likely its action was under the logging policy. If an alternative had zero probability of being selected, weighting cannot manufacture an observation of it. Better estimators can address some variance or modelling problems; they do not turn a never-tried alternative into an independently observed outcome.

<a id="a-comparison-small-enough-to-understand"></a>

## A comparison small enough to understand

One candidate need not be a neural model. A simple baseline can score an eligible item by recency times the logarithm of one plus its previous retrieval count. That rule gives a never-retrieved item zero even when it is fresh: a concrete cold-start behaviour to compare, rather than a vague claim that popular material is helpful. The recency function and candidate-time counts must be fixed for the experiment.

Scope's initial design, A-MAC-lite, instead combines a content-kind prior, access recency, a declining novelty boost and a multiplier from accepted reports of use. That makes its preference inspectable, but does not turn the ranking into a probability of truth or usefulness. Four reports of use are not evidence that an item caused four successes. Neither access recency nor the score can restore an expired source to eligibility.

A moving-average candidate goes further by updating utility from a declared credit and outcome feature. It would make a preference based on reported use and an outcome-attribution rule compete on the same tasks. Mentions, controlled ablations and owner-observed outcomes supply different grounds for credit; none should quietly replace the others. The task outcome remains a vector of observations. Reducing it to one feature is a particular experiment's choice, not a declaration that every successful task is worth one. A scorer that learns the wrong reduction can become very good at choosing context for the wrong objective.

A first experiment could hold the required product rule fixed and compare the optional context on a fixed set of tasks whose owners permit the experiment. One arm uses a simple recency-and-frequency score; another uses the proposed richer scorer. Both receive the same source population, task conditions and context budget. The required rule is not sacrificed to create an impressive token saving.

In a controlled offline setting, the task can be rerun with different optional bundles. That directly measures the selected agent's behaviour in that setting. It is stronger evidence than rescoring yesterday's choices, but still depends on the task sample, executor, evaluation and fidelity of the replay. In a live setting, deliberate exploration needs its own safe assignment design; the fact that an alternative is eligible does not make every experiment with it harmless.

The outcome is more informative as several observations than as one triumphant score. Did the issue resolve? Did an independent check find an error? How much time and resource did it take? Was essential information lost? A faster answer that fails on the difficult device is a different trade-off from an equally correct answer that saves time everywhere. The comparison needs enough separation to see which one happened.

It also needs new situations. A scorer can learn one operator's language or recognise near-duplicate tasks without learning a useful retrieval rule. Future time windows and held-out operators test that dependence. If the simpler scorer performs equivalently under the relevant conditions, extra learning machinery has not earned its cost.

<a id="a-memory-that-becomes-more-useful"></a>

## A memory that becomes more useful

More elaborate ranking, credit assignment or history models become interesting when a simpler method leaves a specific failure unexplained. Perhaps the value of a source depends on the preceding context, or a short sequence reveals that a recurring answer has stopped helping. That is a reason to test a richer representation, not an automatic promotion from a good replay to a self-changing memory.

[Reckon’s completed selective-memory comparisons](https://causality.in/collections/evidence-and-evaluation/from-observation-to-evaluation/what-did-selective-memory-buy/) (on Causality) make the cost of choosing visible. A policy improved over learned utility in one workload while losing to no memory; in another, it matched a simpler policy’s wins after paying for thousands of extra replays. The work spent deciding what to remember belongs in the comparison too.

Those results give Scope questions to test on its own tasks. Scope would propose a retrieval change; an evaluation and its owner’s decision would precede any release of that change. Ordinary strict retrieval need not wait for an evaluation service to be online.

The resulting memory would preserve a productive distinction: a source can be frequently useful without being true in every setting, and rarely used while remaining indispensable for a particular decision. [Eligibility](https://rawthoughts.in/collections/systems/context-that-helps-the-work/finding-the-right-context-for-the-work/) determines what may enter the comparison. Evidence from the work determines what the comparison can teach. The gain is not a larger history of reading; it is a shorter, better-grounded route through the next task.


## Article notes

<a id="gazette-notes-three-scores-for-an-eligible-source"></a>

## Three scores for an eligible source

A score can be easy to calculate while carrying a quite different idea of usefulness from its competitors. These worked examples expose that difference. The inputs are stipulated, not measured retrieval results. Eligibility is settled before any of these calculations: an expired or excluded source cannot re-enter the response by scoring well.

<a id="gazette-notes-recency-and-frequency"></a>

### Recency and frequency

The simple baseline is recency times the logarithm of one plus the previous retrieval count. For a recency value of 0.5 and three prior retrievals:

$$
b=0.5\ln(1+3)\approx0.693.
$$

An item with recency 1 and no retrievals scores zero under this formula. That is its cold-start behaviour, not proof that the item cannot help. The recency function and candidate-time counts are part of the experiment's fixed definition.

<a id="gazette-notes-a-mac-lite-s-components"></a>

### A-MAC-lite's components

Scope's proposed defaults give a transaction item prior 0.5 and a 30-day access half-life. Give an eligible item thirty days since access, two prior retrievals and four accepted reports that the item was used. Its recency is 0.5, novelty is $1-2/5=0.6$, and support from those reports is $4/10=0.4$. The raw score becomes:

$$
s=0.5\times0.5\times(1+0.3\times0.6)\times(0.5+0.5\times0.4)=0.2065.
$$

Dividing by the configured maximum 1.3 gives approximately 0.159. That is a ranking value, not a probability that the source is true or helpful. Normalisation belongs to this active configuration; a different prior or weight changes its maximum. The reported-use multiplier is narrower than outcome utility: four reports of use do not establish four caused successes.

**Note**

**The illustrative baseline value and this normalised score are not comparable magnitudes.** They arise from different rules and scales. The useful comparison is the bundles they select under the same conditions and what happens in the ensuing work.

<a id="gazette-notes-a-moving-average-utility"></a>

### A moving-average utility

Scope's proposed comparison includes a moving-average candidate referenced from Reckon's research:

$$
u_{new}=(1-\eta)u_{old}+\eta\,c\,o,
\qquad \eta=0.1,
$$

with the result clamped to the unit interval. Here $c$ is the credit assigned under the experiment's rule and $o$ its specified outcome feature. With illustrative values $u_{old}=0.4$, $c=0.5$ and $o=1$, the next utility is $0.36+0.05=0.41$. If that outcome feature is zero, it becomes 0.36.

Neither update establishes causation. It shows how a declared attribution rule changes future preference. Mentions, controlled ablations and owner-observed outcomes can produce different credit, which is why the comparison preserves them separately. The task outcome remains a vector of relevant observations; reducing it to $o$ is this experiment's choice, not a universal definition of a successful task.



Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Context that helps the work](https://rawthoughts.in/collections/systems/context-that-helps-the-work/) > [When context helps](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/)

Previous in journey: [When an agent's context changes underneath it](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-changes/)


Source code for [Scope](https://github.com/getHarshOnline/scope) is credited to [Harsh Joshi](https://getharsh.in/about/).

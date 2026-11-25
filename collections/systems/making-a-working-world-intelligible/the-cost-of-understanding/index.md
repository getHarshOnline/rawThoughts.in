Title: The cost of understanding

[Read HTML](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/the-cost-of-understanding/)

Author: Harsh Joshi

<a id="the-cost-of-understanding"></a>

# The cost of understanding

Returning to a project can cost more than doing its next task. The relevant conversation is somewhere, a decision appears in three documents, and the implementation has moved since the explanation was written. Before acting, a person or agent has to reconstruct what belongs together and which version still matters. The next session may repeat most of that reconstruction.

The bet behind [Pale](https://rawthoughts.in/pale/) is that some of this work can be done once, represented explicitly and reused. A declared world would name the relationships and capabilities through which work proceeds; a connected history would preserve what happened and the grounds used. The question is whether that structure makes understanding cheaper without making the answer less faithful.

There is a concrete starting point in the work behind this system. On 14 August 2026, one reconstruction task took about 1.63 million tokens and 69 minutes in Codex's counters: reading conversations, source files and configuration, comparing the applications involved and developing an architectural account. Those are one task's counters, not a bill, and no matched run has been scored against them. They show the scale of the reconstruction that declared structure would have to reduce.

<a id="repeated-excavation-has-a-shape"></a>

## Repeated excavation has a shape

Imagine a hypothetical equipment purchase. A message asks for a comparison, a document contains a proposal, a later approval changes the budget and the supplier confirms only part of the delivery. Asked “what remains to be done?”, a fresh agent must discover all four sources, establish their order and understand what each event completed.

A shorter summary could answer quickly, but it may erase the partial delivery or mistake the original proposal for the current approval. An explicit account instead connects the proposal, its approving record and the particular delivery observation. It need not include every sentence from every conversation. It needs enough structure to recover the unresolved obligation and reach the sources that establish it.

That is a different kind of compression from merely shortening prose. Some detail can remain in its source while a typed relationship makes it easier to find. The gain comes from not having to rediscover the relationship, not from pretending the source no longer matters.

A publication gives another concrete case. An essay has its own argument, a product guide explains how to use the system it discusses, and a collection gives a reader a path through both. [Gazette](https://rawthoughts.in/gazette/) can carry declared relationships into navigation and machine-readable output. The writer still has to understand why those pieces belong together. If a product capability changes, the useful account should lead back to the claim and the explanations that depend on it.

That is part of the motivation for Pale: making the next investigation begin with the right connections. These publications, built with Gazette, give Pale a real task to be tested against.

<a id="preparation-has-to-be-repaid"></a>

## Preparation has to be repaid

Structure is not free. Someone has to identify the real objects, resolve ambiguous relationships and maintain the account as they change. A compiler can check declared structure; it cannot magically supply all the missing facts or decisions needed to declare it.

For a deliberately simple cost model, let B be preparation cost, E the cost of excavating one task from raw sources, R the cost of resolving it through the structure, and M(n) the maintenance cost incurred over n tasks. Structure saves resources when:

$$
\underbrace{B+nR+M(n)}_{\text{structured route}} < \underbrace{nE}_{\text{repeated excavation}},
\qquad n(E-R)>B+M(n).
$$

Assume, for illustration, that preparation costs 3,000 units of effort, excavation costs 600 per question and structured resolution costs 100. With five questions, the structured route costs 3,500 units before maintenance, against 3,000 for excavation. With ten, it costs 4,000 against 6,000; even 800 units of maintenance would leave a saving.

![Three curves compare cumulative effort for repeated excavation and reuse, with and without maintenance.](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/the-cost-of-understanding/preparation-and-reuse.svg)

Adding 80 units of maintenance per question moves the break-even point from six questions to just over seven. Counting whole questions, savings begin with the seventh without maintenance and the eighth with it.

A frequently reused relationship can repay careful preparation. A one-off question may not. A fast-changing source may consume the saving through maintenance. Different kinds of effort also need different measurements: fewer machine tokens can accompany more human work, and lower latency can require more background computation. A single cost figure should not conceal who paid it.

The comparison can keep those costs separate instead of inventing a common unit. Human preparation minutes, machine tokens, elapsed task time and consequential answer errors are four measurements. A structure that cuts machine consumption while requiring frequent human repair has redistributed effort; whether it is worthwhile depends on the people using it.

Discovery and understanding can move in opposite directions too. In the purchase example, one indexed lookup might return all four sources at once. That saves calls compared with finding each source separately, but leaves the agent to interpret the proposal, budget revision and partial delivery inside one larger result. A smaller response with the relevant relation and references might require a second lookup yet reduce the unresolved context. Count the calls, the material returned and the work needed to distinguish the events separately. None alone measures whether the agent understood what remained to be done.

<a id="a-cheaper-mistake-is-still-a-mistake"></a>

## A cheaper mistake is still a mistake

The real comparison is stricter than this arithmetic. Both routes have to answer the same questions from appropriately available evidence. If the structured route saves effort by leaving more facts unresolved, omitting a qualification or leaking another relationship's information, it has changed the quality of the answer rather than simply lowering its cost.

The purchase example makes a useful test. Can both routes identify the incomplete delivery, distinguish it from the accepted comparison and recover the changed budget? Can they find the relevant originals? What happens when the supplier corrects its record, when an authority changes or when a necessary source is absent? The structure earns its place through those cases as well as the ordinary answer.

This also makes room for a simpler competitor. A carefully maintained index and ordinary versioned links might solve the task adequately. The compiled world should be compared with that route, not only with a deliberately chaotic folder. A sophisticated structure is interesting if the typed relationships add a measurable advantage on the difficult cases, rather than merely making the easy ones look organised.

<a id="the-useful-boundary-of-a-compiled-world"></a>

## The useful boundary of a compiled world

A compiled world is fixed as one version, so a session has a definite configuration. It does not freeze the supplier's current state, prove every declaration true or prevent a source from changing. The relation between a stable configuration and moving evidence is part of the system's design. [A changed premise](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-changes/) must become visible at the point where the work relies on it.

This is why the bet matters beyond speed. Useful structure should reduce rediscovery and reveal contradictions: the delivery is partial, the budget moved, nobody accepted the next task. It can make the remaining uncertainty smaller and more actionable without claiming to have eliminated it.

The purchase is one recurring shape inside a larger world. The same person may also work across several companies, research projects and household responsibilities. Reusable structure can connect those pursuits while keeping their different relationships legible. The desired experience is being able to return anywhere in that world and continue from its present position, rather than reconstructing a new miniature world for every session.

An explicit representation is one way to make that understanding affordable. [HENA](https://causality.in/hena/) (on Causality) asks a further question about intelligence whose organisation can itself emerge and evolve. If such an architecture learns a better way to organise the problem, it may reduce work that today has to be described manually. The present comparison still matters: naturalness must come from a more useful representation, with enough fidelity to reveal what it has missed.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Making a working world intelligible](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/) > [The cost of understanding](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/the-cost-of-understanding/)

Next in journey: [How Pale fits together](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/)


Source code for [Pale](https://github.com/getHarshOnline/pale) is credited to [Harsh Joshi](https://getharsh.in/about/).

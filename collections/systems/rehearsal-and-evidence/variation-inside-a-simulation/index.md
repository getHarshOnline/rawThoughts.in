Title: What changes between rehearsals?

[Read HTML](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/variation-inside-a-simulation/)

Author: Harsh Joshi

<a id="what-changes-between-rehearsals"></a>

# What changes between rehearsals?

Twelve of twenty rehearsals produce an objection to a library's appointment system. Another set produces it only twice. What changed: the encounters inside the conversation, the way booking was described, or the assumptions about visitors' access?

These are hypothetical runs, and separating those possibilities is more interesting than turning twelve into an audience percentage. Repetition lets us inspect the simulator's behaviour. A changed premise lets us examine the mechanism that generated it. The two forms of variation can lead to quite different next questions for the actual library.

<a id="repetition-tests-a-setup"></a>

## Repetition tests a setup

Repeated runs can expose fragility. An objection that appears only once may warrant closer examination before it drives a decision. A recurring objection may indicate a persistent mechanism within the model and scenario. Neither recurrence nor disappearance proves the mechanism exists outside that setup. All twenty runs may share the same mistaken assumption, persona template or model bias. Independent random seeds do not make those shared premises independent. Even agreement between different models needs interpretation. They may share training influences or respond similarly to the framing. Agreement is useful evidence about robustness across the selected implementations; it is not automatically evidence of real-world validity.

<a id="sensitivity-to-a-changed-premise"></a>

## Sensitivity to a changed premise

Sensitivity analysis asks a different question from another random run. What happens if appointment booking is optional rather than mandatory? What happens if the scenario makes walk-in capacity explicit? Those changes alter a meaningful premise. The [interaction rules](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/how-opinions-move/) are also premises: changing who hears whom or how strongly an agent retains its starting view changes the mechanism, not just the seed.

A comparison needs both configurations and the observations each produced. [RawFish](https://rawthoughts.in/rawfish/)’s planned workbench preserves a base run when it creates a statistical variant, while Findings separates the settings difference from the evidence difference. Changing the scenario itself and full sensitivity analysis are distinct later capabilities, not consequences of a re-seed button.

The altered configuration should be recorded and actually rerun. A formula that adjusts a result after the fact is not equivalent to observing the system under the changed condition. If two premises interact, changing each separately may also miss the effect of changing them together. This matters because the question is explanatory. We want to know which assumptions drove the objection, not simply produce a wider spread of numbers. If a wording change reverses the apparent conclusion, that may reveal prompt sensitivity rather than a genuine policy trade-off.

For the library, an interpretable comparison separates what is held still from what changes:

| Comparison | Kept fixed | Changed | Question it can examine |
| --- | --- | --- | --- |
| Repeated setup | Policy, cohorts and interaction rules | Encounter seeds | Does the objection recur under this setup? |
| Policy contrast | Matched cohorts and declared interaction rules | Optional versus mandatory booking | Is the objection sensitive to the booking requirement? |
| Mechanism contrast | Policy and starting assumptions | Influence edges or anchoring | Which assumed social mechanism makes it persist? |

Matched seeds can reduce one source of variation in a contrast, but they do not make two different generated conversations identical. The observations still need to come from the altered run. A count such as twelve out of twenty belongs beside its setup, not above it as an estimate of visitors.

For a concrete policy contrast, predeclare the outcome as the coded occurrence of this particular objection: mandatory advance booking prevents a visitor with an unpredictable schedule from using the library. Apply the same coding rule to each completed scenario run, then compare its occurrence under mandatory and optional booking at the declared paired ensemble positions. The mean paired difference describes this simulator setup's propensity to generate that objection under the two policies, not its prevalence among visitors. An incomplete or uncodable run remains missing rather than counting as no objection. Fixing that criterion before the comparison keeps a changed rhetorical emphasis from becoming an apparent result.

The rerun design also needs an honest budget. Take three declared numerical factors for this hypothetical library: the share of visitors with unpredictable schedules, initial trust and susceptibility to other stances. One baseline and a low and high setting for each factor cost $1+2(3)=7$ configurations in a one-at-a-time comparison. Repeating each at twenty ensemble positions would cost 140 scenario runs. That is no longer a twenty-run report, and it still does not estimate interactions among the factors.

A Morris screening design with ten trajectories across three factors would instead require $10(3+1)=40$ configuration evaluations before any ensemble repetition. It can motivate a closer look at effects that vary across the sampled paths; it is not a small-budget substitute for every global sensitivity question. More comprehensive variance-decomposition designs cost much more again. With a cap of sixteen runs, a team can conduct a declared small contrast or an incomplete screen, but should report the unexamined combinations rather than decorate the result as comprehensive sensitivity.

**Tip**

**Keep the configuration and its outputs.** Each rerun needs the actual changed configuration, model and runtime, separate sampling and drift settings, and the findings it produced. Retaining outputs can support replay of those observations. A seed alone cannot promise that a future provider returns the same text. That distinction lets the team return to a particular objection without confusing inspection of an earlier run with a new execution of it.

<a id="calibration-needs-a-separate-bridge"></a>

## Calibration needs a separate bridge

To make a claim about actual visitors, a simulator would need a defined empirical target and suitable evidence. What response is being predicted? For which group, place and period? Which observations are used to fit the system, and which are held out to test it? The evaluation would have to address error on that target, not only coherence within the simulation. A method that fits one audience may fail on another. Changes to the model, data or generation procedure can invalidate an earlier result. Calibration is therefore a limited claim with a method and coverage, not a permanent property acquired by calling a tool statistical. Without that empirical bridge, generated runs formulate and compare hypotheses about visitors; they do not estimate how many visitors hold a view.

<a id="the-investigation-suggested-by-disagreement"></a>

## The investigation suggested by disagreement

Return to the library. If the objection persists only when the scenario assumes no walk-in service, the next question is whether the actual design would preserve that service. If it persists across several plausible designs, real visitors may help identify which concern the simulation is approximating or inventing.

More runs can improve our understanding of the simulator. Better empirical work is what improves our understanding of the people. Keeping those two achievements separate makes simulation useful without giving it borrowed authority.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Rehearsal and evidence](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/) > [What changes between rehearsals?](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/variation-inside-a-simulation/)

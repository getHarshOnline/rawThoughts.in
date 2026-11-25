Title: Review an observation before it becomes work

[Read HTML](https://rawthoughts.in/weave/review-an-observation/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="review-an-observation-before-it-becomes-work"></a>

# Review an observation before it becomes work

Several customer exports fail after a change of data source. The timing gives the team a reason to look, and the cause is still open. Weave’s Radar feature keeps the observations, possible causes and the reviewer’s decision together, so that noticing something, proposing an explanation and deciding what it changes stay three separate steps. Radar is not built yet; this page follows its design.

<a id="start-with-what-was-observed"></a>

## Start with what was observed

“The new source caused the failures” is an explanation to test. Keep the failed-export references, traces, source change and observation times together so the reviewer can compare what happened before and after the change.

Consider alternatives alongside it. Perhaps export size increased at the same time, or the old source has the same timeout. Missing traces leave a question unanswered. An agent can gather material it is allowed to see and suggest an explanation. The person named to review it decides what the material supports.

Source material keeps its own access rules and age. Copying last month's trace into a new Radar observation does not make it evidence of today's behaviour.

Where a proposed direction can be tried before anyone decides, say by pricing its effect or rehearsing how customers might react with another tool, the proposal keeps a reference to each run as evidence. The run stays with the tool that made it, and trying a direction decides nothing; the reviewer still does that.

<a id="decide-what-the-finding-changes"></a>

## Decide what the finding changes

The reviewer compares the explanation with its evidence and alternatives, then records a decision and the reason for it.

| Decision | What to keep |
| --- | --- |
| Accept | The finding the evidence supports, including its limits |
| Reject | Why the explanation does not follow, alongside the original observation |
| Defer | The missing evidence or condition for reviewing again |
| No material change | What was checked, the strongest alternative and the next question |

A trace might show that the timeout happens while reading from the data source. The reviewer could accept that location and wait for a comparison before deciding what caused it.

**Note**

**A run that could not obtain a required trace cannot claim to have found no material change.**

Later evidence may support a different conclusion. A new review preserves what the earlier decision relied on, as far as the source's retention and erasure rules permit. If evidence is missing or erased, the gap stays visible.

<a id="create-follow-up-deliberately"></a>

## Create follow-up deliberately

An accepted finding might justify a comparison run, a source correction or a change proposal. It becomes work only when someone takes responsibility for it: a person allowed to assign the work names who will do it, what result they owe and who will review it.

Link the later result to the observation and question it addresses. In [the export investigation](https://rawthoughts.in/weave/from-request-to-accepted-work/), a trace can answer the investigation while the error-message change and the customer's outcome remain open. That guide follows how the resulting work is reviewed and handed over.

For developers, [the observation and review domain design](https://docs.rawthoughts.in/weave/extending#keep-a-finding-distinct-from-its-follow-up) explains how the records and rules preserve these separate decisions.


Reading path: [Weave](https://rawthoughts.in/weave/) > [Review an observation before it becomes work](https://rawthoughts.in/weave/review-an-observation/)


Source code for [Weave](https://github.com/getHarshOnline/weave) is credited to [Harsh Joshi](https://getharsh.in/about/).

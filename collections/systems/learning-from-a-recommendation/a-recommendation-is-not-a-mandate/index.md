Title: Advice at the decision boundary

[Read HTML](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/a-recommendation-is-not-a-mandate/)

Author: Harsh Joshi

<a id="advice-at-the-decision-boundary"></a>

# Advice at the decision boundary

“The report is blank after yesterday's change.” You need to send the issue to somebody who can investigate it. Is it the team importing the data, the team drawing the report or the team managing access? The word “report” makes one answer tempting. It tells you very little about which team can fix the problem.

This is the sort of question [Counsel](https://rawthoughts.in/counsel/) is designed to help with. Give it the eligible teams and the records it may use; it compares the choices and recommends where to investigate. If the records cannot distinguish them, it can say so. You still decide what to do, but you have less of the comparison to reconstruct yourself.

<a id="a-finite-question-with-room-for-judgment"></a>

## A finite question with room for judgment

In this example, all three teams are allowed to receive the issue. That matters before the model starts comparing them. Finding someone in an address book whose work sounds relevant would not give us permission to share the complaint with them. We supply the eligible destinations, the evidence the model may consider and a deadline. Within that question, it can rank the choices, recommend one or abstain.

A missing import, a rendering fault and a denied query could each leave the report blank. If the underlying rows are present and the same user can retrieve them, rendering becomes a reasonable place to investigate. Without that evidence, a useful answer could be “I cannot distinguish import from rendering; is the underlying data present?” Now we know which fact to look for. We have got further than assigning the issue to a plausible owner from the word “report.”

<a id="confidence-and-abstention"></a>

## Confidence and abstention

A confident answer is still advice. Repetition, agreement between models or a well-written rationale does not promote it into an owner's ruling. Those signals can help investigate the answer; they cannot decide the authority question.

The system also needs an honest abstention. A recommendation forced from insufficient context can be more dangerous than a visible unresolved issue. Abstention should identify what the question and supplied evidence could not settle, without inviting the model to fetch unrelated information or widen its audience.

The routing case gives evaluation something definite to inspect. With rows present and a successful query by the same user, rendering is the supported recommendation. With the underlying data unknown, a question or abstention is preferable to a confident assignment. With an explicit denial for that user and report, the access-policy alternative deserves attention.

These imagined cases could become part of Counsel's model comparison. Keep the alternatives and evidence fixed, then try each candidate on the same questions:

| Case property | What a judgment benchmark would inspect |
| --- | --- |
| Enough evidence to distinguish an alternative | Whether the recommendation follows that evidence |
| A material fact is missing | Whether the model asks for the missing information or abstains |
| Evidence contradicts the obvious keyword match | Whether semantic interpretation beats a simple routing rule |
| Load, cancellation or a deadline interrupts the call | Latency, malformed/late responses and return to the declared baseline |

Would the answer arrive in time? Measure cold and warm calls, concurrency and peak memory alongside decision quality. A model that answers well in isolation may still miss the deadline under load. The checkpoint, tokenizer, quantization, runtime and machine together describe the configuration being compared; a family name leaves too much of that out.

<a id="the-work-that-selects-the-model"></a>

## The work that selects the model

Choosing a model for this work requires a census of the questions it will face and a benchmark fixed before its answers are seen. A broad capability score does not establish its quality on these particular alternatives, its tendency to abstain appropriately or the cost of a wrong recommendation. A simpler baseline matters. If a deterministic rule handles most cases adequately, model judgment should earn its additional latency and uncertainty on the remainder. If a smaller local model is sufficient, prestige is not a reason to replace it. The intended deployment profile includes the actual checkpoint, [runtime and its supported capabilities](https://rawthoughts.in/blog/a-portable-model-needs-a-runtime/), precision and machine, because the tested configuration is the relevant object.

<a id="failure-should-stop-only-what-depends-on-it"></a>

## Failure should stop only what depends on it

Some questions genuinely require judgment under the owner's policy. If the service is unavailable, those questions need escalation or a refusal to proceed. Quietly bypassing the requirement would convert a reliability failure into an authority failure. Other work does not need model assistance. It should continue under its existing rules rather than waiting for a universal intelligence layer. This is one reason Counsel's judgment and memory services are separate: losing one does not give the other extra authority or make every unrelated task unavailable.

<a id="the-record-behind-a-recommendation"></a>

## The record behind a recommendation

The recommendation should say which question, permitted alternatives, evidence and model profile produced it. The owner's acceptance or rejection is a separate fact. The later effect and outcome are separate again.

Retention still has boundaries. A record of an occurrence may remain when the source-derived material has to be deleted. That does not mean the earlier recommendation remains fully reconstructible. A digest records an identity; it is not a recoverable explanation.

<a id="useful-advice-leaves-responsibility-visible"></a>

## Useful advice leaves responsibility visible

The same kind of judgment could help distinguish a conflict, choose how much explanation someone needs or identify the evidence that would separate two possible next steps. In each case, the assistance earns its place by reducing work the person would otherwise repeat.

Return to the blank report. We can now explain why one team should investigate, or name the fact that prevents us from choosing. That is useful advice. Keep it beside the owner's decision and the later investigation: they tell us different things about whether the assistance helped. If the team eventually fixes the report, did the model use the right evidence, or did somebody rescue a bad recommendation? That is where [learning from the judgment](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/learning-from-a-judgement/) begins.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Learning from a recommendation](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/) > [Advice at the decision boundary](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/a-recommendation-is-not-a-mandate/)

Next in journey: [What a judgment can learn from](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/learning-from-a-judgement/)

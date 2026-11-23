Title: What a judgment can learn from

[Read HTML](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/learning-from-a-judgement/)

Author: Harsh Joshi

<a id="what-a-judgment-can-learn-from"></a>

# What a judgment can learn from

Suppose a model confidently recommends the rendering team for a blank report. You follow the recommendation, only to discover that the user was denied access to the underlying query. The next investigation goes to the access team. What should the model learn from that correction?

You could reward the eventual resolution, penalise the original answer, trust your correction or ask the model to grade its own reasoning. But did the model have the access record when it answered? Did following its advice help resolve the issue, or did another intervention do that? And if it missed the relevant fact once, why expect its own assessment to catch the mistake? We need to keep enough of the episode to answer those questions.

<a id="the-answer-needs-its-question"></a>

## The answer needs its question

The routing example in [Advice at the decision boundary](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/a-recommendation-is-not-a-mandate/) starts with eligible teams and evidence the model is allowed to consider. Keep that question with the recommendation. If the access denial was available and ignored, the case exposes a judgment error. If it arrived later, the earlier model may have been right to abstain, but wrong to sound certain. If the alternatives omitted the team that could resolve the issue, the question itself needs repair.

The reviewer can identify the supported destination and explain which evidence determines it. The later investigation supplies different evidence: whether the issue was actually resolved and what changed it. Neither should be reduced to a single thumbs-up. The model learns more from “access denial was present; rendering was unsupported” than from “the user eventually seemed satisfied.”

Escalations are especially useful because they occur near the model's uncertain boundary. They are also a selected sample. Training only on difficult escalated cases would not tell us how the model behaves on routine work, and training on every record it encountered would exceed what permission to answer the original question established. A learning set needs its own permitted selection and a representation of the cases it is meant to improve.

<a id="confidence-meets-an-outcome"></a>

## Confidence meets an outcome

Suppose the model gives its recommended destination 0.8 confidence on ten comparable questions. Independent review supports the destination in five. You would want to look at that discrepancy. Ten cases would not give you a reliable long-run rate, but they would give you somewhere to begin: inspect what the questions shared, then gather more evidence. The model's confidence is a claim we can investigate.

The comparison must also define success. “The recommended team investigated” differs from “the issue was resolved,” and both differ from “this destination was supported by the evidence available at the time.” The first two can be influenced by staffing, access and downstream action. A routing model should not receive all the credit for a capable team or all the blame for a missing permission. Otherwise it can learn to favour teams that close cases easily rather than teams whose responsibility matches the issue.

Self-reported confidence is useful here as a claim to check. It is not an independent reward. Agreement among model-generated judges can share the same blind spot, so the training loop needs anchors that do not improve their own score by agreeing with themselves.

<a id="a-successor-must-face-cases-it-did-not-learn"></a>

## A successor must face cases it did not learn

The proposed path for [Counsel](https://rawthoughts.in/counsel/) begins with a frozen model or deterministic baseline. It can exercise the judgment interface, establish ordinary behaviour and remain available when a candidate fails. Supervised learning on permitted cases with independently reviewed answers is a possible next step. Reinforcement learning against verifiable outcomes is a later research question.

A held-out set keeps some independently reviewed questions outside training. Known-answer probes can detect changes during operation, while the distribution of rewards can reveal that the work itself shifted. For example, a growing share of access incidents could change the apparent error rate even when the model's performance within each case type remains stable. Conversely, a stable average could conceal worsening performance on the rare cases that matter most.

Compare a proposed model successor while keeping the question, evidence, procedure and serving conditions fixed. If the procedure changes too, [the single-change and joint comparisons](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/improving-the-system-between-runs/) are needed to discover which improvement came from where. Retained capability, errors on older cases, latency and resource cost belong in the result alongside the new score. A candidate that handles the new incident and forgets the old ones may have exchanged capabilities rather than improved the service.

The successor question extends beyond fine-tuning today’s model. [MUON](https://causality.in/muon/) investigates a small adaptive reasoning unit, while [HENA](https://causality.in/hena/) investigates an architecture composed of many such units. A future candidate could change how judgment is computed, rather than merely improve the same checkpoint. The episode remains useful to that research only if it preserves the question, the evidence available then and the separate consequences that followed.

If the access team resolves our blank report, we have a useful ending. To learn from it, we still need to know which fact changed the answer and whether the model should have abstained. Then a successor has something definite to improve on: can it make the better judgment on a comparable question it has never seen? Fixing the report gives us a case. Keeping the question with it lets us learn something from the fix.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Learning from a recommendation](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/) > [What a judgment can learn from](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/learning-from-a-judgement/)

Previous in journey: [Advice at the decision boundary](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/a-recommendation-is-not-a-mandate/)

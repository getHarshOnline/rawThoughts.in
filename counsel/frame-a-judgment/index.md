Title: Frame a useful judgment

[Read HTML](https://rawthoughts.in/counsel/frame-a-judgment/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="frame-a-useful-judgment"></a>

# Frame a useful judgment

Someone tells you they received the same notice twice. You can investigate how it was prepared, check delivery or ask for another record. Which would help you find the cause? When an agent reaches a choice like this and [Pale](https://rawthoughts.in/pale/)'s rules allow several options, something has to say which one to look at first. That is the Judgment Host's job, the first of [Counsel’s](https://rawthoughts.in/counsel/) two. No host runs yet; this example follows one recommendation through the design: the question, the evidence behind possible answers and what you can do with the advice.

<a id="turn-an-open-problem-into-a-question-the-model-can-answer"></a>

## Turn an open problem into a question the model can answer

Suppose the preparation record shows one notice and the delivery record shows two events. You have a reason to look at delivery, but you do not yet know what caused the duplicate. Pale gives the model those records and the choices it may compare, with a deadline and resource limits for the answer.

A useful question connects that evidence to the choice:

> Which part of this duplicate notice should we investigate next? One notice was prepared, and its delivery record contains two events. Compare investigating preparation, investigating delivery and asking for a missing observation. Recommend a next step and explain what supports it. Do not resend the notice or assign work.

“Why did this happen?” asks for a cause the records do not yet explain. Asking where to investigate gives the model a choice it can support. The distinction also makes the next human action clear.

**Important**

**Supply only records you may share with the host.** Say when they were recorded and flag gaps or conflicts that could change the answer. Leave out unavailable choices. The model cannot make an option available or fetch missing records itself.

<a id="see-what-the-advice-rests-on"></a>

## See what the advice rests on

One prepared notice and two delivery events point toward investigating delivery. They do not yet prove a delivery fault. Each event could represent an attempted delivery, for example, rather than a received copy.

Different evidence should lead to different advice. These illustrative answers show what changes:

| Available evidence | Useful answer | Your next step |
| --- | --- | --- |
| One prepared notice and two delivery events | Recommend investigating delivery | Find out what each event did |
| Two received copies, with no preparation or delivery history | Ask whether one notice was delivered twice or two were prepared | Obtain the record that distinguishes those cases |
| Conflicting preparation records with no way to tell which applies | Explain why the evidence cannot support a choice | Resolve the conflict before relying on a recommendation |

A **recommendation** proposes one option. A **ranking** orders the choices you supplied. A **clarifying question** asks for information that could tell them apart, and can be sent only to a destination Pale has allowed. An **abstention** means the model cannot support a choice, even if it has no useful question to ask.

<a id="decide-what-to-do-next"></a>

## Decide what to do next

The task’s rules determine whether Pale may act on the advice or must ask a person. You can follow it, reject it or ask for a decision. Here, following it means starting a delivery investigation through the normal process. Counsel does not assign the work or resend the notice.

Keep what the model advised, what you decided and what the investigation found. If you corrected the advice, record the correction. Pale keeps each call and its result as a record in its genealogy, the history of context, which is what [Reckon](https://causality.in/reckon/) learns from to tell whether the advice helped. A useful later discovery tells you what the investigation found, while the earlier records tell you whether the model's answer was reasonable. [Advice at the decision boundary](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/a-recommendation-is-not-a-mandate/) explores the distinction.

<a id="if-no-answer-arrives"></a>

## If no answer arrives

A model saying “these records cannot support a choice” has answered the question. A timeout, cancellation, unavailable host or malformed response leaves you without a usable judgment. Those failures need different remedies: restoring the host may let it answer, but repeating the same question cannot supply missing evidence.

If the question requires a judgment, Pale must escalate or stop when the host cannot answer. An optional judgment uses its configured fallback; unrelated work can continue.

<a id="find-the-records-before-comparing-the-choices"></a>

## Find the records before comparing the choices

Counsel’s separate **Memory host** helps [Scope](https://rawthoughts.in/scope/) find relevant records: compare passages by meaning, suggest links, summarise and reorder results. That is a different job from deciding where to investigate. [Find knowledge with model assistance](https://rawthoughts.in/counsel/memory-artifacts/) follows a maintenance search through that service and its own permissions.

<a id="understand-which-model-supplied-the-advice"></a>

## Understand which model supplied the advice

The answer identifies its model, runtime and machine. Those details help explain an answer’s quality and the time it took. [Understand a model and its improvement](https://rawthoughts.in/counsel/models-and-improvements/) explains how to compare replacements and why learning happens outside live operation.


Reading path: [Counsel](https://rawthoughts.in/counsel/) > [Frame a useful judgment](https://rawthoughts.in/counsel/frame-a-judgment/)

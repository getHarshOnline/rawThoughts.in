Title: Understand a model and its improvement

[Read HTML](https://rawthoughts.in/counsel/models-and-improvements/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="understand-a-model-and-its-improvement"></a>

# Understand a model and its improvement

Suppose a model recommends investigating delivery every time someone reports a duplicate notice. Sometimes it is right. Sometimes the records give it no reason to choose delivery over preparation. A replacement is useful if it can tell those cases apart within the time and memory available. This is how [Counsel](https://rawthoughts.in/counsel/) compares models. No Counsel host runs yet, so this page follows the comparison as the design sets it out.

<a id="compare-answers-to-the-same-questions"></a>

## Compare answers to the same questions

The [duplicate-notice example](https://rawthoughts.in/counsel/frame-a-judgment/) supplies several cases: one prepared notice and two delivery events, two received copies with no history, and conflicting preparation records. A useful model could recommend an investigation in the first case, ask for the missing record in the second and explain why it cannot choose in the third. A model that always abstains avoids some wrong answers but offers little help.

**Important**

**Set the cases and passing criteria before comparing models.** Check answer quality, when the model knows to abstain, response time, memory use and what happens when requests arrive together. A larger model has to improve the actual task enough to justify its cost.

Keep the setup with each result. A model may answer differently if its prompt template changes, and it may take longer on another machine. Counsel calls this account a **model profile**: the saved model weights, tokenizer and prompt template, numerical precision, runtime, backend and machine. Without those details, a later comparison could attribute a change to the model when something else changed.

The first setup would use a fixed model or a test stand-in with predefined answers. The stand-in could show whether requests, cancellation and recovery work. A fixed model would let you compare the quality of answers and return to a known setup when testing a replacement.

The [Memory host](https://rawthoughts.in/counsel/memory-artifacts/) would need its own comparison. A model that recommends the right investigation might still miss a useful passage or omit a warning from a summary.

<a id="improve-judgment-through-experience"></a>

## Improve judgment through experience

Suppose the model recommends delivery, a reviewer notices that two notices were prepared, and the team fixes preparation instead. The problem is solved, but training on the successful outcome alone would reward the wrong recommendation. Learning needs to keep what the model knew and advised separate from the correction, the decision and the eventual result.

One proposed research path starts with supervised learning from independently assessed judgments. Learning from measured outcomes would be a further step. Both would happen outside live operation, using evidence separately permitted for training. The cases would come from [Pale's](https://rawthoughts.in/pale/) genealogy, the history it keeps of each question, and from the evaluations [Reckon](https://causality.in/reckon/) records against them. Held-out cases would check whether a candidate improves useful answers without losing earlier capabilities or exposing private information. [What a judgment can learn from](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/learning-from-a-judgement/) develops the research question.

A model and the procedure around it can change together. Compare each separately as well as the combination, or an improvement in the procedure could be mistaken for a better model. [Improving the system between runs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/improving-the-system-between-runs/) explains that distinction.

<a id="could-a-learning-unit-become-the-judge"></a>

## Could a learning unit become the judge?

The first local judge gives the work a starting point while research explores a different kind of model. [MUON](https://causality.in/muon/) studies a small reasoning unit that could learn within a defined task and resource budget. That makes it a candidate for Counsel’s narrow judgment questions. Everyday decisions could supply useful comparison cases, where their owners permit research use.

[HENA](https://causality.in/hena/) asks how many such units might communicate, use limited memory and develop useful hierarchy. A system built from those units might eventually take over some of Pale’s explicit coordination; how it would do so and where it would fit remain research questions. A HENA-backed model could also be tested as a model provider behind a coding harness, a separate use from Counsel’s local judge. A future unit would have to improve on the initial model on the same cases before replacing it; the ability to learn is not itself evidence that it gives better advice.

Any successor would need to improve the work while preserving the capabilities people rely on. It would take questions and return answers through the same interface, so replacing the model would not require Pale to change how it asks for advice. Pale would check that the new setup is approved for its questions before switching. Keep the previous setup available to compare results and switch back if needed.


Reading path: [Counsel](https://rawthoughts.in/counsel/) > [Understand a model and its improvement](https://rawthoughts.in/counsel/models-and-improvements/)

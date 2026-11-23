Title: The label is a decision

[Read HTML](https://rawthoughts.in/blog/the-label-is-a-decision/)

Author: Harsh Joshi

<a id="the-label-is-a-decision"></a>

# The label is a decision

“The delivery arrived, but I still cannot use it.” One annotator marks the message as resolved because the package arrived. Another marks it unresolved because the customer cannot do the work. Both have read the same sentence. Their disagreement begins in the task's definition, before either person makes a careless click.

This invented example is why I find annotation interesting as a product problem. A label compresses a judgement into a form another system can use. Its value depends on the distinctions that survive the compression: what counts as an item, what the category means, which context the annotator sees and how ambiguity is resolved. Recruiting more annotators can increase throughput while multiplying an unclear decision.

<a id="the-task-determines-the-object-being-labelled"></a>

## The task determines the object being labelled

If the intended model detects delivery complaints, the sentence may belong to that category. If it decides whether a support matter can close, arrival alone is inadequate. If it extracts events, it might record the arrival and the inability to use the item separately. A single “positive” or “negative” label would obscure all three tasks in different ways. The question is therefore not how detailed an ontology can become, but which distinctions the downstream job actually needs.

An annotation project also differs from its dataset. The same source items can support different tasks, using different guidelines, access and output definitions. A dataset may contain whole conversations while a task labels individual turns. Deciding where a unit begins and ends affects what the annotator can infer and what the model is later evaluated against. A short utterance separated from its preceding question can acquire a different meaning.

The label system needs to carry those choices. In a hypothetical support dataset, “arrival reported,” “usable result confirmed” and “matter closed” can be separate observations. If the product only needs one of them, unnecessary fields add work. If it needs all three, forcing them into one status teaches the model a convenient ambiguity. The ontology is part of the product's theory of the work.

<a id="guidelines-turn-a-category-into-a-repeatable-judgement"></a>

## Guidelines turn a category into a repeatable judgement

A category name rarely carries enough meaning by itself. A guideline can supply its definition, positive and negative examples, boundary cases and an honest way to mark missing context. In the delivery example, the rule could explicitly say that arrival is insufficient for usable completion. A pilot then reveals whether annotators can apply that distinction consistently or whether the rule still leaves difficult cases unresolved.

An illustrative guideline for **usable result confirmed** could require an explicit statement that the customer can perform the intended task. It would produce these different decisions:

| Source statement | Annotation | Reason under this guideline |
| --- | --- | --- |
| “It arrived, but I still cannot use it.” | No | The customer explicitly reports unusability |
| “It arrived.” | Unknown | Arrival is reported; usability is not |
| “It arrived and I can complete the job now.” | Yes | The intended use is explicitly confirmed |

The middle row is the important one. An annotator inferring “yes” from delivery and another choosing “unknown” have exposed a missing rule if the guideline never addressed absent evidence. Once the rule is explicit, the same disagreement has a different diagnostic meaning. A missing statement should not be forced into a negative outcome either: unknown and unusable are different training targets.

Disagreement is useful here. One participant may have missed an explicit rule; another may have found a case the rule never considered. Those failures need different responses. Training can help the first. Revising the task or its guideline may be necessary for the second. Treating every disagreement as worker error prevents the product from learning where its own meaning is incomplete.

Changing a guideline also changes the interpretation of the output. Suppose earlier batches treated any delivery report as closing the matter and later batches require usability. Combining them without their rule versions gives the learner two definitions under one label. The model may appear inconsistent while accurately following the inconsistent training material. Versioning links an annotation to the meaning under which it was made, and identifies which earlier items need review rather than silently reinterpreting them.

<a id="agreement-measures-consistency"></a>

## Agreement measures consistency

Imagine one hundred hypothetical items, all marked resolved by three annotators. Agreement is complete. If thirty items actually describe unusable deliveries and the task requires usability, unanimous labelling has preserved the same error. Consistency answers a different question from the adequacy of the task's interpretation.

[Artstein and Poesio's survey](https://aclanthology.org/J08-4004/) distinguishes agreement, reliability and validity and examines the assumptions of agreement coefficients. The important practical consequence is to ask what a score measures before turning it into acceptance. Category prevalence, annotation units and the treatment of missing or uncertain answers affect the comparison. A threshold borrowed from an unrelated task cannot decide whether these labels are useful for this product.

An independent review can inspect the interpretation, including difficult cases and repeated errors. Majority convergence can resolve some variation, but three people trained on the same inadequate rule do not supply three independent grounds for its correctness. Expertise also belongs to the task: recognising a technical failure, a linguistic ambiguity and a domain-specific consequence may require different kinds of review.

<a id="completion-has-a-quality-path"></a>

## Completion has a quality path

Submission means someone supplied an annotation. Review, correction and acceptance have different work to do afterwards. A fast queue with high rework may deliver less useful data than a slower first pass. Counting only accepted items can hide the effort spent getting them there. Conversely, a difficult disagreement that improves the guidelines may create value beyond the particular item that triggered it.

Assistance can change that path. A model may pre-label items so people correct rather than begin from nothing. The experiment then concerns the combined process: time saved, errors retained, cases ignored and the effect of showing the suggestion before an independent judgement. If every reviewer sees the same suggestion, apparent agreement can reflect a shared starting point. Comparing an assisted route with a suitable independent baseline gives the claimed efficiency an actual object to measure.

In [learning whether context helped](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/), a system faces the same choice of what to reward. Offered information, use, agreement and eventual task outcome are related observations, but rewarding one in place of another can train the wrong behaviour. Useful quality begins by keeping the outcome the annotation is meant to support in view.

<a id="the-dataset-carries-the-circumstances-of-its-making"></a>

## The dataset carries the circumstances of its making

A released or transferred dataset needs more than rows and labels. Its sampling, sources, task definitions, rule changes and review process affect what another person can learn from it. [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) proposes documenting motivation, composition, collection and intended uses to make those decisions intelligible to consumers. Such an account helps a team recognise when the material fits its task and when another population or context needs new work.

The delivery example could become a useful training resource if its categories preserve the distinction between an item arriving and a customer succeeding. It could become a misleading one if the same words conceal changing definitions. Annotation makes human judgement available to another system; its quality lies in how faithfully that judgement carries the task's meaning into the next use.

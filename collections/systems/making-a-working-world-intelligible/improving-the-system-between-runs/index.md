Title: Improving the system between runs

[Read HTML](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/improving-the-system-between-runs/)

Author: Harsh Joshi

<a id="improving-the-system-between-runs"></a>

# Improving the system between runs

An agent's procedure and its model work together. Changing the instructions can improve a task without changing any weights; replacing the model can improve the same task while making those instructions less effective. When both change at once, an attractive result can conceal which change helped, which harmed and what the combination depends on.

[Pale](https://rawthoughts.in/pale/) supports improvement without making the live operation an experiment whose conditions keep moving. It separates evidence produced during work from candidates developed afterwards. That separation is useful scientifically as well as operationally: it gives a comparison something stable to compare.

<a id="two-changes-are-not-one-treatment"></a>

## Two changes are not one treatment

Consider a hypothetical document-comparison task. The current procedure tells an agent to locate a revision and list material differences. A revised procedure adds an explicit check for changed definitions before comparing values. Separately, a new model is proposed. Four configurations can then answer four different questions. The table gives illustrative acceptable results out of the same 100 cases.

| Configuration | Procedure | Model | Acceptable results |
| --- | --- | --- | --- |
| Current system | Current | Current | 70 |
| Procedure change | Revised | Current | 82 |
| Model change | Current | New | 78 |
| Joint change | Revised | New | 80 |

They show why the joint arm is insufficient. It improves on the current system but performs worse than the revised procedure with the current model. On this acceptance scale, adding the separate gains would have suggested 90; the joint result is 80. The interaction is:

$$
\Delta_{\text{interaction}} = 80-82-78+70=-10\text{ percentage points}.
$$

The revised procedure gains 12 points with the current model but only two with the new one. That difference is the interaction. Its interpretation depends on the scale, and this toy table supplies no estimate of uncertainty, but it exposes a possibility an old-versus-new comparison would miss.

The new model might follow the extra instruction differently, or spend its effort explaining definitions while overlooking a numerical exception. A different case mix could reverse the ordering. The experiment therefore needs the separate arms, the same cases and a closer account of where errors moved. “Newer” cannot do that explanatory work.

<a id="improving-a-procedure-is-a-real-learning-problem"></a>

## Improving a procedure is a real learning problem

Natural-language procedures are more than wrappers around a model. They can specify an order of inspection, preserve a distinction, add a useful stopping condition or remove a distracting step. Their changes are executable through the agent's behaviour even though the changed artifact is text.

[Microsoft's SkillOpt](https://github.com/microsoft/SkillOpt) explores this text-space approach with a frozen target model, trajectory-driven edits and validation-gated candidates. That supplies a useful mechanism to investigate, not a guarantee that a procedure will transfer to a different task or harness. A candidate can overfit the recurring mistake that inspired it, and an instruction that helps one class of case can damage another.

In the document example, “always reject a changed definition” could remove some false comparisons while incorrectly rejecting a harmless renamed field. The useful procedure must help the agent determine the consequence of the change, rather than teach it a reflex. Retained capabilities and difficult alternatives belong in evaluation alongside the targeted failure.

<a id="the-comparison-has-a-world-around-it"></a>

## The comparison has a world around it

The model and procedure are not the only things that determine performance. Available documents, tools, task definitions, runtime settings and the evaluator all affect what a configuration can do. If the revised procedure receives a clearer document or a more forgiving evaluator, its apparent gain cannot be assigned to the procedure alone.

Pale's design therefore starts an adaptive branch from a fixed account of the relevant conditions. Candidate generation may inspect a defined training set and use feedback to search. Validation helps choose among candidates; [a later held-out evaluation](https://causality.in/reckon/) (on Causality) asks whether the selected candidate still helps. Reusing that final evaluation repeatedly as search feedback changes its role: it is no longer an untouched comparison.

An evaluator used to reward the search also needs independent scrutiny. A model can produce fluent explanations that satisfy another model while still missing the actual difference in the documents. A native check, an independently prepared reference or appropriately reviewed cases can test a different part of the result. Disagreement is informative because the evaluators may be measuring different achievements.

The operational cost matters too. A procedure that reduces mistakes by doubling every read may be worthwhile for a consequential decision and unsuitable for a routine one. Acceptance, time, resource use and consequential errors remain separately interpretable; their trade-off belongs to the task being improved.

<a id="a-successor-rather-than-a-moving-target"></a>

## A successor, rather than a moving target

Once a candidate has earned adoption, it can become a distinct released configuration. Pale compiles that successor outside the live path, accepts the intended change and lets new sessions use it. Existing sessions keep the configuration under which their work began. A rollback then has an identifiable previous state, rather than an approximation of instructions that have since edited themselves.

That is also how later evidence stays useful. An improved result can be traced to the configuration that produced it; a new failure can be compared with the earlier one. Source material used for work still needs permission for its particular learning use, so a broadly useful procedure cannot quietly contain a client's private case.

The ambition is an agentic system that gets better through its work while keeping the improvement intelligible. Which [context helps](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/) and how a procedure or model uses it are related experimental questions. Holding the conditions still long enough to understand a change makes the next change less of a guess.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Making a working world intelligible](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/) > [Improving the system between runs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/improving-the-system-between-runs/)

Previous in journey: [The structure a responsibility needs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/starting-with-the-duty/)

Next in journey: [Would you carry another control layer?](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/another-control-layer/)


Source code for [Pale](https://github.com/getHarshOnline/pale) is credited to [Harsh Joshi](https://getharsh.in/about/).

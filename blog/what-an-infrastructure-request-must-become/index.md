Title: What an infrastructure request must become

[Read HTML](https://rawthoughts.in/blog/what-an-infrastructure-request-must-become/)

Author: Harsh Joshi

<a id="what-an-infrastructure-request-must-become"></a>

# What an infrastructure request must become

“Give us enough compute to finish this experiment by Friday.” It is an intelligible request and an incomplete specification. Enough for which experiment? Does Friday mean a trained checkpoint or an evaluated result? Can the data leave its present location? What is the budget for an attempt that may not work?

Natural language makes sophisticated work easier to ask for. The next product problem is making the requested change equally intelligible. A useful interface helps the person discover the consequential choices, turns them into a definite proposal and carries the accepted proposal through execution. It makes the machinery more accessible without reducing the work to the machinery's first successful response.

<a id="a-goal-acquires-a-specification"></a>

## A goal acquires a specification

Consider a hypothetical team testing a small model adaptation. Its request names a dataset, a base model and a deadline, but omits the permitted region and acceptance test. A planning step can identify those omissions, compare suitable paths and construct a specification containing the exact inputs, environment, resource limits, result destination and evaluation. The plan is useful before anything runs because it makes the intended work inspectable.

Some choices can follow existing rules. Others need judgement or an owner's answer. The interface can distinguish them rather than ask twenty questions indiscriminately or guess at a sensitive constraint. The person may approve a region already permitted for the data but reject a faster alternative that requires moving it elsewhere. That decision changes the feasible plan, not merely a preference in its presentation. A model's role in [comparing eligible alternatives](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/a-recommendation-is-not-a-mandate/) can help here while the rules and accepted choices remain explicit.

<a id="a-preview-carries-an-economic-proposition"></a>

## A preview carries an economic proposition

Suppose the proposed allocation costs two arbitrary currency units per hour and is expected to run for six hours. The estimated allocation charge is twelve. An eight-hour cap permits up to sixteen for that component. Neither number includes an unstated storage charge or promises that the training target will be reached. The preview becomes useful when it separates the estimate, the permitted maximum and the circumstances that change either one.

The same distinction matters when the operation replaces an existing service. A cheap new allocation can coexist temporarily with the old one during a canary or migration. A preview pricing only the final arrangement can omit the transition's cost. Conversely, stopping the old service first may reduce expense while removing the recovery path. The actual proposal has an interval, dependencies and alternatives; those give the price its meaning.

Approval can bind that particular proposal, including its revision, scope and limits. If the plan changes to use twice the resources or another region, the system has a new proposal to consider. Keeping this connection explicit makes automation more useful: routine execution can proceed inside an understood boundary instead of repeatedly asking for broad permission whose consequences are unclear.

For the adaptation experiment, a compact proposal could state the approved dataset and base revision; the permitted region; the selected environment; a six-hour estimate and eight-hour allocation cap; the retained artifact destination; and the evaluation that answers the experiment's question. Its return record would then name the applied configuration, observations, artifact and evaluation outcome. The request “by Friday” has become a relationship between those two objects. If a dataset cannot be reached, the system can identify the failed premise without improvising another dataset; if evaluation rejects the adapter, it can return a completed experiment with an unsuitable candidate rather than an unexplained deployment failure.

<a id="a-capability-is-larger-than-an-endpoint"></a>

## A capability is larger than an endpoint

“Prepare an approved environment for this experiment” may coordinate several lower-level operations. That can reduce the caller's burden, provided the operation retains the important intermediate choices and returns a coherent position in the work. Exposing each provider endpoint separately makes everything composable in theory while requiring every caller to reconstruct the workflow. One giant operation can hide too much. The useful granularity follows the work that can be specified, observed and recovered together.

The [MCP tools specification](https://modelcontextprotocol.io/specification/2025-06-18/server/tools) provides discovery and invocation schemas, structured results and security considerations, including input validation and confirmation for sensitive operations. A transport can carry a defined capability through different interfaces. It does not decide the product's budget, define the experiment's success or supply the execution owner's recovery behaviour. Those meanings have to be built around the operation.

An engineer may inspect the deployment details. A business user may inspect the goal, cost and choices. An agent needs structured preconditions, results and error meaning. These are different views of the same proposal, not different versions of what was approved. Simplifying an interface is valuable when it removes irrelevant machinery while retaining the choices that can change the result.

<a id="where-an-interrupted-change-stands"></a>

## Where an interrupted change stands

The allocation request is sent, then the connection drops. Repeating it might acquire another allocation; assuming success might leave the experiment waiting. A useful workflow retains the operation's identity and uses the provider's supported observation or idempotency mechanism to find what happened. [An uncertain response](https://rawthoughts.in/collections/practice/unknown-effects-and-interrupted-work/) is a position to reconcile, not a reason to regenerate the whole plan.

Different recovery operations answer different needs. Timed teardown releases resources after their agreed interval. Rollback attempts to restore a previous arrangement after a failed change. Resumption continues from retained progress. None can be substituted merely because they all sound like cleanup. The plan needs to know which state can survive each operation and who is responsible for restoring it.

<a id="completion-returns-to-the-requested-outcome"></a>

## Completion returns to the requested outcome

An environment can be healthy while the application fails. A training run can complete while its evaluation rejects the result. The workflow therefore observes more than deployment: the operation applied, the service is healthy, the work produced an artifact, and the artifact met or missed its criterion. Each gives the person a different next decision. A failed experiment may still be valuable if it answers the question the team meant to investigate.

This is one kind of continuity [Pale's](https://rawthoughts.in/pale/) design keeps across its providers. Its wider purpose is to connect a person’s goals with the context, people, agents and applications that can carry them, rather than make the person reconstruct a separate workflow at every entrance. The person can return to an intelligible proposal and find the work's present position, including the decision still needed. The interface succeeds when “finish this experiment” becomes a smaller set of explicit choices and a dependable path through them, rather than a fluent instruction followed by an opaque effect.

Title: When an agent's context changes underneath it

[Read HTML](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-changes/)

Author: Harsh Joshi

<a id="when-an-agent-s-context-changes-underneath-it"></a>

# When an agent's context changes underneath it

An agent is drafting a product page from a decision to offer a service. Another agent records a new decision: the service is no longer being offered. The draft still reads well. Nobody has edited the same file, so there is no file conflict to catch. Yet publishing it would offer something that is no longer available.

Agents decide far more often than people, so by the time one writes, what it read has usually changed: the gap between the time of a read and the time of the action taken on it, which distributed systems have long handled as an occasional fault, becomes the ordinary case. [Scope’s](https://rawthoughts.in/scope/) semantic-transaction research asks whether recording what the draft depends on would catch this kind of change better than a simpler system that checks source versions. The task is to notice the changed service decision while letting unrelated work continue.

<a id="the-text-being-edited-may-be-untouched"></a>

## The text being edited may be untouched

Call the drafting agent A and the agent recording the new decision B. To catch the problem, A's record of what it read must include the service decision and its revision. Recording only the draft file would miss the change. Recording merely the project name would not tell us which claim needs another look.

The same problem arises when an owner changes, a permission is revoked or a required contract is revised. Each can change what the draft may say or what someone may do with it. Keeping the particular dependency gives the check something to inspect; locking the whole project would also stop work that never relied on that decision.

<a id="stale-reasoning-can-continue-as-speculation"></a>

## Stale reasoning can continue as speculation

A may have written a useful explanation of how the service works. Pausing the offer does not necessarily make that explanation wrong. It does make the invitation to buy wrong. A can keep developing the draft as speculative work, but the old decision can no longer authorise its publication. Checking the new decision might require changing one sentence, recasting the page as a historical account or abandoning it. We have to read what changed to know which.

<a id="record-what-the-draft-depends-on"></a>

## Record what the draft depends on

The proposed protocol has five operations: **open** a transaction for the relevant scope, **query** its context, **propose** a change, **respond** to that proposal and **watch** the dependencies. The record of what was read includes the source revisions, which items belonged to the scope and who had authority over the decision. Those last two can change even when the wording stays the same.

A records that its draft used availability decision r1 within the scope where that decision applies. B proposes r2 through the scope's designated writer; the design permits only that writer to make the accepted change. Once r2 is accepted, A's watch reports that its dependency has changed. Before publication, the proposal must be checked against r2. Cancellation, abort and expiry also have explicit outcomes. Silence cannot stand in for a successful response.

Four consistency choices describe different uses of this record:

| Consistency class | What the reader asks for |
| --- | --- |
| Snapshot | A coherent account at the selected revision |
| Causal | The declared dependency order, so a derived result does not precede the ground it used |
| Strong | A fresh check of the visible source revisions, scope and authority before the next consequential step |
| Speculative | Continued reasoning whose changed ground has not yet been reconciled |

**Note**

**These names describe consistency guarantees.** Here “causal” means respecting the declared dependency order, not identifying scientific causes. A “strong” check can confirm that the visible context is current; it cannot prove the claims in that context true.

One writer per scope and a fixed ordering rule where scopes overlap would make it possible to replay the same changes and get the same result. The experiment must show whether those rules catch the stale dependency more precisely, or at less cost, than the simpler version-checking system.

<a id="version-order-is-not-semantic-truth"></a>

## Version order is not semantic truth

A revision records an accepted change and its place in the history. It does not prove that the newer wording is true, that its author had the relevant authority or that every dependent claim must change. Those questions still belong to the source and its decision process.

<a id="agents-on-unrelated-work-should-not-wait-for-each-other"></a>

## Agents on unrelated work should not wait for each other

While A revises the service page, agent C may be working on an unrelated essay. C should keep going without waiting for one global agent to approve everyone's next step. Where scopes overlap, the system needs a rule for rejecting conflicting changes or applying them in order. It must also record changes in membership and authority: moving a source into a different scope, or changing who can decide, can invalidate A's use of it even if its paragraph is unchanged.

<a id="context-consistency-does-not-execute-the-effect"></a>

## Context consistency does not execute the effect

Checking r2 answers whether A's draft still rests on a current decision. The publisher separately decides whether it may go out. The system that performs publication keeps its credentials, checks permission and records what happened.

If a publication request was sent but its response was lost, rereading r2 cannot tell us whether the page went live. That [unknown external effect](https://rawthoughts.in/collections/practice/unknown-effects-and-interrupted-work/) needs a check of the provider's state and a way to recover without blindly repeating the action. Scope would identify what reasoning needs another look; the system that performed the action must establish what it actually did.

<a id="one-changed-premise-two-agents"></a>

## One changed premise, two agents

The first experiment can follow this case all the way through. A reads the availability decision, B changes it, and the check stops A's next attempted publication before anything goes out. A still has its draft to revise. Replaying the same sequence reaches the same result, while C's unrelated work continues.

The case, moment by moment:

| Moment in the proposed experiment | Agent A | Agent B | Unrelated agent C |
| --- | --- | --- | --- |
| Initial read | Uses availability revision r1 | Prepares a change to that decision | Works within another scope |
| Source revision | Its draft still contains the r1 claim | Records the accepted revision r2 | Continues |
| Revalidation | Detects the changed premise and revises or retains speculative work | Its change remains in the source history | Does not acquire a dependency on r2 merely by running concurrently |

Run that case against the simpler versioned resolver and compare what each detects, what it unnecessarily stops and how much coordination it costs. Explicit semantic dependencies earn their place only if they improve that comparison. The useful result is that A knows which part of its work to reconsider and C has no reason to stop.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Context that helps the work](https://rawthoughts.in/collections/systems/context-that-helps-the-work/) > [When an agent's context changes underneath it](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-changes/)

Previous in journey: [Finding the right context for the work](https://rawthoughts.in/collections/systems/context-that-helps-the-work/finding-the-right-context-for-the-work/)

Next in journey: [When context helps](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/)

Title: The structure a responsibility needs

[Read HTML](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/starting-with-the-duty/)

Author: Harsh Joshi

<a id="the-structure-a-responsibility-needs"></a>

# The structure a responsibility needs

A team needs a monthly account review. Somebody gathers the records, resolves discrepancies and prepares a comparison; somebody else uses it to decide what happens next. Before long, we could give it a department, a room, a dashboard and an agent. But what work have we actually asked any of them to do?

Start there: prepare a comparison of the agreed accounts for this review, show the discrepancies and keep a way back to the source records. Now we have something to organise. Which parts does that responsibility need, and which ones are we adding because the last system had them?

<a id="a-responsibility-can-outlive-its-occupant"></a>

## A responsibility can outlive its occupant

Suppose you prepare the comparison today. If this were a one-off request, assigning it to you might be enough. A monthly review asks for more: somebody must make sure the comparison arrives each time, resolve exceptions and arrange a replacement when you are away. That continuing responsibility gives us a reason to name a role. You fill it for a time; the duty needs to survive your absence.

Changing the occupant should preserve what the duty means without implying that every detail of the former person's authority transfers. Preparing the figures, resolving an accounting interpretation and authorising a payment are different acts. A handover can transfer the first while leaving the others with their existing decision-makers. One title cannot safely stand in for all three.

<a id="a-crossing-needs-a-consequence-at-each-end"></a>

## A crossing needs a consequence at each end

Suppose a separate reporting team prepares the comparison for the account team. We now have a reason to describe a service: what the account team asks for, what the reporting team agrees to supply and how they handle an exception. The reporting team can finish and deliver its comparison. The account team still has to decide whether it can use that result for the review. If the report covers the wrong period, the delivery happened, but the review still needs its comparison.

[Those two meanings of done](https://rawthoughts.in/collections/practice/two-meanings-of-done/) keep the correction small. The report need not be discarded, and the account review need not pretend to be complete. The request can identify the period to revise, who accepts the revision and what happens if a required record is unavailable. A shared chat may help coordinate that correction. A chat is not mandatory merely because two teams participate.

The service also runs in a particular direction. Preparing a comparison for the account team does not give the reporting team the reverse right to commission work from it. Another consumer may need a different disclosure boundary and a different acceptance condition. Reusing the service pattern does not reuse those terms automatically.

<a id="the-record-behind-the-discrepancy"></a>

## The record behind the discrepancy

Does this duty need a new application? If the existing accounting system already owns the transactions and can reproduce the relevant period, perhaps the report needs only references and a reusable preparation procedure. Copying the ledger into a coordinating tool would create another place to reconcile without adding a new source of truth.

An application becomes necessary when the duty has its own state or effects that must transact and replay. A reconciliation queue, for example, might need to remember which discrepancy was raised, what revision resolved it and which result was accepted after an interruption. That record belongs with the system responsible for it. The source ledger still owns its entries. A view can connect the two without holding either.

The reusable procedure says how to prepare the comparison. An agreed rule says which period or criterion applies. The application records the actual episode. Keeping these separate lets the next review reuse the method without accidentally reusing last month's facts or acceptance.

<a id="the-smallest-configuration-that-can-continue"></a>

## The smallest configuration that can continue

A [Pale workspace](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/) should acquire its structure this way. Each role, contract and application answers a need in the duty. If the team can do the review without a new room or dashboard, leave it out. Keep a direct human route for the work when the coordinating engine is unavailable. The compiler can check the relationships we declare; the people carrying the responsibility decide what those relationships mean.

At the next monthly review, the team needs the continuing duty, this month's assignment, the ledger's figures and the accepted comparison. Each answers a practical question: why the work recurs, who is doing it, which numbers it uses and what the reviewer found sufficient. If a client commissions that review, its commercial agreement adds another relationship with terms of its own. The internal review needs no such agreement simply to exist. The configuration follows the responsibility as it grows, rather than giving every review the shape of a sale.

A household calculation, a publication and an arm’s-length client engagement can use the same method while producing different structures. The calculation may stay in its native application; the publication needs its publisher’s decision; the client keeps its own acceptance and private records. A common grammar is useful because it can express those differences, not because every duty becomes a department, a chat room and an agent.

The test of the structure arrives at the next review, or when the preparer is absent. Can another person find the right period, see the unresolved discrepancy and continue without inheriting an authority nobody gave them? If the selected structure makes that possible, it has earned its place. If a department, dashboard or agent contributes nothing to that continuity, the duty can proceed without it.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Making a working world intelligible](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/) > [The structure a responsibility needs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/starting-with-the-duty/)

Previous in journey: [Records, context and decisions](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/records-and-context/)

Next in journey: [Improving the system between runs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/improving-the-system-between-runs/)


Source code for [Pale](https://github.com/getHarshOnline/pale) is credited to [Harsh Joshi](https://getharsh.in/about/).

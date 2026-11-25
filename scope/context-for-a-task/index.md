Title: Context for a task

[Read HTML](https://rawthoughts.in/scope/context-for-a-task/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="context-for-a-task"></a>

# Context for a task

You return to an equipment order after a few days away. Which version was approved? Has anything arrived? What still needs an answer? Finding the folder is only the beginning: the agent needs enough of the history to tell those things apart.

[Scope](https://rawthoughts.in/scope/) supplies that account from records their owners permit it to use. Follow one equipment order to see which records belong in the answer, what they support and when they need to change. Scope's repository holds an empty Rust library today; the service that answers an agent is the work in front of it.

<a id="work-out-what-the-update-needs"></a>

## Work out what the update needs

Suppose you want to send a colleague an internal delivery update. The request could be:

> Prepare an internal delivery update for order 42. Use approved revision 3 and the latest permitted supplier report. Include the approval reference and report date, and identify any missing arrival estimate. Do not use another client's records.

The approval and the supplier report answer different questions. Keeping both matters more than collecting every mention of the order.

| Question | What supports the answer | What you can conclude |
| --- | --- | --- |
| Which order may proceed? | Approval naming revision 3 | Revision 3 was approved; an earlier quotation is not the current instruction |
| What has arrived? | The supplier's dated partial-delivery report, revision 7 | The supplier reported a partial delivery at that time |
| When will the rest arrive? | No current estimate | You still need an answer from the supplier |

Open the approval and the report. If they support the answer, the update could read:

> Revision 3 of order 42 is approved. In report revision 7, the supplier says part of the order has arrived. We still need an arrival date for the rest.

Include the report date and approval link when drafting from real records.

The colleague's needs also shape the message: a formal summary and a short decision update may use the same evidence differently. Scope's private mental model keeps that context about people, roles and priorities, with sources and dates that say when it applies. A person's role can change, and a project's long-term importance can differ from its priority this week. A communication preference helps with the draft; it does not authorise sending it or making a commitment.

<a id="use-the-records-this-task-permits"></a>

## Use the records this task permits

For this update, the order's owner supplies copies of the approval and supplier report. Each copy identifies its original, revision and date, how long it remains usable and what the task may do with it. Scope answers from that dated material. The owner keeps access to the supplier's mailbox and supplies a new report when it is available; Scope does not open the mailbox itself.

Keep the quotation, approval and delivery report identifiable as different records. The [source-import explanation](https://docs.rawthoughts.in/scope/concepts#owners-hand-scope-snapshots-scope-never-reads-a-source) describes how those copies reach Scope without credentials or unrelated conversations.

The request's wording cannot enforce access. Scope checks what its caller may use before looking for relevant material. Each instance has an expressly defined data owner and permitted uses; a shared company name, folder or machine does not establish that arrangement.

**Caution**

**Check the audience before using the report.** Permission to read it internally may exclude sending it to a model or quoting it in a public update. Access to two clients' records does not make both sets appropriate for either client's task. [Finding the right context for the work](https://rawthoughts.in/collections/systems/context-that-helps-the-work/finding-the-right-context-for-the-work/) develops that distinction.

A source owner can also select a [Gazette](https://rawthoughts.in/gazette/) site export. [Pale arranges its import into Scope](https://rawthoughts.in/pale/understand-your-world/#use-connected-applications-for-their-own-strengths), so later tasks can use the captured publication within the same source and permission checks.

<a id="see-what-the-answer-leaves-open"></a>

## See what the answer leaves open

The answer should let you trace each part of the update: which approval it used, which report supports the delivery sentence and why no arrival date is given. Scope calls that response a [context bundle](https://docs.rawthoughts.in/scope/concepts#a-context-bundle-explains-itself). It keeps the source references, revisions, age and gaps with the answer, so you can check the account rather than trust a fluent summary.

The missing arrival estimate calls for new evidence from the supplier. A useful passage left out for space calls for a narrower question or a larger response. An unavailable search method may call for a different way to find the record. Those are different problems, and the answer should say which occurred without exposing records the caller cannot access.

**Important**

**Keep the approval and its limits in the answer.** If the size allowance cannot hold required context, Scope should report that problem rather than silently omit it. The bundle helps prepare the update; approving the order, sending the message and accepting delivery remain separate actions.

An order reference may be enough to find the approval. A question about “maintenance” may need help finding a report that calls it “servicing.” The [retrieval-mode guide](https://rawthoughts.in/scope/strict-and-model-assisted-context/) explains strict lookup and model assistance from [Counsel](https://rawthoughts.in/counsel/), including what happens when that assistance is unavailable. Neither can supply the absent arrival estimate.

<a id="return-to-the-task-without-losing-its-history"></a>

## Return to the task without losing its history

A new session should be able to reopen the same bundle and source references. A later supplier report should produce a new answer, leaving the earlier account intact. [Keep a task current](https://rawthoughts.in/scope/keep-context-current/) follows that change and explains corrections and withdrawal.

Source removal must also reach dependent summaries, embeddings and learned links. If deletion makes an old answer impossible to reconstruct, its history needs to say so. It must not preserve a disguised copy merely to make replay possible.

Parallel work raises another question: if one agent changes a premise, which parts of another agent's reasoning need attention? [When an agent's context changes underneath it](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-changes/) explores Scope's proposed semantic transactions. Ordinary retrieval does not depend on that research being complete.

<a id="find-out-whether-the-context-helped"></a>

## Find out whether the context helped

An agent reporting that it used the supplier report tells us something about the draft, but not whether the update was useful or correct. Scope's learning programme would compare what it offered, what the agent reported using and how the work ended.

Through Pale, [Reckon](https://causality.in/reckon/) (on Causality) would compare retrieval and memory choices on the same work; each comparison is an intervention contrast, not proof of what caused the outcome. That evidence could support a proposed change to Scope's retrieval policy, followed by review and a separate release. [When context helps](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/) explains the comparison.

To build the Scope library and set up for development, follow [Building the library](https://docs.rawthoughts.in/scope/development#building-the-library).


Reading path: [Scope](https://rawthoughts.in/scope/) > [Context for a task](https://rawthoughts.in/scope/context-for-a-task/)


Source code for [Scope](https://github.com/getHarshOnline/scope) is credited to [Harsh Joshi](https://getharsh.in/about/).

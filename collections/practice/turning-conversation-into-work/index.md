Title: Turning a conversation into work

[Read HTML](https://rawthoughts.in/collections/practice/turning-conversation-into-work/)

Author: Harsh Joshi

<a id="turning-a-conversation-into-work"></a>

# Turning a conversation into work

Work often starts before anyone calls it work. A customer mentions a problem, a colleague offers to investigate and a manager says it sounds useful. Three weeks later, everyone remembers a different commitment. What, exactly, did we agree to do?

Somewhere in that conversation, a suggestion needed to become a responsibility somebody accepted. Finding that moment is one of the questions behind [Weave](https://rawthoughts.in/weave/). People and agents should be able to continue the work without rereading an entire conversation to decide which remark became a promise.

<a id="the-responsibility-inside-the-exchange"></a>

## The responsibility inside the exchange

Imagine a team discussing an unreliable export. One person says, “I can look at the timeout.” Another says, “We also need a better error message.” Both would improve the export. But the investigation can finish while the error message stays exactly as it was. A different person might accept the interface change. These are two responsibilities we can assign and accept separately.

For each, keep a short account of the work, who is taking it and what would let someone accept the result. Link the conversation that explains why it matters. The person who turns the suggestion into work is its creator; the original speaker remains the source of the suggestion. An agent reading the transcript needs the same distinction. Spotting an action is useful. Assigning it to somebody requires permission to do so.

<a id="ordinary-discussion-and-accountable-change"></a>

## Ordinary discussion and accountable change

Now somebody writes “done”. Is the investigation done? Is the patch ready? Has the customer accepted the result? Before changing the record, the system needs to know which responsibility the person means and whether they can make that decision. They should be able to decide in the conversation where they are already working.

Small teams can make these distinctions verbally. A formal system becomes useful when work crosses time, organisational boundaries or several independently acting participants. The point is to preserve the agreed meaning, not to impose ceremony on every helpful exchange.

In the export example, “I can look at the timeout” could become an agreed investigation: reproduce the timeout on the stated export, report its cause or the missing evidence, and return that result to the person accepting the investigation. “We need a better error message” remains a separate proposed change until someone takes it. When the investigator says “done” and supplies a trace, the investigation is ready for its agreed acceptance; the interface change has not magically finished alongside it.

The reviewer could reply to that investigation, “Accepted: this trace answers the timeout investigation.” In Weave's design, that message carries the decision. The reviewer's identity must be bound to someone entitled to accept this exact work, and the supplied result must meet the agreed conditions. The same checks apply whether the decision arrives through chat or another interface. Once they pass, acceptance is recorded and the work's card updates; the reviewer is not asked to confirm again. A repeated delivery of the message must not produce a second acceptance. If the message leaves the item unclear, the system asks which one is meant. If the reviewer lacks authority or a condition is unmet, it explains the refusal where the decision was made and leaves the work unchanged.

If an attempted closure lacks that acceptance, Weave's intended response is to keep the item open and identify the missing condition. The refusal is useful because it preserves the team's agreement. The investigator can supply the absent result or ask for the agreement to change, rather than losing the distinction under a successful status update.

The resulting history is small but consequential:

| In the illustrative export investigation | What the work record retains |
| --- | --- |
| A colleague suggests looking at the timeout | The source exchange, still a proposal |
| An authorised participant creates the investigation | That participant as creator, with the original speaker and message kept as the source |
| An investigator takes the work | The assignment, current attempt and agreed result |
| The investigator posts a trace and writes “done” | The comment and supplied result, without silently closing the item |
| The entitled reviewer accepts the stated investigation in an unambiguous reply | One recorded acceptance and an updated card, without another confirmation |

The suggested interface fix remains beside the completed investigation. We have an answer about the timeout; somebody still needs to take on the proposed error-message change. The two records let the team see both.

<a id="handover-changes-the-future-not-the-past"></a>

## Handover changes the future, not the past

Suppose the investigator leaves the role. Work nobody has started can move to the verified successor. Work already in progress stops accepting new effort until the handover is agreed: establish what has happened, what permission still applies and what the successor is taking on. The completed timeout investigation keeps the person who did it. Replacing their name everywhere would tidy the task list by making its history false. The handover needs its own record, whether work passes between two people, a person and an agent, or two agents.

Recurring work has a related boundary. “Review this every month” is a schedule; this month's review is an occurrence. One successful occurrence cannot stand for the next, and a missed occurrence needs an explicit policy rather than disappearing behind the schedule's active status.

<a id="what-closes-the-responsibility"></a>

## What closes the responsibility

The task should close against its agreed result, not because the conversation went quiet. A provider can supply a result while the consumer still disputes its adequacy. [Delivery and acceptance](https://rawthoughts.in/collections/practice/two-meanings-of-done/) need to remain visible separately. At the next month's review, this month's result should have its own acceptance, the next occurrence its own responsibility, and a handover its account of what the earlier participant actually did. Conversation can remain informal because the record carries the commitments that need to survive it. The team can then return to discussing the problem, rather than arguing over which remark became a promise.


Reading path: [Practice](https://rawthoughts.in/collections/practice/) > [Turning a conversation into work](https://rawthoughts.in/collections/practice/turning-conversation-into-work/)


Source code for [Weave](https://github.com/getHarshOnline/weave) is credited to [Harsh Joshi](https://getharsh.in/about/).

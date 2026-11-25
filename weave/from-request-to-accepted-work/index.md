Title: From a request to accepted work

[Read HTML](https://rawthoughts.in/weave/from-request-to-accepted-work/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="from-a-request-to-accepted-work"></a>

# From a request to accepted work

A customer writes in: the export timed out, and the error told them nothing. Two things need doing. Someone has to find where the timeout happens, and someone has to write an error message that actually helps. They are different jobs that may finish on different days, and both still answer to the same complaint. [Weave](https://rawthoughts.in/weave/) keeps each piece of work tied to the request it came from, with its own person responsible and its own reviewer. Weave is not built yet; the steps below follow its design.

<a id="continue-an-export-investigation"></a>

## Continue an export investigation

Agree what each job should produce before assigning it. For the investigation, that means a trace and an explanation of where the timeout occurs. For the message change, it means proposed wording, evidence of its behaviour and review by the receiving team. Each work item refers to the customer’s original report.

| Role | Responsibility in the investigation |
| --- | --- |
| Creator | Makes the investigation a definite commitment |
| Assignee | Supplies the agreed trace and explanation |
| Reviewer | Decides whether that result meets the agreed conditions |
| Customer | Reported the problem and needs the export to work |

The customer raised the problem; the creator made the work exist. Those can be different people. An agent could investigate and a human review the result. One person could hold several roles where the rules allow it, but each action still records the role they used.

[An agent joins the team](https://rawthoughts.in/weave/an-agent-joins-the-team/) follows the membership and role behind an assignment, including how the agent appears in conversation under its own identity.

<a id="let-a-conversation-become-definite-work"></a>

## Let a conversation become definite work

The customer’s message starts the conversation. The person allowed to commit the team records what it will deliver, where the request came from and who will decide whether the result meets the agreement. The investigator takes responsibility for supplying the trace and explanation.

**Important**

**That assignment does not give the investigator access to customer data or permission to send messages.** Those permissions must already cover the action. An existing work item can carry the request if it uniquely matches the responsibility; a similar title is not enough.

When the investigator supplies the trace and writes “done”, the comment keeps their report. Submitting the investigation for review is a separate action. The reviewer then decides whether the trace and explanation answer the agreed question.

The reasoning behind this distinction is in [Turning a conversation into work](https://rawthoughts.in/collections/practice/turning-conversation-into-work/).

<a id="keep-the-result-and-the-remaining-responsibility-visible"></a>

## Keep the result and the remaining responsibility visible

Accepting the investigation leaves the message change open. Accepting the message change still leaves a further question: can the customer complete the export? That outcome needs its own check against the goal agreed before the work began.

A provider may accept its own delivery while the receiving team asks for a correction. Weave keeps both decisions and the evidence behind them. A missing trace leaves a clear request for evidence; a disputed explanation leaves the review and correction visible.

If the review cannot go through, the next step depends on what happened. A missing trace calls for the trace. A changed work item calls for reading its current version. Agents decide far more often than people, so by the time one writes, what it read has usually changed: a read says what else to read, and a write is checked for what it affects before it is committed alone, made together with others or proposed to the owners. If a reply gets lost, check whether the first request took effect before sending it again. Developers can see how the system reports each case in [command outcomes](https://docs.rawthoughts.in/weave/concepts#every-command-ends-in-one-of-four-outcomes).

<a id="hand-over-the-investigation"></a>

### Hand over the investigation

Unstarted work can pass to a verified successor. An active attempt needs an explicit handover: pause new effort, account for the work already done and resolve who may continue. The successor needs the existing results, remaining responsibility and any outside action whose outcome is still uncertain.

The first investigator keeps credit for the trace they produced and the role they held. The successor takes responsibility for the work that remains. If someone loses permission to act, their unfinished work comes back for a decision about who may continue.

Suppose you review the exports every month. Each review is its own piece of work with its own acceptance: this month's stays separate from next month's. A missed review follows the schedule's stated policy, so it cannot disappear as the calendar advances.

<a id="review-in-chat"></a>

### Review in chat

Chat is an optional way to reach the same work. The person named to review the investigation could reply, “Accepted: this trace answers the timeout investigation.” The message can carry the decision once Weave can identify the sender, the work they mean and the decision they are allowed to make. The reviewer should only need to approve once.

If “approved” could mean either the investigation or the message change, the system asks which one. A card opens the current record and shows when its information is stale or unavailable. It does not create another task to maintain. The same card, with the same fields and the same checks, appears in whichever chat room, assistant or browser client the team uses; Weave describes it and the surface renders it. Being mentioned grants neither access to the record nor membership of the room.

<a id="run-the-relationship-as-well-as-the-task"></a>

## Run the relationship as well as the task

The investigation can sit within a mandate, a particular commercial commitment to the customer. The account relationship continues across mandates. An account manager keeps that continuity; an account executive carries a particular opportunity or promise. Delivery still has its own assignee and reviewer.

[Run a relationship across several mandates](https://rawthoughts.in/weave/relationships-and-mandates/) follows an ongoing reporting service alongside a proposed integration. It shows how a changed assessment can affect one opportunity without changing the service already owed.

<a id="carry-an-observation-through-review"></a>

## Carry an observation through review

Repeated export failures may begin as a Radar observation, something noticed that is worth investigating. The traces, possible explanations and counter-evidence belong together until the reviewer can decide what they establish. Accepting a finding does not assign its follow-up automatically; the finding becomes work only when someone takes responsibility for it, with an owner and an agreed result.

[Review an observation before it becomes work](https://rawthoughts.in/weave/review-an-observation/) follows that decision, including rejection, deferral and a review that finds no material change.

<a id="client-and-provider-keep-separate-records"></a>

## Client and provider keep separate records

A client and a provider each keep their own records and acceptance. The client offers an investigation; the provider decides whether to take it on. Delivering a trace on the provider's side does not accept it for the client.

An outside contact can stay in the relationship history without becoming an internal member or software user. Linking records for the same person across organisations preserves each side's history and access rules. The developer guide to [Instances](https://docs.rawthoughts.in/weave/instances) explains this exchange; the [relationship example](https://rawthoughts.in/weave/relationships-and-mandates/) follows its commercial consequences.

<a id="define-the-records-and-actions-your-organisation-needs"></a>

## Define the records and actions your organisation needs

A domain defines the kinds of records, relationships and actions an organisation needs. The first domain, commercial work, covers accounts, people, evidence, Radar observations, goals, work, comments, files and schedules. The SDK lets other organisations describe their own domains.

The developer guide [Extending Weave](https://docs.rawthoughts.in/weave/extending) explains how those rules are defined and versioned. For the people doing the work, an important consequence is that a new definition cannot silently change what an earlier investigation meant or how it was accepted.

<a id="work-independently-or-with-pale"></a>

## Work independently or with Pale

Weave's design serves an organisation of people alone. Chat, agents and [Pale](https://rawthoughts.in/pale/understand-your-world/#use-connected-applications-for-their-own-strengths) are optional. With Pale connected, Weave keeps the business records and work; Pale checks permission and coordinates permitted work. Their histories link where they concern the same work.

The path to [Scope](https://rawthoughts.in/scope/) for context, [Counsel](https://rawthoughts.in/counsel/) for judgment and [Reckon](https://causality.in/reckon/) (on Causality) for evaluation goes through Pale. Without Pale, Scope still reads Weave directly and is how an agent reads Weave; Weave itself never calls Scope. [Gazette](https://rawthoughts.in/gazette/) may read Weave facts directly for publication. These connections are the work in front of Weave once its first vertical runs.

<a id="availability"></a>

## Availability

No Weave service runs yet. The first version is a headless service, accessed through APIs, SDKs, a command line and agent interfaces. It ships no browser application of its own: the cards and views it describes are rendered by the surfaces a team already uses, and a browser client is one more of those. It has no built-in models. The [developer overview](https://docs.rawthoughts.in/weave/overview) explains the architecture for anyone considering an integration or extension.


Reading path: [Weave](https://rawthoughts.in/weave/) > [From a request to accepted work](https://rawthoughts.in/weave/from-request-to-accepted-work/)

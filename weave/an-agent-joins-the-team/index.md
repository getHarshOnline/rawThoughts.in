Title: An agent joins the team

[Read HTML](https://rawthoughts.in/weave/an-agent-joins-the-team/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="an-agent-joins-the-team"></a>

# An agent joins the team

An editor asks an agent to check the links in a collection of articles. The agent should have a name, an assigned job and a place to report its findings. The editor should be able to ask it about a broken link without wondering which of several agents answered through one shared bot.

In Weave's design the agent joins like any member. Consider a publication team that connects [Weave](https://rawthoughts.in/weave/) to [Pale](https://rawthoughts.in/pale/): Weave keeps its relationships and work, and Pale configures the agents' roles and coordinates their permitted actions. The service is not built yet, so this example follows the design.

<a id="give-the-agent-a-place-in-the-organisation"></a>

## Give the agent a place in the organisation

The team authorises an agent to act as its publication checker. Its role covers reading the selected draft articles, checking their destinations and preparing a report. The editor keeps responsibility for accepting the report and deciding whether the publication is ready.

On this connected path, adding the agent and granting its role is an authorised change in Pale's configuration, and Weave records the resulting membership and role. Creating a task for an unfamiliar name or mentioning that name in chat adds no member and grants no permission.

The role and the actor answer different questions. The publication checker is a responsibility that might later pass to another agent. The particular agent keeps its own identity and history, including the checks it actually performed. An organisation can then change who holds a role without changing who did the earlier work. Which software runs the agent and which model it uses are recorded with each act but do not change who the agent is: the same agent, run tomorrow on different tooling, reads and writes the same records under the same name.

<a id="agree-one-result-the-editor-can-review"></a>

## Agree one result the editor can review

The editor creates a specific assignment: check the selected collection's links and supply the destination, result and any unresolved problem for each one. The work names the collection revision and the editor who will review it. A colleague's suggestion that someone should “check the site” can remain a proposal until the responsibility is made definite.

The agent takes the assignment under its publication-checker role. That assignment supplies neither access to unrelated drafts nor permission to send messages to authors outside the team. If a destination is unavailable, the report should distinguish an unavailable page from a confirmed broken link. A missing result remains visible rather than turning into a successful check.

This gives the human reviewer something concrete to assess. The agreed job is a link report, with enough evidence to understand its findings. It is not an instruction to rewrite an author's position or to publish the collection.

<a id="let-the-agent-speak-as-itself"></a>

## Let the agent speak as itself

In the team's permitted chat, the agent appears under its own identity. It can explain that a destination moved, ask about an ambiguous reference or point the editor to its completed report. Another agent checking figures appears separately, with its own assignment and contributions.

The work card opens the current Weave record. It shows who is responsible and what happens next, rather than creating a second task in the conversation, and it looks the same in whichever chat room or assistant the team uses. The room sees only the material it is allowed to receive; being mentioned in the report does not make an outside author a room member.

**Important**

**A message saying “done” is a report, not acceptance.** The agent submits its result for review. The editor decides whether that result meets the assignment.

If the editor replies that the link report is accepted, that message carries the decision when the system can identify the editor, the exact work and the permission to accept it. An ambiguous “approved” needs clarification. If acceptance was recorded but the reply was lost, recovering the result does not require the editor to approve the same report again.

<a id="keep-acceptance-attached-to-what-was-checked"></a>

## Keep acceptance attached to what was checked

Accepting the link report finishes that assignment. The figure check could still be open, and the publisher would still decide whether the collection should go out. [Gazette](https://rawthoughts.in/gazette/) builds the publication from the supplied writing and configuration; a successful link report does not supply an author's acceptance or a publisher's permission.

If the articles change after the check, the earlier report remains a report about their earlier revision. The team can assign a further check for the changed material without pretending the first agent reviewed it already.

<a id="hand-the-role-over-without-rewriting-its-history"></a>

## Hand the role over without rewriting its history

Suppose another agent takes over publication checking. Unstarted work moves to the verified successor. An active check pauses further effort until an explicit handover accounts for the results already obtained, the links still unresolved and any outside request whose outcome is unknown.

The successor's work carries its own identity. Earlier findings keep their original contributor. Revoking the first agent's role stops further action under that role and leaves the completed history intelligible.

The point is ordinary teamwork: a person can see who joined, what they may do, which job they accepted and who reviewed their result. [From a request to accepted work](https://rawthoughts.in/weave/from-request-to-accepted-work/) develops the same responsibilities across a customer's investigation and delivery. Weave's design lets organisations use it with people alone, and agents, Pale and chat are optional connections to that shared work model.


Reading path: [Weave](https://rawthoughts.in/weave/) > [An agent joins the team](https://rawthoughts.in/weave/an-agent-joins-the-team/)


Source code for [Weave](https://github.com/getHarshOnline/weave) is credited to [Harsh Joshi](https://getharsh.in/about/).

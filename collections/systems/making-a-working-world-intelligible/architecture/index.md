Title: How Pale fits together

[Read HTML](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/)

Author: Harsh Joshi

<a id="how-pale-fits-together"></a>

# How Pale fits together

An agent revises a project guide. The explanation depends on code in one repository, an earlier design decision and an essay that needs the same correction. Each lives somewhere else, and permission to edit the guide does not include permission to publish it. The [connections between writing and projects](https://getharsh.in/collections/building-products-and-teams/building-a-place-to-think/) (on getHarsh) have to survive the chat where the change began.

[Pale](https://rawthoughts.in/pale/) makes that connected world usable by people and their agents without reconstructing it for every task. The need extends beyond publication: a household shares some responsibilities, while a company serves clients that govern themselves. The engine checks requests against their permissions, connects the systems doing the work, records the path and carries unfinished obligations forward. Each application keeps its own records, while the person can understand how the parts serve the objective.

[The product guide](https://rawthoughts.in/pale/understand-your-world/) starts with adding instructions to a repository and reviewing a workspace change. Here, the question is how those tasks fit into work that crosses applications.

<a id="describe-the-world-and-its-permissions"></a>

## Describe the world and its permissions

A workspace describes who can act, their relationships, the rules they work under and the capabilities they can use. Its compiler checks those declarations and packs a checked configuration into a fixed version, called a generation. Sessions can reuse that version without reinterpreting every relationship before each call. Preparation and maintenance also cost effort; [The cost of understanding](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/the-cost-of-understanding/) asks when reuse earns that effort back. Reviewing a change, authorising its effects and activating the new generation remain separate: compiling a description cannot grant a missing permission.

The resident engine works through ports: interfaces that keep its operations independent of a particular storage or transport mechanism. Adapters supply those mechanisms. Application integrations supply a different kind of knowledge: what an operation means in the receiving application, what can fail and how to check what happened. Replacing a transport therefore need not change what the request asks for or which obligations remain. Replacing an application can change those answers; its integration has to account for the difference.

![A compiler turns a workspace and reusable packages into configuration for a resident engine that connects hosts with independent applications.](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/compiled-world.svg)

The upper path compiles the declared world. Below it, applications keep their own records while ports, integrations and adapters carry the work between them.

Suppose you ask Pale to create a ticket. The engine checks that the request is permitted and preserves its identity. The integration translates it into the ticket system's terms, including how to find out whether creation succeeded when the reply is lost. An adapter carries the call; the ticket system owns the ticket. A lost reply is no reason to create it again. Deciding whether another attempt is safe depends on the application's rules and the work Pale still needs to resolve. Replacing the adapter changes how the request travels. Replacing the ticket system can also change what the request means and how its outcome is established.

The distinction between a project and the place its agents work is equally important. Consider an illustrative maintenance project using two repositories, with a review workspace exposing both and a repair workspace exposing only one. The project, repositories and execution workspaces are separately declared objects. A machine binding locates their checkouts; a provider binding identifies the executor. Moving a checkout changes where Pale finds its files, without changing which project they serve. Including another repository in the review changes the files available for that task without granting permission to merge or release them.

The maintenance example follows these stages:

| Stage | What happens in the maintenance example | What the next stage receives |
| --- | --- | --- |
| Source modules | Repository identities, the two working sets and the reviewer's permitted role | Declarations with their owners and the exact versions they import |
| Linking and policy resolution | Resolve shared repository references and combine applicable restrictions and obligations | One consistent set of objects, relationships and rules, or a specific conflict |
| Generation | Combine the checked relationships and rules with the file locations and chosen executor | A fixed version of the checked working environment |
| Materialisation plan | Compare selected instructions and host settings with the files already there | Exact proposed file changes for review |
| Apply and read-back | Write only the approved files and blocks Pale manages | A record of the write and any difference between the planned and observed files |

<a id="one-engine-several-entrances"></a>

## One engine, several entrances

The resident engine compiles the workspace and checks requests and actions against the permissions declared there. It manages startup, shutdown and recovery, keeping the journal needed to resume after an interruption. It also records how requests and results came about, identifies callers, connects people's separate Pale services over private links, and monitors the engine and its connections.

One Rust SDK exposes those responsibilities. Python, JavaScript, Go and WebAssembly wrappers extend that interface rather than reproduce the engine in four languages. Command-line, MCP, language-server, coding-session and agent-handoff interfaces are different entrances into the same work.

That arrangement gives an integration a small job. A repository editor need not implement the journal to ask about a declared workspace. A model worker need not know how a ticket service authenticates. The application integration owns that translation; the technical adapter owns how bytes reach it. Reusable procedures belong in packages, while an adopter's people, chosen systems, paths and policies belong in their workspace. The system can therefore be reusable without distributing somebody else's working world as its defaults.

<a id="a-world-a-person-can-inspect"></a>

## A world a person can inspect

The compiled structure also gives the person a way to inspect their own arrangements. PaleUniverse connects the written Source with its World, shows the full arrangement of organisations and responsibilities, and compares a current world with a proposed Change. A relation, its meaning and its evidence come from the underlying system; the spatial view makes the structure easier to explore. An accessible presentation supplies the same answers.

That is a different job from showing a task card. A card helps someone continue one responsibility. A world view helps them notice that several responsibilities depend on a role, that a service crosses an account boundary or that a proposed change leaves a result without anyone responsible for accepting it. Stable structure makes the consequences of a change visible across scales.

<a id="separate-systems-contribute-separate-answers"></a>

## Separate systems contribute separate answers

[Scope](https://rawthoughts.in/scope/) prepares permitted, fresh context; [Counsel](https://rawthoughts.in/counsel/) offers judgement; and [Reckon](https://causality.in/reckon/) (on Causality), from [Causality](https://causality.in/) (on Causality), evaluates the evidence from a comparison. Those contributions answer different questions in a task: which information may be used, what decision the evidence supports and how the result compares with an alternative. Advice or a favourable evaluation does not give the caller permission to act. The system carrying out the action still checks that permission. [Weave](https://rawthoughts.in/weave/) keeps organisational relationships and accountable work, while [Gazette](https://rawthoughts.in/gazette/) compiles publications. An integration connects the contribution a task needs without making every component a prerequisite or moving its records into Pale.

<a id="work-that-survives-an-interrupted-session"></a>

## Work that survives an interrupted session

Suppose a provider performs an action but its reply is lost. The caller cannot safely treat silence as either success or failure. It needs a way to read back the effect, identify the original request and decide whether another action is permitted. Recording that uncertainty is part of the system's job, not an exception to hide.

Asking for an action, performing it, confirming what happened and accepting the result are separate steps. Pale saves its own permission decisions and unfinished commitments in a durable journal before acting on them. After an interruption, it uses that journal to recover what it may do and what it still has to settle, then checks the application's records for what happened there. Recovery can mean waiting or asking for a decision; replaying the journal is not permission to repeat the actions it records.

<a id="a-configuration-can-have-a-successor"></a>

## A configuration can have a successor

Work also produces evidence about what could improve. A procedure may repeatedly miss a distinction; a different model may handle an exception better while costing more. [Comparing those changes apart and together](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/improving-the-system-between-runs/) can distinguish the contribution of each from their interaction. The comparison asks whether a candidate actually improves the work. Once a successor is accepted and activated, new sessions can use it while existing sessions retain the conditions under which they began.

Some changes reach the description itself. A workspace that records who owns a repository may still lack the relation needed to say who can accept a particular result. Adding that distinction changes which questions the world can answer. Pale can compile a revised declaration while keeping the language's meaning fixed; changing that meaning raises a different problem. Either change still needs its grounds and authorisation.

<a id="when-the-organising-architecture-changes"></a>

## When the organising architecture changes

[Causality’s research programme](https://causality.in/about/) (on Causality) connects that problem to [MONAD’s mathematics](https://causality.in/monad/) (on Causality) and to [HENA](https://causality.in/hena/) (on Causality), a swarm of MUON units aimed at the counterfactual rung of the [ACI framework](https://causality.in/blog/beyond-the-mirage/) (on Causality). Pale would stand to HENA as a harness stands to the model it runs: HENA the intelligence, Pale the harness through which it acts. How far that goes remains open.

At the unit scale, a [MUON](https://causality.in/muon/) (on Causality) candidate could be compared with the model serving Counsel. At the collective scale, HENA could absorb some coordination expressed directly in Pale, leaving Pale to connect the learned engine to applications, people and consequences. A separate experiment could place such an engine behind a coding harness. Each path would have to preserve what its surrounding system needs and demonstrate what it improves. This gives Pale a reason to keep its interfaces narrow: the architecture beneath the experience can change without asking the person to rebuild their working world around it.

<a id="returning-to-the-work"></a>

## Returning to the work

When you return to interrupted work, you need to know where things stand: which requests were permitted, which applications returned results, which actions still have an uncertain outcome and which decisions are yours. Keeping those records connected lets you continue without moving every application's records and rules into Pale.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Making a working world intelligible](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/) > [How Pale fits together](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/)

Previous in journey: [The cost of understanding](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/the-cost-of-understanding/)

Next in journey: [Records, context and decisions](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/records-and-context/)


Source code for [Pale](https://github.com/getHarshOnline/pale) is credited to [Harsh Joshi](https://getharsh.in/about/).

Title: Introduction to Pale

[Read HTML](https://rawthoughts.in/pale/understand-your-world/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="introduction-to-pale"></a>

# Introduction to Pale

A new coding session begins with a familiar job: explain the project, point the agent to its instructions and make sure it knows how to check a change. When several repositories share a way of working, those explanations can drift apart. Changing the review method in one place leaves you wondering where else it applies.

[Pale](https://rawthoughts.in/pale/) lets you write your world once, and compiles it into the permissions and context the coding tools you already use ask for at every step. You describe that arrangement once, select the methods a responsibility needs and inspect what a change would affect, whichever host and model an agent runs on. Its local configuration tools let you begin with the repositories you already use.

<a id="what-you-can-use-now"></a>

## Start with a repository

Start with either task using a local source build:

- [Add coding instructions to a repository](https://rawthoughts.in/pale/materialize-repository-guidance/). Review what Pale proposes for Codex or Claude Code, then install it alongside the instructions you already keep there.
- [Inspect your workspace](https://rawthoughts.in/pale/inspect-your-workspace/). Find what applies to a project and compare a proposed edit before changing files.

**Note**

**Today you can try the two local tools above.** Connecting your everyday chat tools and handing work to agents needs a deployed Pale service and its integrations, which are the part being built.

<a id="your-workspace-gives-the-work-its-context"></a>

### Put the responsibility in its setting

Suppose the job is reviewing code. Your workspace says which project the repository serves, who carries the responsibility and which applications are involved. The same description can distinguish your own project from client work, or a repository from the service that runs its code.

When review is a continuing duty, a **role** names that duty separately from whoever performs it. The reviewer can change while the responsibility remains. [The structure a responsibility needs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/starting-with-the-duty/) explains when to introduce a role and what a handover should preserve.

A project can run in several settings, each an **execution workspace**. A **machine binding** supplies the paths to files and executables on one computer. If Pale cannot find the checkout, fix its machine binding. If the review belongs to the wrong project, fix that relationship in the workspace. Connecting an application still requires the access that application grants.

<a id="select-procedures-for-the-responsibility"></a>

### Choose how the review should work

A **Package** supplies reusable roles, procedures and policies. Select a code-review procedure for this responsibility, and Pale can turn it into instructions and skills for your coding host. The repository keeps its own build commands and conventions alongside them. After installation, ask the agent to use the guidance on a small task and follow its findings back to the code. The useful question is whether those instructions helped it do the work.

<a id="understand-a-change-before-applying-it"></a>

## See what a changed method affects

Now suppose you choose a different review procedure from a Package you already use. Which responsibilities depend on that choice? [Compare the current and proposed workspaces](https://rawthoughts.in/pale/inspect-your-workspace/#compare-a-candidate-without-applying-it) to find them. A responsibility can depend on the change even when its final settings stay the same; the review shows that connection too.

The comparison returns your decision without saving it to either workspace. If you also want to install different instructions, [read the file plan](https://rawthoughts.in/pale/materialize-repository-guidance/#save-the-plan-before-changing-repositories) before applying it. Seeing how a choice affects the workspace and agreeing to change repository files are separate steps.

<a id="the-connected-work-experience-pale-is-building-toward"></a>

## When the work crosses applications

A code review is one responsibility. An account review might involve several: the customer system holds the account, a reporting tool produces a comparison, and the receiving team decides whether it is useful. A report for the wrong period still needs correction after the tool finishes. Pale carries that work between applications and brings you back into the conversation when a decision is needed.

That requires more than calling tools. The design distinguishes asking contributors for advice, handing work to another system, checking progress and requesting a stop. If the reporting tool's reply goes missing, it may already have acted. Pale checks the application's records before trying again.

The coding host must enforce Pale's permission decisions: a refusal has to prevent the action. [How Pale fits together](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/) explains how permission, context and recovery connect the host to Pale's service.

<a id="use-connected-applications-for-their-own-strengths"></a>

### Use connected applications for their own strengths

[Weave](https://rawthoughts.in/weave/) keeps the organisation's account and work records. [Scope](https://rawthoughts.in/scope/) supplies permitted context for a task, while [Counsel](https://rawthoughts.in/counsel/) provides judgment and memory assistance. [Reckon](https://causality.in/reckon/) runs the evaluation lab, and its design adds the services for investigating whether a changed method helped. What Reckon learns comes from Pale's genealogy, the history of context: an append-only map of references showing where work came from, what it relied on and what followed, with each record staying in the system that owns it.

Integrated requests for Scope's context, Counsel's judgment and Reckon's evaluations pass through Pale. Each receiving application checks the caller's permission and keeps responsibility for its own result. Each product can also be used without the others under its own access rules, except Scope, which works with Pale, Weave or both; adopting one does not require adopting the whole set.

For example, [Gazette](https://rawthoughts.in/gazette/) builds a publication directly from selected sources, which can include permitted Weave records. It needs no live context, judgment or evaluation call to compile them. Pale can arrange the publication work through Gazette's own interface.

<a id="explore-the-whole-picture-with-paleuniverse"></a>

### Explore the whole picture with PaleUniverse

PaleUniverse connects the picture of your world to the source that describes it, and is planned for a coming release. Its first views show your World, open the Source behind it and compare a proposed Change, so you can follow a responsibility back to its declaration. Later views follow work in progress (Now), system health (Doctor) and a result's genealogy: what it relied on, what changed and what followed (Trace).

<a id="related-ideas"></a>

## The question behind the system

[Building a place to think](https://getharsh.in/collections/building-products-and-teams/building-a-place-to-think/) explains the motivation: returning to work without having to reconstruct its context each time. Structure takes effort to prepare and maintain, so [the cost of understanding](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/the-cost-of-understanding/) asks whether it repays that effort. [Improving the system between runs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/improving-the-system-between-runs/) follows how results could inform a change to the method.

[MONAD](https://causality.in/monad/) studies what descriptions preserve and when they need to change. [MUON](https://causality.in/muon/) and [HENA](https://causality.in/hena/) explore adaptive units and their collective organisation. These research questions connect to Pale's ambition while the current tools work with an explicit workspace.

[Harsh Joshi](https://getharsh.in/about/) is Pale's author, and RTEPL owns the project. Pale comes in two profiles of the same community code, with the same rights: Bare selects the smallest working set of parts, and Curated assembles a reference selection of connected products.

<a id="choose-your-next-step"></a>

## Build an integration

To embed or extend Pale, read the [developer architecture](https://docs.rawthoughts.in/pale/architecture) or [choose an SDK](https://docs.rawthoughts.in/pale/sdks). For the first repository task, return to [adding coding instructions](https://rawthoughts.in/pale/materialize-repository-guidance/) with a repository you control.


Reading path: [Pale](https://rawthoughts.in/pale/) > [Introduction to Pale](https://rawthoughts.in/pale/understand-your-world/)

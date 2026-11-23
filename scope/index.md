Title: Scope

[Read HTML](https://rawthoughts.in/scope/)

Author: Harsh Joshi

<a id="scope"></a>

# Scope

Scope gives an agent the smallest fresh account it needs to continue a task. It brings the question back together with the decisions, sources, people and open questions that give it meaning. When the world changes, the context needs to change with it, so Scope works as a cache does in any development stack: it is optional, keeps derived context over what Pale and Weave hold and is never the source of truth. The repository holds an empty Rust library today, and the service that answers an agent is the work in front of it.

<a id="remember-the-world-around-the-task"></a>

## Remember the world around the task

A new session should not mean explaining the project again. Among [the products](https://rawthoughts.in/products/), Scope brings the context a task needs. It works with [Pale](https://rawthoughts.in/pale/), [Weave](https://rawthoughts.in/weave/) or both: Weave keeps the records and points to the files around them, Pale keeps the history of what work relied on and what followed, and Scope combines them into one account an agent can ask for what it needs. Without Pale, Scope is how an agent reads Weave. With Pale, Scope reranks as the history of what work relied on and what followed updates, and writes back a pointer to the context it gave each agent, so the chain from what an agent was given to what it did stays whole. It helps an agent find the owning account, understand why a choice was made and see what remains open. Scope selects from snapshots supplied by their owners. The original knowledge stays with those owners, so rebuilding an index must not lose the thought. Its first use is to help Claude and Codex resume work across [Harsh Joshi](https://getharsh.in/about/)'s connected writing and projects.

People and circumstances belong in that account too. How a colleague prefers a decision explained can improve a draft; it cannot give an agent permission to send it.

- [Docs](https://docs.rawthoughts.in/scope/overview "Developer documentation") 

- [Learn](https://rawthoughts.in/scope/context-for-a-task/ "Use-case guide and practical applications") 

- [GitHub](https://github.com/getHarshOnline/scope "Explore on GitHub") 

- [Mentions](https://rawthoughts.in/scope/mentions/ "Writing that discusses or references this product") 

<a id="pick-up-the-work-with-its-context-intact"></a>

## Pick up the work with its context intact

Consider returning to an essay in a fresh agent session. Its title is not enough: the agent needs the original argument, the current draft, the publication's purpose and the decisions that explain the revision. [A worked publication slice](https://rawthoughts.in/collections/systems/context-that-helps-the-work/finding-the-right-context-for-the-work/) shows those sources together.

1. 
   
   <a id="start-with-the-task"></a>
   
   ### Start with the task
   
   Say which essay is being revised, who it is for and what needs to change. Developing the argument and approving its publication are separate tasks.

2. 
   
   <a id="use-the-sources-the-task-can-see"></a>
   
   ### Use the sources the task can see
   
   Source owners provide permitted snapshots. Scope checks their use and freshness before searching them, keeping the original argument and current decisions ahead of optional background.

3. 
   
   <a id="receive-a-useful-account"></a>
   
   ### Receive a useful account
   
   Read the original, the working draft and the relevant decisions together. A useful slice explains what changed and what remains unresolved, with links back to the sources. A short summary that loses the argument has not done the job.

4. 
   
   <a id="continue-as-the-world-changes"></a>
   
   ### Continue as the world changes
   
   If a decision changes, refresh the context that depended on it. The previous answer should still explain what the agent knew then, subject to the source owner's retention rules. Unrelated work can continue.

## Collection contents

- [Context for a task](https://rawthoughts.in/scope/context-for-a-task/)
- [Keep a task current](https://rawthoughts.in/scope/keep-context-current/)
- [Understand the retrieval modes](https://rawthoughts.in/scope/strict-and-model-assisted-context/)

<a id="questions-about-scope"></a>

## Questions about Scope

**Does Scope grant access to a source?**

Scope gives a task its context at every step, bounded by what that task may see. Access stays with the source's owner: owners supply copies with secrets removed, and Scope checks what the caller may use for the task before it searches anything, so it widens no boundary of its own. On the integrated path, [Pale](https://rawthoughts.in/pale/) carries the request and response.

**Does it need a model?**

Scope can bring a task its context with or without a model; the choice decides what material may go into the account. Strict mode excludes all model-made material, including cached summaries and embeddings, so every line comes from a source owner's copy. Full mode can use [Counsel's memory host](https://rawthoughts.in/counsel/) through Pale, or through a direct library connection when Scope works with Weave alone. Scope and the host each check permission. The [mode guide](https://rawthoughts.in/scope/strict-and-model-assisted-context/) explains that route and permitted fallback.

**Where should I start?**

Follow the [equipment-order walkthrough](https://rawthoughts.in/scope/context-for-a-task/) to see what a useful answer must preserve, how a changed source affects it and what missing information leaves unresolved.

**How does Scope learn whether its context helped?**

Opening or quoting a source does not establish that it improved the work. Scope's learning design compares what was offered, what the agent used and how the task ended. [When context helps](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/) develops that comparison and its connection to [Reckon](https://causality.in/reckon/).

Title: Finding the right context for the work

[Read HTML](https://rawthoughts.in/collections/systems/context-that-helps-the-work/finding-the-right-context-for-the-work/)

Author: Harsh Joshi

<a id="finding-the-right-context-for-the-work"></a>

# Finding the right context for the work

An agent returns to a task about a project and finds a compelling passage. It is the right subject, uses the right words and answers the question neatly. It is also from last year's arrangement, or from another organisation with a similar problem.

The puzzle is finding context that belongs to this work, not merely text that resembles it. A historical account and a current action can need different records about the same project. [Scope](https://rawthoughts.in/scope/) is the ecosystem's cache for that task-specific account, sitting on Pale, Weave or both and, like any cache, optional and never the source of truth. It checks which records the task may use, keeps the facts needed to interpret them, and then ranks the useful detail. The result can be smaller than a broad search while carrying more of what matters. That includes the context around the people doing the work: which relationship a person is acting within, how a decision is made and which communication style fits the recipient. Finding a source and understanding its setting are complementary parts of useful memory.

<a id="what-an-agent-needs-to-resume-an-essay"></a>

## What an agent needs to resume an essay

Scope’s first intended use is publication work: helping an agent resume an essay after a new session starts. The original writing establishes the argument; the current draft shows what has been developed; the publication's purpose explains why the piece belongs there; the current decisions identify what may change. A compressed account that remembers the title but loses the reason for the essay has preserved the wrong thing.

For a revision of [Breath of Cosmos](https://getharsh.in/blog/breath-of-cosmos/), the proposed slice could look like this:

| Context | Why this task needs it |
| --- | --- |
| The original breath-and-cosmos argument | Preserve its passage from a breathing interval to an unbounded frame, including the textual image behind it |
| The current getHarsh edition | See the developed argument and the qualifications beside its model of breath and consciousness |
| The distinct [Sleepwalker reflection](https://sleepwalker.in/blog/the-world-inside-a-breath/) | Keep the question about the observer and the world it can contain connected without making both essays the same piece |
| Current editorial decisions and the reuse terms of each image | Distinguish a drafted revision from accepted publication, and an available image from one cleared for reuse |

**Note**

**Keep the originals within reach.** Owner-supplied snapshots would help Scope assemble this context without replacing the full arguments an editor needs to read. [Gazette](https://rawthoughts.in/gazette/) has the separate job of presenting the resulting articles and their links; receiving this context would grant no permission to publish them.

<a id="someone-helping-two-organisations-does-not-merge-their-records"></a>

## Someone helping two organisations does not merge their records

Imagine someone helping two organisations with similar problems. The same operator and similar vocabulary can make their records look close in a semantic search. That does not make one organisation's private account an available example for the other. The request needs the relationship and purpose under which it is made, not just a query string. The source needs its own permitted uses. A system should not infer either from a familiar project name or the fact that the operator can technically open both files. The distinction also applies within one context. Information available for internal diagnosis may still be forbidden in a public explanation. A summary can carry the same restricted meaning in fewer words; compression does not clear the boundary.

<a id="keep-what-the-task-needs-before-ranking-the-rest"></a>

## Keep what the task needs before ranking the rest

Scope would first check which records the task may use and whether they are still valid and current enough. It would keep the required context, then rank optional material from the remaining records. A relevance score cannot bring an excluded source back. A small token budget cannot silently remove an authority page that changes the meaning of an otherwise attractive passage. The result may be a concise bundle with an authority page and two supporting passages rather than the ten closest excerpts. It may also be an explicitly limited answer because a necessary source is missing. Both are useful: the first carries enough context to interpret the evidence, while the second exposes the gap the task needs resolved.

For an imagined question about whether a service may be offered today, three passages could look equally relevant:

| Candidate source | Relation to this request | Place in the bundle |
| --- | --- | --- |
| Current offering decision | Governs present availability | Required, including its revision |
| Last year's promotional description | Explains the historical proposition | Optional history, labelled as such |
| Another organisation's private deployment | Similar language, outside this request's source population | Excluded before relevance ranking |

A current decision saying the service is unavailable changes the reading of the historical description. Returning only the more fluent old passage would be a smaller answer, but a worse account of the task. The indispensable context is not always the nearest semantic match.

An exact reference could locate the current decision, while keyword search could find its terminology. Following links between permitted records, with a limit on how far the search goes, could reveal a relevant dependency. Model-assisted search could find a supporting passage that uses different words. Each method proposes material from what the caller is allowed to use; none changes that permission. Fixed rules could combine their rankings while keeping owner-pinned items and required context ahead of optional detail. Exact references, keyword search and links between records need no model.

Suppose a toy bundle has a 500-token budget. The required decision and its qualifying context cost 300 tokens, a supporting note costs 120, and a historical example costs 180. The decision plus the note fits at 420; adding the example reaches 600. The example can be omitted with its reason visible. If the indispensable context alone costs 600, ranking cannot solve the problem by discarding the qualification. The system needs a permitted larger budget or an answer that makes the unmet requirement explicit.

<a id="what-reaches-the-answer-besides-the-text"></a>

## What reaches the answer besides the text

A system can omit restricted passages from the response while still using them to shape candidates or ranking. The existence of a result, a changed score or an observable count may then carry information that the caller was not meant to receive. The design must name the isolation it promises. Keeping restricted text out of the answer is one condition. Preventing restricted populations from changing the search result is stronger. Controlling information exposed through timing, caches, counts and errors is stronger again. Claiming the strongest condition because the weakest one passed would make the boundary fictional.

A filter applied after ranking can conceal restricted text while leaving its influence intact. Searching only a genuinely permitted population answers a different isolation question. The comparison between designs has to follow those information paths, rather than treating the label “filtered index” as a description of everything a caller can learn.

<a id="a-relevant-old-statement-can-still-be-wrong-for-the-task"></a>

## A relevant old statement can still be wrong for the task

Freshness is a relationship between a source, a request and a use. An old historical record can be exactly the right source for a historical question. The same record can be inadequate for a current action. A recent edit date does not verify every fact in a document. The response therefore needs to carry the revision and the limitation that matter. If a source has been revoked or a required authority has changed, an immutable cached answer does not become safe simply because its bytes are unchanged. The dependency has moved.

<a id="the-context-bundle-should-show-what-it-leaves-out"></a>

## The context bundle should show what it leaves out

The aim is not to give every agent everything it might conceivably need. It is to give enough context for the particular task, with the sources, omissions and unresolved contradictions that change interpretation. A link to an original is valuable because it lets the reader inspect the reasoning, not because the link makes the summary authoritative. For the agent, the benefit is a shorter route to the right interpretation. It can inspect the source, see which revision supports the answer and notice a missing premise before acting on a fluent summary. Permission to make the eventual change remains with whoever owns the system where it is made; the bundle supplies the context needed to ask and reason well. Whether that bundle actually helped is [a question about the work and its outcome](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-helps/), beyond the relevance score that selected it.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Context that helps the work](https://rawthoughts.in/collections/systems/context-that-helps-the-work/) > [Finding the right context for the work](https://rawthoughts.in/collections/systems/context-that-helps-the-work/finding-the-right-context-for-the-work/)

Next in journey: [When an agent's context changes underneath it](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-changes/)

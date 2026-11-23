Title: Understand the retrieval modes

[Read HTML](https://rawthoughts.in/scope/strict-and-model-assisted-context/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="understand-the-retrieval-modes"></a>

# Understand the retrieval modes

An order number gives you something exact to look up. A question such as “what maintenance does this equipment need?” may require finding instructions that use different words. Scope combines exact searches with optional model assistance. The service that answers an agent is the work in front of Scope; this page follows what its two modes do in that design.

<a id="an-exact-reference-and-a-related-idea-need-different-help"></a>

## When each mode helps

Strict mode can find the approved order revision by reference, or a report through its words and links. Full mode can also connect “maintenance” in the question to “servicing” in the instructions.

| Mode | How it finds context | Model-generated material |
| --- | --- | --- |
| Strict | Reference and keyword lookup, links between permitted records, and fixed rules | Excludes summaries, embeddings and inferred links made by a model |
| Full | The same methods, with model-assisted search or reranking from [Counsel](https://rawthoughts.in/counsel/) | Keeps source and model references with embeddings, candidate links and summaries so they can be refreshed or removed |

Both modes check which records the task may use before searching. Finding a related passage cannot make a restricted record available, and neither mode can invent the missing arrival estimate in the [equipment-order example](https://rawthoughts.in/scope/context-for-a-task/).

<a id="if-the-model-service-is-unavailable"></a>

## If the model service is unavailable

A request can allow a fallback to strict retrieval. Scope identifies that change in the answer, and you can still find the order by reference or search the permitted records by keyword. If the request requires full mode, it must fail rather than silently supply a different kind of answer.

**Tip**

**Try a narrower question if related ideas are not being found.** An exact phrase or reference may be enough. You can also ask the source owner where to look; increasing the answer's size cannot replace the unavailable search method.

<a id="connect-model-assistance-with-permission"></a>

## Connect model assistance with permission

In the integrated setup, [Pale](https://rawthoughts.in/pale/) checks the request and permission to send the selected records, then connects to Counsel's memory service. When Scope works with Weave alone, it runs without a Pale daemon and uses its own grants for retrieval. For full mode it calls the local or remote memory host named in Scope’s configuration through Pale's Counsel port, used as a library.

Permission to retrieve a report and permission to send it to a model are separate. The memory host checks the caller, the selected model profile and whether these records may be processed for this owner, relationship and purpose. It also checks the budget and any withdrawal of permission. Scope checks the returned material before adding it to a retrieval snapshot and again before use.

Counsel's memory and judgment services have separate profiles, models, caches and permissions. Connecting the memory service does not enable the judgment service.

<a id="check-what-a-cached-summary-describes"></a>

## Check what a cached summary describes

Suppose full mode summarised supplier report revision 7 as a partial delivery. Revision 8 then confirms the rest has arrived. The summary's bytes have not changed, but it can no longer answer today's delivery question.

Permission can change even when the report does not. If the owner withdraws permission for model processing, Scope cannot keep supplying the old summary under that withdrawn permission. Retiring the model profile that produced it also stops new use. Restoring an old index or backup cannot undo either change.

To make those checks, Scope keeps the summary connected to its source revision, the model service and profile, and the particular processing request that produced it. The earlier answer may remain evidence of what was known then, subject to its retention and deletion rules.

**Warning**

**A cached summary still needs permission for model-generated material.** If the host becomes unavailable, an allowed strict fallback would use the source reports directly. It would exclude summaries, embeddings and model-inferred links before selecting candidates; their age does not make them model-free.

The [developer mode explanation](https://docs.rawthoughts.in/scope/concepts#scope-works-with-no-model-at-all) describes that separation. Either mode still needs to preserve the approved revision, the reported delivery and the unanswered question, as the [order example](https://rawthoughts.in/scope/context-for-a-task/) shows.


Reading path: [Scope](https://rawthoughts.in/scope/) > [Understand the retrieval modes](https://rawthoughts.in/scope/strict-and-model-assisted-context/)

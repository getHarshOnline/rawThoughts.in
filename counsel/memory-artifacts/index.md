Title: Find knowledge with model assistance

[Read HTML](https://rawthoughts.in/counsel/memory-artifacts/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="find-knowledge-with-model-assistance"></a>

# Find knowledge with model assistance

You need the maintenance procedure for a machine, but searching for “maintenance” misses a manual filed under “servicing the equipment.” Counsel’s **Memory host** helps [Scope](https://rawthoughts.in/scope/) find that connection, with Pale or, where Scope works over Weave, without it. No host runs yet; this example follows one search through the design.

<a id="find-the-procedure-that-applies"></a>

## Find the procedure that applies

A passage about servicing gets you closer, but it may describe another machine or an older procedure. You need the current instruction for this equipment. The four kinds of model assistance help at different points in that search.

| Aid | How it helps | What to check |
| --- | --- | --- |
| Embedding | Represent the meaning of your question and passages as numbers, so similar meanings can be compared | Does the passage actually apply to this machine? |
| Candidate link | Suggest a connection between a machine record and a service instruction | Is the connection supported by its sources and permitted for this request? |
| Summary | Give you a shorter account of a passage | Can you still tell when the procedure applies and what its warnings require? |
| Reranking | Put the most relevant of the eligible results first | Is the highest result current, rather than simply a close match? |

An embedding could bring the differently worded passage into the search results. A suggested link could connect it to the machine record, and reranking could put it ahead of less relevant instructions. You would still check the machine and revision before relying on it. A summary helps you see what a long procedure covers; it cannot safely replace the procedure when you act.

**Caution**

**Open the procedure before acting.** A summary can omit a required shutdown warning or hide a conflict the original makes clear.

<a id="check-whether-the-instruction-may-go-to-a-model"></a>

## Check whether the instruction may go to a model

You may be allowed to read the maintenance instruction without being allowed to send it to a model or share a summary with someone else. In the integrated design, [Pale](https://rawthoughts.in/pale/) checks permission to send it. The memory host checks whether it may process that material, and Scope checks whether it may store and use the returned aid. Permission at one step cannot stand in for the next.

A result identifies its source revision, producing model and purpose. The host works from the material supplied for the request, without browsing source systems or obtaining more records on its own.

<a id="a-derived-artifact-can-stop-being-usable"></a>

## When a summary becomes out of date

If the service interval changes, an old summary must not keep presenting the previous interval as current. Scope checks freshness and permission each time a summary or embedding is used, including results restored from a backup. Depending on those rules, the old result may need to be refreshed, invalidated or removed.

The same applies when access is revoked: a cached summary or embedding cannot preserve permission to use its source. Removing that aid does not delete the owner's original instruction.

The model profile also stays attached to each result. Changing models would not silently relabel old embeddings or summaries as the new model's work. The memory service could be replaced independently of Counsel's judgment service.

<a id="find-the-instruction-without-model-assistance"></a>

## Find the instruction without model assistance

Scope’s **strict mode** is designed to work without this host, since it needs no model. It can still retrieve items their owner has pinned: a maintenance owner might require the shutdown procedure to accompany a machine's service instructions. That pin says to include an item; it is different from fixing a particular source version. Access and freshness checks still come first, so a pin cannot restore a revoked or obsolete instruction. [Understand the retrieval modes](https://rawthoughts.in/scope/strict-and-model-assisted-context/) explains the available retrieval methods and what **full mode** could add through this host.

If the host becomes unavailable, a request allowing strict fallback could continue without model assistance and report that limitation. It would exclude cached model-made aids as well as new calls. A request requiring full mode would stop instead of quietly returning a different kind of search.

Scope working with Weave alone also offers model assistance without running a Pale daemon. It uses Pale’s Counsel port as a library to reach the configured memory host. Scope checks the retrieval request, the host separately checks permission to process the instruction, and Scope checks the returned aid before storing or using it.

Once you have the applicable instruction, you may still have a choice to make. [Frame a useful judgment](https://rawthoughts.in/counsel/frame-a-judgment/) follows that next question through Counsel’s separate judgment service.


Reading path: [Counsel](https://rawthoughts.in/counsel/) > [Find knowledge with model assistance](https://rawthoughts.in/counsel/memory-artifacts/)

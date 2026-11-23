Title: Keep a task current

[Read HTML](https://rawthoughts.in/scope/keep-context-current/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="keep-a-task-current"></a>

# Keep a task current

A supplier has sent a new delivery report. Before rewriting the whole update, find the sentence that depends on the old one. Scope keeps the earlier answer and prepares a fresh account on request. The approval may be unchanged even though the delivery has moved on. The service that answers an agent is the work in front of Scope; the example follows what its design asks of a refresh.

<a id="refresh-the-part-that-changed"></a>

## Refresh the part that changed

In the [equipment-order example](https://rawthoughts.in/scope/context-for-a-task/), approval revision 3 says which order can go ahead, and supplier report revision 7 says only part of it arrived. If revision 8 confirms the rest has arrived, change the delivery sentence and its source. The approval sentence still uses revision 3.

When returning to the task, reopen the source references and check whether they still answer today's question. The old bundle explains what the agent knew then; it cannot keep itself current as the order progresses.

<a id="decide-what-an-old-report-can-still-support"></a>

## Decide what an old report can still support

Yesterday's report can support “the supplier reported a partial delivery yesterday,” if historical use is still permitted. It cannot establish that delivery remains partial today. Importing it again changes neither its observation date nor how long it is valid.

**Important**

**Wait for the evidence the task requires.** If the update needs today's delivery position and no permitted source supplies it, pause the work that depends on that position, including drafting. You could instead prepare an explicitly historical account. Calling an unsupported current account a draft does not resolve the missing evidence.

Optional context is different: the owner's policy may allow work to continue with the gap made clear. More room in the answer can help with omitted detail, but cannot make an old observation current.

<a id="keep-unaffected-work-when-a-premise-changes"></a>

## Keep unaffected work when a premise changes

One agent may be drafting while another updates a source. Ask which revision the draft used, what changed and which conclusion depends on it. In this example, the approval and the rest of the draft may remain useful while the delivery claim needs revision.

Scope's semantic-transaction research asks how to identify that affected reasoning without restarting unrelated work. [When an agent's context changes underneath it](https://rawthoughts.in/collections/systems/context-that-helps-the-work/when-context-changes/) develops the proposed approach.

<a id="a-correction-is-not-permission-to-keep-another-copy"></a>

## Correct or withdraw a source

Suppose the supplier corrects the report: the equipment was dispatched, not delivered. Obtain the correction as a new revision, refresh the context and change the delivery claim. Editing only the agent's summary would leave the incorrect report available for the next request.

To withdraw the report, its owner must explicitly identify it for removal. Simply leaving it out of an export is not enough: an interrupted export should not erase valid records.

Revoking access stops later use. Deletion also removes source-derived material under the applicable policy, including summaries, embeddings and learned links. Earlier lawful use does not permit keeping those copies indefinitely.

**Caution**

**Deletion can make an old answer impossible to reconstruct.** Its history should explain which evidence is no longer available, rather than promise a replay without that evidence.

The implementation guide explains [how imports distinguish omission from removal](https://docs.rawthoughts.in/scope/concepts#owners-hand-scope-snapshots-scope-never-reads-a-source) and [how a request handles invalidation](https://docs.rawthoughts.in/scope/concepts#every-request-reads-one-frozen-snapshot). The [order example](https://rawthoughts.in/scope/context-for-a-task/) shows what the corrected update must preserve.


Reading path: [Scope](https://rawthoughts.in/scope/) > [Keep a task current](https://rawthoughts.in/scope/keep-context-current/)

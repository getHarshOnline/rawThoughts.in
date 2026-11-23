Title: Unknown effects and interrupted work

[Read HTML](https://rawthoughts.in/collections/practice/unknown-effects-and-interrupted-work/)

Author: Harsh Joshi

<a id="unknown-effects-and-interrupted-work"></a>

# Unknown effects and interrupted work

A request to create a ticket leaves the caller, and the connection fails before the reply arrives. Somewhere on the other side, the ticket may already exist. The caller sees an error; the provider may have completed the work. What should happen next?

A retry feels like the natural repair because it makes the interface move again. But a new request can create a second ticket while leaving the first unexplained. Before trying again, the caller needs to find out whether the provider created the first ticket, or keep that question open if it cannot find out.

A log saying "timeout" tells us what happened to the connection, not what happened to the ticket. The same uncertainty appears in a payment, a deployment or a booking, though duplication has different consequences in each. Recovery therefore begins with the original request and the provider's state, rather than a fresh attempt whose apparent success could hide both effects.

<a id="an-identity-helps-only-if-the-provider-honours-it"></a>

## An identity helps only if the provider honours it

A stable request identity can let a provider recognise repeated delivery of the same request, under a contract stating what is deduplicated, for how long and in which scope. Where the outcome remains ambiguous, a read-only lookup of that original request can turn the caller's uncertainty into a useful observation. It may confirm the effect, establish that it was not applied or leave the case open for another form of reconciliation.

Suppose the caller records request `create-42` before sending it. The provider creates ticket `T-19`, but the reply is lost. Reading back `create-42` can reveal `T-19` if the provider supports that lookup. The useful next step is now to inspect that ticket, not to create `T-20`. If lookup is unavailable or inconclusive, the caller still has an unresolved request; a fresh identifier would conceal rather than settle it.

Give this fictional provider a more precise contract: it retains a create request's deduplication record for twenty-four hours, within the same account, and requires the same semantic body for a repeated key. Its ticket index is eventually updated. Those stipulations produce three different recovery observations:

| Observation about `create-42` | What it establishes | Where that leaves the work |
| --- | --- | --- |
| Authoritative request lookup returns `T-19` with the matching account and body | The original creation occurred | Inspect that ticket and continue from the observed result |
| An early search returns no ticket while the index may still be behind | The search found nothing yet | Creation remains unknown; preserve the original request and seek a stronger observation |
| The deduplication window expires before the result is resolved | The provider no longer promises to recognise the key | Creation remains unknown; a resubmission could now create another ticket |

**Caution**

**An expired key can allow a duplicate.** The third row is particularly easy to misread. Expiry removes a recovery guarantee; it does not undo `T-19` or prove it never existed. A retry with the same key can create a second ticket after the provider forgets the first request. Changing accounts can lose the guarantee even earlier. The recovery record therefore needs the account, original request and body, the provider's promised horizon and the observation that was actually obtained.

[Pale’s](https://rawthoughts.in/pale/) effect path records the intention to dispatch before calling the provider. If the reply is lost, it keeps the outcome unresolved while the owner’s read-only check investigates what happened within its allowed scope and deadline. An inconclusive lookup leaves the case open. Evidence that the effect was not applied can support another course. A further change must stay within the owner’s existing permission or receive a new decision; changing the target or business action is not merely repairing the connection. Pale’s records for effects and reconciliation exist, but this complete path has not yet been proved against a real provider.

<a id="recovery-is-still-work"></a>

## Recovery is still work

An unresolved effect needs an accountable place to remain open. Ending a session, cancelling a task or expiring a timeout does not make the external consequence disappear. Someone must own the next observation and any decision to accept, compensate or restore the provider's state. Compensation is itself another consequential action. It can require new authority, introduce a new failure and fail to restore every consequence of the first action. Calling it rollback does not make it harmless.

<a id="a-recovery-record-is-not-accepted-completion"></a>

## A recovery record is not accepted completion

Confirming that the ticket exists resolves the question of whether the create effect happened. It does not establish that the ticket is correct or that the broader workflow has achieved its purpose. [Delivery and acceptance](https://rawthoughts.in/collections/practice/two-meanings-of-done/) remain separate after reconciliation.

[Pale's design](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/) gives an unknown effect a durable place in the work still owed. The same obligation exists in a manual process. A person following up an uncertain ticket needs to know which request to investigate and what observation would settle it. Reliable recovery preserves that unfinished question across the interruption.


Reading path: [Practice](https://rawthoughts.in/collections/practice/) > [Unknown effects and interrupted work](https://rawthoughts.in/collections/practice/unknown-effects-and-interrupted-work/)

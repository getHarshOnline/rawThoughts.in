Title: Records, context and decisions

[Read HTML](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/records-and-context/)

Author: Harsh Joshi

<a id="records-context-and-decisions"></a>

# Records, context and decisions

An equipment purchase can be approved and partly delivered while the person waiting for it still cannot do their work. A short summary saying "approved and delivered" is tempting because it gives the workflow a clean ending. It also loses the position from which somebody needs to resume.

[Pale](https://rawthoughts.in/pale/) preserves that position across applications. The conversation explains the need, an approval establishes a permitted purchase, and the supplier records what arrived. Context makes those records usable together. The interesting problem is giving the person a coherent account while letting each claim remain answerable to the source that actually establishes it.

<a id="a-copy-is-not-the-authority"></a>

## A copy is not the authority

An index or cache makes a source easier to reach. It does not replace the source's current state or the qualifications attached to it. A contract, draft, message and runtime observation can concern the same work while establishing different facts. Context therefore needs more than relevant text. The task needs to know which source it came from, whether the revision still applies and whether this caller may use it for this purpose. A plausible answer assembled from the wrong relationship's records is still wrong.

In the hypothetical purchase, the connected account can preserve these claims separately:

| Claim | Record establishing it | Connection that lets the work continue |
| --- | --- | --- |
| Equipment is needed | Original request | Explains the comparison task |
| A comparison was supplied | Delivered comparison and receipt | Gives the approver a particular artifact to review |
| A purchase within agreed limits was approved | Approval record | Identifies which proposed purchase may proceed |
| Some items arrived | Supplier's delivery observation | Refers to the approved order and the items actually delivered |
| The intended work remains blocked | Consumer's usability account | Identifies the remaining need rather than contradicting arrival |

The context is the connected reading of these records. If the supplier corrects its item count, that correction changes the delivery claim, not the earlier approval. Pale calls this connected history its genealogy: which comparison was reviewed, which purchase it supported and which observation now explains the remaining work.

<a id="three-kinds-of-connection"></a>

## Three kinds of connection

Suppose the purchase conversation contains a reply attaching the comparison. Later, a person turns the request into a work item, and a context service suggests that a separate maintenance note concerns the same equipment. Those connections look similar in a graph, but they would answer different queries.

| Connection | What establishes it | A question it can answer |
| --- | --- | --- |
| Reply to the original message | Communication provider's native metadata | Which exchange did this attachment answer? |
| Conversation converted into work | Conversion that passed the permission and validity checks, plus the destination's work record | Which responsibility was actually created from the exchange? |
| Maintenance note may continue the topic | An inferred semantic relation with its evidence and uncertainty | What related material might help someone investigate? |

For “what work was created?”, the second connection is decisive. The reply can lead to the supplied comparison, but cannot establish that the recipient created a responsibility. The maintenance note may be useful context, but cannot silently become an approved task dependency. A question about the conversation's structure instead follows the provider's reply link. Similar wording in two messages does not establish that one answered the other. The three kinds of connection can live in the same account without acquiring each other's authority.

![A purchase request connects to a reply, a conversion into work and a possibly related maintenance note.](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/records-and-context/three-kinds-of-connection.svg)

The dashed connection suggests something to investigate. The solid connections carry a reply and an accepted conversion into work, each backed by its own record.

Pale's design also keeps progress as several positions rather than one synced flag. In this example, the comparison reference might be journalled and delivered while review is pending; a supplier observation might be current while the consumer still cannot use the equipment. The operator needs to see the incomplete review and unresolved usability separately.

<a id="permission-is-not-a-preference"></a>

## Permission is not a preference

A system may learn that someone often chooses a particular action. That pattern can support a recommendation; it cannot become consent, a signature or authority to act for another person. Likewise, possession of a document does not grant publication rights. In the purchasing example, a person who prepared three earlier comparisons may be a sensible person to ask again. Their history does not establish that they accepted this task or can authorise its purchase. A convenient default becomes dangerous when it silently turns repeated behaviour into standing permission.

<a id="evidence-should-explain-the-consequence"></a>

## Evidence should explain the consequence

A journal can record what was requested and observed. The connected history can explain which request and evidence led to a later result. Neither proves that the external provider behaved correctly or that the consumer accepted the work. Those facts require their own observations and decisions. Keeping the request, the checks that permitted its transition and the resulting record together lets an operator inspect the particular link that failed, rather than reconstruct a story from nearby messages.

**Note**

**Even a recorded consequence path is not, by itself, a scientific identification of causation.** It can show that a request accepted by Pale led through a particular execution path to an observed result. Establishing what would have happened without the request is a different question.

<a id="acknowledgement-closes-only-delivery"></a>

## Acknowledgement closes only delivery

Suppose the purchasing system receives a reference to the completed comparison and acknowledges it. That receipt says the reference arrived. It does not say the comparison was reviewed, accepted or acted upon. The account therefore needs separate positions for receipt, required judgment and the consequence owed by the owner. One completed position must not hide another that is pending. Nor should one pending consumer make a different consumer's successful receipt look incomplete.

This is more useful than a single “last synced” time. A recent timestamp can coexist with a missing range, a stale projection or a response nobody has accepted responsibility for supplying. The history should make those gaps inspectable rather than compress them into a green indicator.

<a id="continuity-after-an-interruption"></a>

## Continuity after an interruption

After a crash, replaying committed references can reconstruct a projection. It must not repeat the purchase, infer fresh approval from the old conversation or replace the supplier's current record with an earlier cached copy. The journal preserves continuity; the native owner supplies its own current state. A missing or contradictory result opens reconciliation rather than becoming permission to try the action again. [An uncertain effect](https://rawthoughts.in/collections/practice/unknown-effects-and-interrupted-work/) needs independent inspection, not a more confident summary.

A person returning to the purchasing workflow should be able to find the comparison, distinguish its receipt from its acceptance and see which supplier observation is still owed. Continuity means recovering that position in the work, with each fact still answerable to its owner. The record becomes useful because it explains what to inspect next, rather than making a summary look complete.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Making a working world intelligible](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/) > [Records, context and decisions](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/records-and-context/)

Previous in journey: [How Pale fits together](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/)

Next in journey: [The structure a responsibility needs](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/starting-with-the-duty/)


Source code for [Pale](https://github.com/getHarshOnline/pale) is credited to [Harsh Joshi](https://getharsh.in/about/).

Title: Choosing an API means reading its contract

[Read HTML](https://rawthoughts.in/blog/choosing-an-api/)

Author: Harsh Joshi

<a id="choosing-an-api-means-reading-its-contract"></a>

# Choosing an API means reading its contract

A developer looking for an API usually has a task in mind, not a provider name. An application needs to establish where a parcel can go, reconcile a payment or receive an event when some work finishes. Could a discovery assistant find the relevant services and show which parts of their contracts matter to that task? It would save us reading unrelated documentation, and might catch a constraint before we built around the wrong service.

<a id="a-plausible-match-is-the-beginning-of-the-comparison"></a>

## A plausible match is the beginning of the comparison

Suppose an application needs to check whether a delivery address can be served. A general address-search API, an address-validation API and a logistics provider's serviceability API can all look relevant. They may answer different questions. Finding a place, deciding that an address is well formed and deciding that a particular delivery service will accept it are not equivalent capabilities.

The comparison becomes useful when it explains what each candidate actually establishes. An address that exists may still fall outside a courier's delivery area; a courier may accept that area while requiring a different pickup arrangement. Familiar words such as "availability" and "completion" conceal these distinctions. Ranking by similarity alone can put the most fluently described service first while leaving the application's real question unanswered.

For this imagined integration, the comparison might look like this:

| Candidate capability | Inputs it needs | Answer it can supply | What the application still needs |
| --- | --- | --- | --- |
| Place search | Address text | A candidate place and coordinates | Whether the chosen courier carries this parcel there |
| Address validation | Structured address | Address components accepted under its rules | Courier coverage, pickup and parcel constraints |
| Courier serviceability | Origin, destination and parcel details, under the relevant account | Available services under that courier's contract | Quote validity, booking permission and final acceptance |

The third candidate is closest to the question. Even then, an account-specific exception could matter more than its advertised geographic coverage. That is the passage to retrieve next. The table has narrowed the reading instead of pretending to finish it.

A capability description can preserve those dependencies without pretending every provider has one schema. In this hypothetical case it would carry “serviceability for this account”, the required origin, destination and parcel details, the source passage defining the answer, and the conditions still needed before booking. A returned `available: true` is ambiguous without that account and parcel context. It might mean a service exists for the supplied inputs, not that capacity has been reserved, a price has been fixed or the shipment has been accepted.

<a id="the-schema-is-only-part-of-the-contract"></a>

## The schema is only part of the contract

The developer needs the shapes of requests and responses. They also need authentication, permissions, quotas, errors, applicable commercial terms and the conditions under which data may be sent or retained. Some of those conditions can change while the response schema stays the same. A compatibility check that compares only endpoint shapes can therefore miss a material change in the integration. Conversely, a documentation edit may clarify prose without changing behaviour. Treating every changed byte as a breaking change is as unhelpful as treating identical schemas as identical contracts.

The comparison needs evidence tied to its source: which provider document, which version or observation, and which part of the application it affects. An announcement feed says that something changed. A useful explanation says what that change would mean for the use in front of us.

Suppose the imagined provider keeps the same response shape but changes its parcel-weight limit from 20 to 15 kilograms. A cached comparison can still parse correctly and recommend the wrong service for an 18-kilogram parcel. A useful version comparison flags the affected capability and input condition, retains the earlier source for interpreting older decisions, and makes the old answer unavailable as evidence for the new limit. A changed limit matters to this application; an unrelated wording correction need not trigger the same response.

<a id="a-common-comparison-with-native-behaviour-intact"></a>

## A common comparison, with native behaviour intact

A common comparison can describe the outcome, required inputs, limits and evidence across different services. It should not imply that request-response interfaces, queries and event subscriptions have the same operational behaviour. The integration still needs its native contract. An event may arrive later or more than once. A request may return a response without completing the business operation. A documented capability may require a plan or permission the application does not have. A tidy capability table can help select the next read; it cannot replace that read.

<a id="a-local-cache-needs-an-honest-horizon"></a>

## A local cache needs an honest horizon

Keeping selected documentation locally can reduce repeated retrieval and support offline work. It also creates a horizon: the cache cannot know about a change it has not received. The answer needs to make that boundary visible rather than calling itself current because it is available. A saved copy can identify the exact words used in an earlier decision; it cannot establish that the provider still follows them. Matching a file’s hash establishes that the bytes match, not that two differently described services mean the same thing.

**Caution**

**A cache can disclose more than it should.** Public access is not automatically permission to redistribute a documentation corpus. Internal specifications stay with the audience and use they were written for. Search analytics can reveal the work a team is considering even when no secret is present in the indexed text.

A selected, versioned subset can still be valuable. The developer can inspect the original passage beside the comparison, reuse it offline within its permitted audience and see when a material premise needs checking again. The cache earns its place by making that evidence easier to work with, rather than by presenting an unobserved provider as current.

<a id="recommendation-should-stop-before-the-effect"></a>

## Recommendation should stop before the effect

Producing an example request or a testing collection can cross from explanation towards execution. The assistant must still know whether the caller may disclose the inputs, use the credential and perform the effect. Discovery establishes none of those permissions. That connects this small integration problem to larger questions in [Scope](https://rawthoughts.in/scope/) and [Counsel](https://rawthoughts.in/counsel/): giving an agent useful understanding of its setting, then applying semantic judgment where the available alternatives still need interpretation. Relevant evidence can support a recommendation without widening the task or giving the recommender control of the action. Neither product is the API-discovery assistant imagined here; each has its own job.

<a id="a-better-integration-decision"></a>

## A better integration decision

The useful test is whether a source-grounded comparison reduces wrong integrations, missed constraints or unnecessary investigation for a defined set of tasks. It needs a competent manual baseline and examples where abstaining is the right answer. A large catalogue or a fluent generated explanation cannot settle that test.

That gives the assistant a concrete ambition. For a serviceability task it might eliminate an address-search API, explain why a courier API needs an account-specific agreement and leave two suitable contracts for a developer to examine. The value lies in the wrong turn avoided and the constraint understood: the developer can now decide how to answer the application's question, rather than merely which endpoint resembles its words.

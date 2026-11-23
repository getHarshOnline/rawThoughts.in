Title: Models, memory and the work between them

[Read HTML](https://rawthoughts.in/rawfish/configure-the-prototype/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="models-memory-and-the-work-between-them"></a>

# Models, memory and the work between them

Before a creator sends an announcement through RawFish, they need to know which services will read it and whether those services can do the work. The report model and graph memory have separate connections. Either can fail while the other works, and choosing a local report model leaves the memory clients to be configured separately.

This guide explains those choices in the [reference prototype](https://rawthoughts.in/rawfish/use-the-local-prototype/). For the source setup and service settings, follow the [configuration procedure](https://docs.rawthoughts.in/rawfish/using#configure-the-services).

<a id="which-work-uses-the-model"></a>

## Check the model before starting

The prototype can use native Ollama, another local server with an OpenAI-compatible API, or an external provider. Choose a model that the selected server actually provides and check that it can return the structured responses report generation needs.

Preflight shows the provider, model and address alongside readiness, proposed run size, estimated tokens, latency and available external cost. Use those results to decide whether to proceed or reduce the run. If the price is missing, the cost is unknown. A scale guard can stop an oversized run before launch.

For the creator considering daily clips, the model can help parse the pasted announcement and later write a report. Creator's Simulate step records completion without running agents. Changing the model can change the proposed reactions in the report; it does not test a different simulated conversation.

**Caution**

**An external provider can receive the announcement during parsing or report generation.** Check where each call goes before supplying material.

<a id="memory-has-its-own-dependencies"></a>

## Choose how the graph is kept

Source development can use a deterministic in-process memory mock without Neo4j. Graphiti mode uses Neo4j and its own model, embedding and reranking clients to work with the graph. Those clients have separate settings from the report model. Check each one's recipient and the material it processes and retains.

Match the embedding dimension to its model, and choose the reranking model separately. The prototype's locked Neo4j dependency falls outside Graphiti's declared supported range, so this arrangement remains experimental. The local Docker recipe selects Graphiti; choosing mock memory in a host-side setting does not change that recipe.

A successful report call tells you the report model answered. To check memory, follow its own storage and retrieval path. That is also how you find which part needs attention when the application can write a report but cannot retrieve the records behind it.

<a id="the-caller-changes-what-an-address-means"></a>

## Reach the model from the host and from containers

The local recipe runs Ollama on the host and the application and Neo4j in containers. A probe running on the host can reach Ollama through `localhost`. From a container, that address points back to the container itself.

The recipe therefore keeps separate addresses for the host probes, the Docker application and Graphiti's client. When changing provider or model, update every caller that should use the new service. Otherwise, a request can continue reaching the old local model while another uses the replacement. Check the connection from the application as well as from the host.

When a report fails, follow the error to that call. A model timeout needs a different remedy from an unavailable graph store. Report validation can also reject the text returned by a working model. Identify the failed step before retrying the rehearsal, so that the retry does not merely repeat work that already succeeded.

<a id="what-readiness-does-not-settle"></a>

## Check who can use the application

Authentication can reject an application request before either service is called. In a source build using the prototype's browser key, matching the frontend and backend keys satisfies that key check. The key is delivered in the frontend, however, so it cannot authenticate separate people or isolate their data. The local recipe binds ports to loopback; a shared deployment would need its own access and data boundaries.

Once the services are ready, you can examine the report. Keep the scenario, model and configuration with it, then use [Read the findings](https://rawthoughts.in/rawfish/read-the-findings/) to distinguish a statement drawn from the announcement from a proposed reaction to it. Readiness tells you that the chosen services can be reached; the audience's response still needs investigation.


Reading path: [RawFish](https://rawthoughts.in/rawfish/) > [Models, memory and the work between them](https://rawthoughts.in/rawfish/configure-the-prototype/)

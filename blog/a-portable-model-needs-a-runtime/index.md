Title: A portable model needs a runtime

[Read HTML](https://rawthoughts.in/blog/a-portable-model-needs-a-runtime/)

Author: Harsh Joshi

<a id="a-portable-model-needs-a-runtime"></a>

# A portable model needs a runtime

An application sends a request through a familiar API and receives text. Swapping the server appears easy until the same request loses a required output constraint, handles its images differently or takes too long to finish. The envelope travelled. The useful behaviour did not necessarily travel with it.

Portability interests me because it can make a system less dependent on one implementation without forcing the application to forget what it needs. The difficulty is choosing a stable boundary that carries meaning, not just a common spelling for incompatible operations. Model files, loading formats, request protocols and workload behaviour provide different kinds of portability. A successful conversion at one layer opens the next question rather than answering all of them.

<a id="the-application-asks-for-a-capability"></a>

## The application asks for a capability

Consider an illustrative document assistant. It needs to read a permitted document, extract named fields into a specified structure, and return the relevant passages for review. A second application needs a vector representation for comparison. Both might use related model architectures, but the requested capabilities differ. Returning plausible prose cannot substitute for a valid extraction, and generating a paragraph cannot substitute for a vector with the dimensions and interpretation its consumer expects.

[vLLM's supported-model documentation](https://docs.vllm.ai/en/latest/models/supported_models/) distinguishes generative and pooling tasks and describes architecture-specific feature support. That is a useful model for a service boundary: identify the task and required features before selecting the execution path. The application can remain independent of many implementation details while still declaring the input types, output meaning and constraints on which its own work depends.

A capability declaration also needs failure meaning. If structured output is unavailable, silently returning unstructured text gives the next component a different job. It may now need to interpret and repair what it expected to validate. An explicit unsupported capability is more useful than success on an easier task, because the caller can select another path without confusing adaptation with fulfilment.

For the document assistant, the stable requirement could be “return these five fields, evidence passages and an explicit missing-value representation.” The deployment can then vary behind that requirement:

| Application requirement | Deployment choice | Compatibility question |
| --- | --- | --- |
| Read text and supplied page images | Checkpoint and input preprocessing | Are both input types actually supported? |
| Return five structured fields | Constraint mechanism and output validation | Does failure remain distinguishable from a valid empty field? |
| Cite the admitted source passages | Passage identifiers carried through the adapter | Can each result be traced to the same source text? |
| Finish within the task's time and memory budget | Precision, runtime, device and scheduling | Does the selected request mix fit, not just one example? |

The adapter owns translation between these two vocabularies. A backend-specific setting belongs to the deployment unless the application genuinely depends on its meaning. That leaves room to replace the runtime without silently dropping a field or turning missing evidence into prose.

<a id="state-has-to-fit-the-chosen-path"></a>

## State has to fit the chosen path

Attention-based generation carries keys and values from preceding tokens. Recurrent and hybrid models can carry a different mixture of state. That difference matters to allocation, scheduling, concurrency and recovery, even when the user sees the same request interface. It belongs close to the runtime where that state is managed. [A service carrying many requests](https://rawthoughts.in/blog/serving-tokens-is-a-service-problem/) needs the actual memory shape, not merely the size of the model weights.

Suppose two hypothetical backends accept the same maximum input length. Under one, each additional token substantially increases retained per-request attention state; under the other, a recurrent component has a different growth pattern. The application need not manage those internals directly. But the platform cannot assume that a scheduling policy derived for one has the same capacity consequences on the other. Portability at the task boundary allows a different implementation precisely because its resource management can remain different.

Compiled artifacts introduce another boundary. [NVIDIA's TensorRT support matrix](https://docs.nvidia.com/deeplearning/tensorrt/latest/getting-started/support-matrix.html) documents platform, version and hardware-compatibility conditions for serialized engines. A file being portable in storage does not make its executable representation portable to an arbitrary target. The selected artifact, runtime and hardware form a configuration whose compatibility has to be established together.

<a id="an-adapter-translates-meaning"></a>

## An adapter translates meaning

A narrow adapter can translate request fields, preserve identifiers and map failure results. It may also need to describe the differences it cannot translate. An embedding model's output dimension, a tokenizer's treatment of the input, a constraint mechanism or a model-specific preprocessing path can be material to the consumer. Concealing all variation behind one generic success response makes the interface simple by making the application uninformed.

The opposite extreme is exposing every runtime option as a common requirement. That ties callers to the first engine's vocabulary and turns each replacement into an application migration. A useful separation keeps the application's requirements stable while a deployment profile supplies the checkpoint, preprocessing, precision, runtime and hardware decisions needed to fulfil them. Extensions can expose particular capabilities explicitly instead of pretending that every backend implements the same maximal feature set.

<a id="replacement-changes-an-experiment"></a>

## Replacement changes an experiment

Imagine two hypothetical extraction configurations. A handles one hundred prepared cases and returns ninety-five valid outputs. B returns ninety-seven, but takes twice as long and misses a rare field that A consistently finds. Choosing B cannot be justified by the headline total alone if that field determines the downstream decision. Equally, retaining A solely because it is incumbent misses a possible improvement. The test needs the errors and resource costs that matter to the actual task.

The comparison binds model revision, runtime, precision, preprocessing, workload and evaluator. It can then examine a replacement against the same required capability. A transport conformance test establishes that requests and responses cross the interface; task evaluation establishes whether the result remains useful. [A narrow judgement service](https://rawthoughts.in/collections/systems/learning-from-a-recommendation/a-recommendation-is-not-a-mandate/) makes this concrete by selecting a configuration for the questions it will face rather than for a general prestige ranking.

Backend neutrality is therefore a constructive constraint. It gives the application a stable way to say what it needs and the implementation room to improve how that work happens. The boundary is successful when a replacement can be evaluated and adopted without either rewriting the whole application or quietly changing the job it performs.

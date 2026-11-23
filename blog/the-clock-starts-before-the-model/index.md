Title: The clock starts before the model

[Read HTML](https://rawthoughts.in/blog/the-clock-starts-before-the-model/)

Author: Harsh Joshi

<a id="the-clock-starts-before-the-model"></a>

# The clock starts before the model

A speech model can process audio faster than real time and still make a person wait too long. The processing rate says whether the system can keep up. It does not say when enough audio arrives, when the recogniser commits its answer or when the interface responds.

Imagine an on-device voice interface that must follow a short command through background noise and language switching. Its promise is a person speaking naturally and receiving a usable response without depending on the cloud. That promise connects the listening window, the model and the action that follows the transcript. The examples below ask what a complete measurement would have to include.

<a id="where-the-clock-begins"></a>

## Where the clock begins

Suppose a hypothetical recogniser collects 320 milliseconds of audio before processing a chunk. Its computation takes 150 milliseconds. Those numbers describe different intervals. Measuring only the second makes the recogniser look faster than the experience that includes waiting for the first. Continuous processing can overlap collection and computation after the pipeline starts. That does not erase the initial wait or a final decision to hold an unstable transcript until more speech arrives. A timer starting at the beginning of a command will also include the command's duration; a timer starting at the end asks a different question.

These stipulated timings expose different interface questions. Time to first partial text tells us when a person begins to see recognition; time from the end of speech to a committed response tells us when they can expect the command to proceed. The design may need both. A single “latency” figure becomes useful only when the events it measures are clear.

| Interval in the illustrative first chunk | Starts | Ends | Duration |
| --- | --- | --- | --: |
| Audio collection | First sample | Complete chunk available | 320 ms |
| Chunk computation | Complete chunk available | Chunk result available | 150 ms |
| First-chunk path without overlap | First sample | Chunk result available | 470 ms |

**Note**

**This is a timing sketch, not a benchmark or the final command-response time.** In a pipeline, later collection and computation may overlap. Endpoint detection, lookahead and committing the transcript add their own intervals. They need positions on the same clock rather than disappearing into an average processing rate.

<a id="a-model-file-is-only-part-of-memory"></a>

## A model file is only part of memory

Now suppose a quantised model's weights fit on the device. The runtime still needs activations, audio buffers, decoder state, caches and workspace. Other services need memory too. The useful quantity is peak demand under the intended operation, not the size of the downloaded file.

Compression can also move the cost instead of removing it. If the accelerator cannot execute an operator, computation may fall back to the CPU. Transfers and conversions can consume time even when the nominal arithmetic count falls. The deployed graph and its actual placement matter more than a precision label in a proposal. For example, [ONNX Runtime’s execution providers](https://onnxruntime.ai/docs/execution-providers/) select the nodes or subgraphs a backend can execute. The model’s presence in one file does not mean every operation runs on one processor.

That is especially consequential in a streaming encoder. A convolution may map neatly to the accelerator while normalisation or another unsupported operation returns to the CPU. Repeating that crossing through several layers can spend the latency saved by compressing the weights. A useful profile separates accelerator work, CPU fallback and transfer time for the same chunk. It can then test whether changing an operator, reducing depth or choosing a different streaming architecture helps the complete path.

A cold start, a long utterance and several active streams stress different parts of that budget. The intended use determines which conditions matter: a brief-command interface needs a representative command test, while a system carrying continuous streams has another memory and scheduling problem. A useful measurement follows the operation being promised.

<a id="the-language-task-has-to-stay-the-same"></a>

## The language task has to stay the same

A command can cross languages inside a sentence. A recogniser tested separately on clean English and Hindi has not thereby been tested on that switch, particularly when names and place names carry the meaning of the request.

Consider “Rajesh ko call karo.” A transcript might preserve most ordinary words while getting the person's name wrong. Average word error is useful, but the contact error matters differently to the intended task. That does not justify abandoning the transcript metric. It means pairing it with the consequences the interface is supposed to handle.

Evaluation also needs consistent transcription and tokenisation rules. Apparent differences can reflect spelling or segmentation conventions rather than recognition alone. Comparing different systems on different audio cannot establish a winner for the same on-device task.

The strongest test names its audio set, streaming policy and target device. It examines noise, switching and regional variation together, with enough detail to see which cases became worse after compression. A mean can improve while a particular group or command becomes harder to recognise.

<a id="one-configuration-has-to-carry-the-whole-task"></a>

## One configuration has to carry the whole task

Imagine one configuration meets the memory limit but loses important names, a second improves recognition but misses the response window, and a third runs quickly only on clean audio. Each result teaches something. None establishes a configuration that meets all the obligations together. An architecture proposal therefore needs a joint operating test. The report should identify the exact model, precision, compiler, device, stream and data conditions, then show latency, memory and recognition quality for that same configuration. Sustained behaviour matters when heat or accumulated state can change performance after the first successful command.

Even that result would not establish safe action. A transcript is a candidate interpretation of speech. Choosing a contact, placing a call and handling ambiguity belong to the surrounding interface, with their own confirmation and failure behaviour.

Published architectures give us concrete choices to examine. [Conformer](https://arxiv.org/abs/2005.08100) combines convolution and attention to model local and wider relationships in audio. [Squeezeformer](https://arxiv.org/abs/2206.00888) revisits that design, reducing sequence-processing work and simplifying parts of the network. Those papers establish particular architecture and benchmark comparisons. Selecting either for this hypothetical interface would still require a streaming policy and a complete measurement on the intended device.

The choice becomes clearer when the same command is carried through each design. Does a simpler encoder reduce CPU fallback enough to compensate for a recognition loss? Does keeping attention at higher precision preserve a switched-language name while exhausting the memory margin? Does a model that recognises the whole utterance well need too much future audio to answer at the intended moment? Each choice changes another part of the budget. Borrowing a small footprint from one model, an accuracy score from another and a speed figure from another chip would conceal that conflict rather than resolve it.

The first useful comparison would therefore be a small joint experiment: the same noisy, code-switched commands, an explicit chunk and endpoint policy, each candidate's complete runtime, and its own target device. It would report the command's name and intent errors alongside peak memory and response intervals. That comparison could reject an architecture before expensive training, or show exactly which part deserves further work.

<a id="an-experiment-that-can-change-the-design"></a>

## An experiment that can change the design

Comparing architectures under those same conditions lets the experiment change the design. A smaller model may leave room for a more useful decoder; another streaming policy may shorten the wait without changing the model. The winning configuration is the one that carries the command through the whole interface, rather than winning one isolated metric.

What makes the problem worth exploring is that the interface can improve at several points. Earlier useful partial recognition can shorten perceived waiting; a suitable streaming policy can limit accumulated state; a confirmation step can recover from a misheard name before the wrong call begins. The model contributes to all of this, but the person's experience begins before it runs and continues after it returns.

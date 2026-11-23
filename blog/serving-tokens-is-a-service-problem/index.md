Title: Serving tokens is a service problem

[Read HTML](https://rawthoughts.in/blog/serving-tokens-is-a-service-problem/)

Author: Harsh Joshi

<a id="serving-tokens-is-a-service-problem"></a>

# Serving tokens is a service problem

Twenty requests reach a model at once. Another twenty arrive evenly over the same period. The machine can finish the same amount of work in both cases, yet the people waiting experience very different services.

That difference is where inference becomes interesting to me as an operating problem. Learned parameters and fast token generation are necessary ingredients, but the service also has an arrival pattern, a queue, live memory and people expecting a result. A steady base load can justify one capacity arrangement while unpredictable peaks justify another. Long documents, short conversational turns and overnight processing need different schedules even when they use the same model. The economics follows that larger object: what the held-ready capacity can deliver to the work arriving.

<a id="the-same-throughput-can-feel-very-different"></a>

## The same throughput can feel very different

Imagine a deliberately simple service with one worker. Every request takes exactly 100 milliseconds, and there is no batching or overhead. The arrivals begin at time zero. Only their spacing changes.

| Arrival pattern for twenty requests | First result | Last result | Mean arrival-to-completion time | Work completed over two seconds |
| --- | --: | --: | --: | --: |
| All arrive at time zero | 0.1 s | 2.0 s | 1.05 s | 20 requests |
| One arrives every 0.1 s | 0.1 s | 2.0 s | 0.10 s | 20 requests |

For the burst, completion times are 0.1, 0.2, …, 2.0 seconds, whose average is 1.05 seconds. In the spaced case each request arrives just as the worker becomes free. Throughput is ten requests per second in both cases; the 10.5-fold difference in mean response time lives in the queue.

A real inference engine is more complicated, but this example isolates an important point. The arrival process and the queue belong in the performance claim. A throughput figure cannot recover them after they have been discarded.

Rejecting some requests can protect the latency of the rest. That can be a deliberate overload response, but it changes how much attempted demand the service fulfils. A chart of successful requests alone hides the trade.

<a id="an-answer-has-more-than-one-clock"></a>

## An answer has more than one clock

Time to first token is the wait before output begins. Time between generated tokens affects the pace of a streamed answer. Total completion time tells a downstream process when the whole result is available. For a conversation, a prompt beginning can make the service more usable. For a process waiting on a complete structured result, the first token may do little to unblock the work. Neither use is wrong. They place value on different points in the same generation process.

Long prompts and long outputs also create different loads. A service processing short questions is not carrying the same work as one reading substantial documents, retaining long contexts and producing extended answers. An average token rate blurs that distinction if it combines input processing and generated output. This is why a benchmark includes a request distribution and an arrival pattern, not just a model name and a device.

<a id="live-memory-changes-the-number-of-users-a-machine-can-carry"></a>

## Live memory changes the number of users a machine can carry

Autoregressive attention models retain earlier keys and values for each active request. The cache grows as sequences grow, and a serving system has to manage many such sequences together. The [PagedAttention paper](https://arxiv.org/abs/2309.06180) identifies wasted space from fragmentation and duplicated cache state as limits on batching. Its block-based memory management makes allocation and sharing more flexible, allowing useful serving capacity to change without increasing the model's parameter count or adding another accelerator. How much that helps depends on shared prefixes, sequence lengths and concurrency; the paper's measured speedups describe its evaluated workloads and baselines.

A longer-context feature therefore has a service cost as well as a model meaning. Fitting one request establishes that the state can fit. Carrying many such requests while retaining a latency target is a different operating condition.

<a id="batching-trades-work-efficiency-against-waiting"></a>

## Batching trades work efficiency against waiting

Sharing computation across requests can improve hardware use. Waiting for a group can add delay. A long request can occupy resources after shorter requests would otherwise be ready to leave. Continuous batching changes the schedule by bringing new work into the active batch as other requests finish, instead of making every request wait for one fixed group. But scheduling cannot make demand, memory and quality disappear. A policy that is useful under one mix can behave differently when context lengths or arrival bursts change.

The resource model can change too. An attention cache, recurrent state and a hybrid architecture need not have the same memory shape. A serving interface can hide those differences from the application only where it genuinely supports [the required behaviour through its selected runtime](https://rawthoughts.in/blog/a-portable-model-needs-a-runtime/). The stable boundary is the task the application can rely on, while the implementation remains free to manage its particular kind of state.

<a id="the-accepted-result-is-the-economic-denominator"></a>

## The accepted result is the economic denominator

Suppose an illustrative service spends 10 currency units carrying one hundred attempted requests. Ninety meet both the quality and latency condition; ten do not. Cost per attempted request is 0.10. Cost per accepted request is about 0.111, before any correction work outside the service.

If a new configuration doubles raw throughput but increases unacceptable results, its economic benefit depends on that trade. A shorter context, lower precision or smaller model can be an excellent choice for one task and a poor choice for another.

The calculation also includes the idle capacity held for bursts, startup, data movement, retries and the application surrounding the model where those costs apply. Owning a steady base load and renting peaks can produce one cost pattern; renting everything can produce another. Neither arrangement eliminates demand uncertainty.

Procurement has to price [the completed work](https://rawthoughts.in/collections/useful-compute/a-gpu-price-is-not-a-job-cost/) those resources can deliver, including the cost of keeping capacity ready between requests. The distinction from training remains important: a training experiment has a result to reach; a service has people continuing to arrive. Its useful capacity is the work it can give those people under the conditions they depend on.

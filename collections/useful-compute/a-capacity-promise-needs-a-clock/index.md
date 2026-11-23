Title: A capacity promise needs a clock

[Read HTML](https://rawthoughts.in/collections/useful-compute/a-capacity-promise-needs-a-clock/)

Author: Harsh Joshi

<a id="a-capacity-promise-needs-a-clock"></a>

# A capacity promise needs a clock

A service can be highly available after a job starts and difficult to plan around before it starts. Uptime describes continuity of an operating service. It does not, on its own, describe whether the buyer can obtain the required allocation at the required time.

This distinction becomes visible when the job needs a cluster. A request is acknowledged, fifteen machines launch, and a sixteenth remains unavailable. For a workload that can use independent smaller groups, the first fifteen may already produce value. For a coordinated sixteen-worker run, the start has not yet arrived. The promise concerns usable capacity, not merely a response from the booking system.

<a id="two-intervals-can-tell-opposite-stories"></a>

## Two intervals can tell opposite stories

Time from request to usable allocation and lateness against a promised start are different measures. A booking made a month ahead can have a month-long request-to-start interval and be exactly punctual. An immediate request can allocate in ten minutes and still miss a window that mattered. Describing the first as slow and the second as fast confuses intentional lead time with lateness.

The required resources also shape the population. A single-device request and a large colocated cluster do not necessarily face the same availability. Pooling their starts can conceal the uncertainty that the coordinated workload is trying to price.

“Usable” adds another boundary. Device visibility, communication, storage access and a representative readiness check can mark different moments. A start measure acquires economic meaning when it refers to the minimum that can actually carry the promised job.

<a id="the-requests-that-never-start-belong-to-the-story"></a>

## The requests that never start belong to the story

Suppose nine illustrative requests each start in ten minutes and one does not start before the observation ends. A report containing only completed starts can truthfully report ten minutes for every observation it retained. It has still omitted a tenth of the attempted demand. The unfinished request has no completed waiting duration yet. Assigning it zero or removing it changes the result. A customer cancellation may also follow an unacceptable delay rather than an unrelated change of plan. Its meaning depends on why it happened.

At a declared thirty-minute cutoff, the same record can say both things plainly:

| Outcome at the cutoff | Requests | Waiting-time observation |
| --- | --: | --- |
| Usable allocation obtained | 9 | Each started after 10 minutes |
| Still waiting | 1 | At least 30 minutes; final wait not observed |

The fulfilled fraction is 9/10 by that cutoff. The completed-start mean is ten minutes. The mean final wait across all ten requests is not known. Those three statements describe the same cohort without substituting the most flattering one for the others.

The operating record is consequently more than a percentile. It includes fulfilled requests, partial starts, failed paths, cancellations and requests still waiting at the cutoff. The proportion fulfilled and the speed of fulfilled starts answer different questions. This matters commercially because an excellent percentile can coexist with a substantial probability of never obtaining the required resource within the useful window.

<a id="the-allocation-has-a-usable-ending"></a>

## The allocation has a usable ending

The other edge of the reservation is easy to overlook. A job needs time to complete, retain its result and leave the resource in a recoverable state.

AWS's current Capacity Blocks documentation says termination begins thirty minutes before the nominal end for instance blocks and sixty minutes before it for UltraServer blocks.<sup><a id="fnref-note-63617061636974792d626c6f636b73"></a>[1](#fn-note-63617061636974792d626c6f636b73)</sup> The booking duration is therefore not identical to the interval in which the customer can continue running.

A workload finishing its last computation just before that boundary may still need to write a checkpoint, transfer output or verify the result. An extension helps only if another allocation is actually available on the required terms.

The ending also changes the value of the beginning. A late start does more than add delay if the reserved end remains fixed: it shortens the usable interval. A job can then fail to finish despite receiving all the promised devices.

<a id="a-credit-prices-one-consequence-not-every-consequence"></a>

## A credit prices one consequence, not every consequence

A service objective and a contractual remedy have different roles. One describes performance being targeted. The other defines what happens under specified conditions when performance is missed. A credit can align incentives and compensate for a charge. It need not compensate for a delayed product launch, lost experiment or downstream commitment. The remaining uncertainty still affects what the buyer can sensibly plan.

That does not make a start promise worthless. It makes its value specific. A predictable interval can support coordinated work that flexible access cannot schedule confidently. A flexible arrangement can be preferable when the workload itself is still changing.

<a id="the-clock-connects-procurement-to-the-experiment"></a>

## The clock connects procurement to the experiment

A reservation may protect a sequence as well as one run. Generating simulation trajectories, training a policy and evaluating its artifact depend on one another. A late start can leave the checkpoint intact while removing the time needed to evaluate it. Independent exploratory variants need not share that protected interval. The booking should follow the actual dependency, not treat every GPU-hour as interchangeable.

A small exploratory allocation, a reproducible environment and a transferable checkpoint can reduce the risk around a later large booking. They cannot make an unobserved queue into a scheduled resource.

The clock brings that uncertainty into [the cost of the finished job](https://rawthoughts.in/collections/useful-compute/a-gpu-price-is-not-a-job-cost/). It distinguishes a billable wait from an unbilled delay, an acknowledgement from a usable cluster, and a long planned lead time from a missed start. Those distinctions give capacity a practical meaning: a resource with a place, configuration and interval in which the intended work can happen.

1. 
   
   <a id="fn-note-63617061636974792d626c6f636b73"></a>
   
   [AWS's Capacity Blocks terms](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-blocks-how.html). [↩](#fnref-note-63617061636974792d626c6f636b73)


## Article notes

<a id="gazette-notes-a-seven-day-robotics-experiment"></a>

## A seven-day robotics experiment

Consider an imagined robotics experiment with seven days available. The team wants to generate trajectories in simulation, train a policy and evaluate it under a fixed set of challenges. Exploratory variants can run beside that core sequence, but the evaluation depends on a particular trained artifact, and training depends on usable trajectories. The reservation protects a chain of work, not seven interchangeable daily GPU quotas.

| Planned interval | Core work | What must survive the transition |
| --- | --- | --- |
| Days 1–3 | Generate the selected simulation trajectories | Scenario settings, simulator revision and saved trajectories |
| Days 3–5 | Train the candidate policy, while the last selected trajectories arrive | Dataset revision, run configuration and recoverable checkpoints |
| Days 5–7 | Evaluate the selected policy on the fixed challenge set | Policy artifact, evaluation conditions and results |

On day three, simulation and training overlap. That works only if the two jobs can share the available resources without delaying the core training run. A burst of exploratory work can use spare or separate capacity. If it competes for the same memory, devices or storage path, the team has to account for it in the protected schedule.

A late start now has a specific consequence. If simulation loses a day and the reservation still ends on day seven, the team must either shorten another phase, obtain an extension or leave the intended comparison unfinished. A saved checkpoint can preserve training progress, but it cannot supply evaluation time that no longer exists. If the variants are independent and their timings remain uncertain, reserving enough capacity for every possible branch can buy mostly idle time.

Continuity here concerns progress, coordination and the promised result. Pausing a simulator does not necessarily change the physics it computes: a simulator that advances its own time and restores its state may resume the same experiment. A wall-clock-coupled or live-input system has a different interruption problem. The reservation choice should follow that actual dependency, rather than a blanket claim that every simulation must run without a pause.



Reading path: [Useful compute](https://rawthoughts.in/collections/useful-compute/) > [A capacity promise needs a clock](https://rawthoughts.in/collections/useful-compute/a-capacity-promise-needs-a-clock/)

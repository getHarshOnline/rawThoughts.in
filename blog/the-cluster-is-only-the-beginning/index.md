Title: The cluster is only the beginning

[Read HTML](https://rawthoughts.in/blog/the-cluster-is-only-the-beginning/)

Author: Harsh Joshi

<a id="the-cluster-is-only-the-beginning"></a>

# The cluster is only the beginning

Sixteen accelerators have been allocated. The status is green. The training team is still waiting: its image cannot reach the dataset, one worker has a different library version, and the checkpoint destination has not been configured. The hardware exists, but the experiment has nowhere coherent to happen.

This imagined scene exposes a product boundary that a capacity catalogue can miss. A developer buys a path through work, not merely possession of devices. The useful path begins before allocation and continues after computation, through preparation, access, observation, retained results and release. Building a GPU service means deciding which parts of that path the platform makes dependable and which choices remain with its user.

<a id="different-journeys-need-different-products"></a>

## Different journeys need different products

An inference service is expected to keep receiving requests. Fine-tuning has a bounded dataset, a base model and an artifact to produce. Distributed training coordinates workers whose collective state matters. Each can use accelerators, but their useful beginnings and endings differ. For inference, an endpoint becoming reachable is only the start of carrying its actual request mix. For training, a healthy group has to agree on the run and eventually preserve a checkpoint that can be resumed or evaluated.

A common allocation interface can support all three without making their readiness identical. Kubernetes illustrates the distinction at a narrower layer: its [GPU scheduling documentation](https://kubernetes.io/docs/tasks/manage-gpus/scheduling-gpus/) describes device plugins, resource declarations and node selection. Those mechanisms make devices available to a workload. They do not supply the application's dataset, determine its experiment or establish that its result met the user's need. The platform's opportunity is to connect these layers into a recognisable journey rather than present every lower-level success as completion.

Consider a hypothetical fine-tuning request. The user supplies an approved dataset reference, a base-model revision, a training configuration and a destination for the resulting adapter. The service resolves the environment and storage, acquires suitable capacity, records the run configuration, exposes progress and retains the artifact. A worker becoming available is one useful milestone. An artifact reaching its destination is another. The evaluation of that artifact answers a further question. Keeping those milestones visible lets the user recover the position of the work when it stops.

The journey exposes a different recovery question at each point:

| Position in this fine-tuning job | Evidence useful to the user | If work stops here |
| --- | --- | --- |
| Environment prepared | Image, dependencies, base-model revision | Repair the environment before consuming the booked run |
| Data reachable | Approved dataset and successful access within its limits | Resolve the access failure without changing the dataset silently |
| Workers joined | Intended group and shared run configuration | Identify the missing or inconsistent worker |
| Run advancing | Progress and retained checkpoints | Resume from declared state or make the restart explicit |
| Adapter retained | Artifact destination and producing configuration | Recover the result independently of the rented machines |
| Resources released | Removed allocations and deliberately retained storage | Investigate resources still accruing cost without destroying the artifact |

This is why a useful status view follows the job, not just the devices. “Data access blocked” and “training failed” lead the user to different next actions even when both leave the accelerators idle.

<a id="responsibility-has-a-shape-above-the-hardware"></a>

## Responsibility has a shape above the hardware

Suppose the provider supplies a functioning machine, the platform selects its operating environment, and the tenant supplies application code. A failed job may begin in any of those places. An interface that reports only “provider error” gives each party an incentive to send the problem elsewhere. A better account connects the failure to the layer that can investigate it: device health, environment construction, dataset access, scheduler admission or the application's own exception.

The exact division depends on the service. Bare metal and a managed container do not hand over the same responsibilities. Neither label settles who patches the operating system, controls network access, gathers usage, removes a volume or preserves a result. Those decisions influence the API, support process and price. They also determine what the platform must observe itself rather than assume from the provider's reply.

Cleanup is a revealing example. Deleting a training allocation can be successful while leaving a paid volume behind. Removing every resource together can destroy a checkpoint that another run needs. The meaningful operation is therefore attached to the lifecycle of the work: release this allocation, retain this artifact and remove these temporary resources. The platform needs resource identities and dependencies precise enough to carry that decision through the provider's actual controls.

<a id="readiness-belongs-to-a-particular-workload"></a>

## Readiness belongs to a particular workload

A provider screen becomes more useful when it begins with the journey's hard dependencies. Can the desired allocation be obtained and released at the required granularity? Can the environment reach the data? Can the needed communication pattern run? What happens to retained state when a machine is replaced? A score may compare eligible offers afterwards, but a high average cannot repair a missing prerequisite.

Imagine two offers. One supplies a single node quickly and can remove workers independently; the other takes longer but supplies the tightly connected group a training run needs. There is no contradiction in choosing the first for an elastic service and the second for a scheduled experiment. A product that pools them into one undifferentiated inventory asks its users to rediscover the workload boundary themselves. A more useful catalogue describes the capabilities through which each offer becomes usable.

The same boundary gives [the start clock](https://rawthoughts.in/collections/useful-compute/a-capacity-promise-needs-a-clock/) a practical meaning. Allocated, reachable and workload-ready are different times. A benchmark that begins only after successful setup can explain execution while hiding most of the user's wait. For procurement, that wait remains part of [the completed job's economics](https://rawthoughts.in/collections/useful-compute/a-gpu-price-is-not-a-job-cost/).

<a id="the-result-should-survive-the-rented-machine"></a>

## The result should survive the rented machine

A compute service becomes more valuable when the user can leave it with the useful work intact. That means more than an export button. An artifact needs enough configuration and provenance to be understood elsewhere, storage needs a deliberate retention policy, and the next environment needs an actual way to consume the result. A checkpoint that restores only on the original shape gives a different freedom from one that supports the intended replacement.

This is where a platform can reduce a developer's burden without pretending to remove the underlying complexity. It can remember the environment, make failure attributable, expose the interval that remains and preserve the result separately from the allocation. The rented cluster then becomes one stage in the experiment rather than the container of its entire history. The product is the dependable passage through those stages.

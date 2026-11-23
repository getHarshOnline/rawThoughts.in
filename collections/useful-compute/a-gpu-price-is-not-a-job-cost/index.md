Title: A GPU price is not a job cost

[Read HTML](https://rawthoughts.in/collections/useful-compute/a-gpu-price-is-not-a-job-cost/)

Author: Harsh Joshi

<a id="a-gpu-price-is-not-a-job-cost"></a>

# A GPU price is not a job cost

The cheaper GPU hour can produce the more expensive job.

Imagine two offers for eight accelerators. Offer A charges 2 currency units per accelerator-hour and needs twenty hours to complete a job. Its accelerator bill is 320. Offer B charges 2.5 and completes the same job in twelve hours. Its bill is 240. These are illustrative offers, not provider measurements. Their purpose is to expose the comparison hidden by the hourly price: the buyer pays for a duration and needs a result. Device name and rate describe only part of that purchase.

<a id="the-job-gives-the-price-its-meaning"></a>

## The job gives the price its meaning

For a training experiment, a usable result can include the required evaluation, configuration and retained checkpoint. For an inference service, it can mean requests meeting quality and latency conditions. For a simulation campaign, it can mean a valid set of completed scenarios. GPU-hours are inputs to those results. They are not equivalent results in their own right.

This is why a faster run can still be a bad comparison if it changes the experiment. Lower precision may reduce cost but alter the quality. Shorter requests can make an inference benchmark look cheap while carrying a different service from the one the buyer needs. A procurement comparison starts to become informative once it refers to equivalent useful work.

The illustrative bills also leave out storage, transfer, supporting instances, licences and engineering effort. A week spent porting to Offer B could reverse its apparent advantage. So could a second run after Offer A loses its progress. The accelerator rate remains real in both cases; it is simply incomplete.

Under the original assumptions, B saves 80 currency units per equivalent job. If a one-time port to B costs 400 of the same units and recurring non-accelerator costs remain equal, five jobs repay the port exactly. The sixth starts to create a net saving:

$$
K_A(n)=320n,\qquad K_B(n)=400+240n,\qquad K_B(n)<K_A(n)\iff n>5.
$$

That calculation deliberately prices the engineering work in the same declared unit. A real comparison should keep the human effort visible before valuing it, and account for maintenance when the port needs repeating. For a one-off experiment, the lower accelerator bill can easily be the dearer path.

<a id="certainty-can-be-purchased-and-wasted"></a>

## Certainty can be purchased and wasted

A team may pay more to know that a connected allocation will be available during an experimental window. That certainty can save coordination time across engineers, data preparation and evaluation. It can also create paid idle time. If the data are not ready, the environment does not work or the experiment changes, the reserved window continues to pass. Flexible capacity transfers some of that scheduling risk back to the availability of the service.

The commercial vocabulary does not settle the trade. AWS distinguishes regional Reserved Instances, which do not reserve capacity, from zonal Reserved Instances, which reserve it in the specified Availability Zone.<sup><a id="fnref-note-6177732d73636f7065"></a>[1](#fn-note-6177732d73636f7065)</sup> A discounted billing commitment and a capacity guarantee are different properties.

Interruptible capacity creates yet another trade. A job that resumes cheaply can use it differently from one whose useful state is expensive to reconstruct. There is no universal ordering of flexible, committed and interruptible offers independent of the workload.

<a id="a-delay-can-be-costly-without-being-billed"></a>

## A delay can be costly without being billed

When a team waits for capacity, no accelerator invoice may accrue. Yet a launch can slip, a decision can remain blocked or people can spend time adapting to equipment that was not their first choice. Those are economic costs, but labelling them GPU charges confuses two different losses. A refund can reverse a bill. It cannot move a missed deadline back into the past.

The distinction also changes a supplier's incentives. A provider can reduce the rental price without improving the customer's waiting time. A provider with a higher rate can create value by delivering [a predictable start](https://rawthoughts.in/collections/useful-compute/a-capacity-promise-needs-a-clock/). Measuring that certainty means following the usable allocation against the interval in which the customer's work matters.

<a id="an-experiment-campaign-contains-unsuccessful-work"></a>

## An experiment campaign contains unsuccessful work

A useful checkpoint protects only the progress it actually retains. An interruption can add work since the checkpoint, restore time, transfer and a wait for replacement capacity.

Some failures also occur without an outage. An experiment can finish and teach the team that the chosen configuration does not work. That attempt belongs to the economics of the campaign, even when it is not a usable final model. Dividing the campaign's spend by only the successful run's work removes the cost of learning how to get there. Conversely, calling every unsuccessful experiment wasted expenditure misses the value of the information it produced. The accounting question and the scientific value are related but not identical.

The result is a fuller job-cost picture: useful outputs, unsuccessful attempts, supporting resources and paid idle time over the period that produced them.

<a id="the-supplier-sees-a-different-denominator"></a>

## The supplier sees a different denominator

A customer may want to reduce the hours required for a result. A supplier may want to increase the fraction of installed hours that are sold. Both can improve their economics, but they describe different uses of the same machine. An occupied fleet can carry inefficient workloads. An efficient customer run can take place in a mostly empty fleet. Model efficiency and fleet occupancy therefore cannot substitute for one another.

[Installed capacity between jobs](https://rawthoughts.in/blog/the-cost-of-an-idle-fleet/) remains a cost to the supplier even when no customer is using it. The buyer's question stays with the finished job: what arrangement produces the result at a credible total cost, within the time that makes it useful? Once that is the object of the purchase, the hourly price becomes one term in an economic argument rather than the argument itself.

1. 
   
   <a id="fn-note-6177732d73636f7065"></a>
   
   [AWS's scope distinction](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/reserved-instances-scope.html). [↩](#fnref-note-6177732d73636f7065)


Reading path: [Useful compute](https://rawthoughts.in/collections/useful-compute/) > [A GPU price is not a job cost](https://rawthoughts.in/collections/useful-compute/a-gpu-price-is-not-a-job-cost/)

Title: The cost of an idle fleet

[Read HTML](https://rawthoughts.in/blog/the-cost-of-an-idle-fleet/)

Author: Harsh Joshi

<a id="the-cost-of-an-idle-fleet"></a>

# The cost of an idle fleet

A quiet compute fleet can have a smaller electricity bill and a worse cost per completed job. The apparent contradiction disappears once we separate what the operator spends from what the capacity produces. Expense can fall more slowly than useful work.

The customer's [cost per accepted result](https://rawthoughts.in/collections/useful-compute/a-gpu-price-is-not-a-job-cost/) includes the resources bought to obtain it. The operator faces another question: what does the installed system cost across the periods in which it works, waits and remains available? A paid reservation, an active device and useful output are different quantities on this side of the marketplace too.

<a id="idle-is-a-state-not-zero-power"></a>

## Idle is a state, not zero power

An awake server can consume energy without advancing its intended workload. [ENERGY STAR's guidance on unused servers](https://www.energystar.gov/products/data_center_equipment/5-simple-ways-avoid-energy-waste-your-data-center/identify-and-remove-unused-servers) identifies this waste and describes why removing unnecessary equipment can also reduce cooling and power-infrastructure demand. That does not supply a universal idle percentage for modern GPU systems. The actual equipment and its operating states need measurement.

An unallocated machine, an allocated machine waiting for data, a busy machine repeating failed work and a powered-down machine can all appear as "not producing" on an output report. Their electrical behaviour and obligations differ. A spare machine kept ready for recovery is not necessarily abandoned capacity. A server with little CPU activity may still provide a service whose availability matters.

The accounting boundary also has to include the supporting system. Host processors, memory, storage, networking, fans and power conversion are not free because the accelerator is waiting. Neither does the entire facility's cooling load disappear when one job stops.

<a id="a-smaller-bill-can-buy-fewer-results"></a>

## A smaller bill can buy fewer results

Consider a deliberately invented 100-hour operating period. An IT group draws 12 kW while working and 4 kW while awake but idle. Assume facility overhead is a constant 2 kW, electricity costs 0.2 arbitrary currency units per kWh, and continuing cash expenses excluding electricity are 600 units for the period. Assume the same workload produces two accepted jobs per working hour, with no failed attempts.

These assumptions are a toy model, not a GPU specification, tariff or facility measurement. They hold the workload and acceptance condition constant so that the denominator can be seen clearly.

| Measure over the same 100 hours | Working for 25 hours | Working for 75 hours |
| --- | --: | --: |
| IT energy | 600 kWh | 1,000 kWh |
| Facility overhead energy | 200 kWh | 200 kWh |
| Total facility energy | 800 kWh | 1,200 kWh |
| Electricity expense | 160 units | 240 units |
| Continuing cash expense including electricity | 760 units | 840 units |
| Accepted jobs | 50 | 150 |
| Cash expense per accepted job | 15.20 units | 5.60 units |

The first IT-energy figure is 12 × 25 plus 4 × 75. The second is 12 × 75 plus 4 × 25. Each then adds 2 × 100 for facility overhead.

For w working hours in this fixed hundred-hour period, the same assumptions give:

$$
\begin{aligned}
E_{\text{facility}}(w)&=12w+4(100-w)+2(100)=600+8w\quad\text{kWh},\\
K_{\text{cash}}(w)&=600+0.2E_{\text{facility}}(w)=720+1.6w,\\
J(w)&=2w,\\
\frac{K_{\text{cash}}(w)}{J(w)}&=\frac{360}{w}+0.8,\qquad w>0.
\end{aligned}
$$

The last expression reveals the shape of the cost: a fixed period expense spread across more work, plus a per-job term. At zero working hours there are expenses and no jobs over which to divide them. A chart should leave that point undefined, not quietly display a zero cost.

The quieter period spends 80 units less, yet produces one-third as many accepted jobs. Its cost per job is consequently much higher. This does not mean more activity is always desirable. It means that a lower aggregate expense cannot by itself demonstrate a more economical service.

<a id="cash-expense-and-capital-consumption-answer-different-questions"></a>

## Cash expense and capital consumption answer different questions

The toy model's 600 units represent expenses that continue during the period, such as a declared combination of staffing, maintenance and committed space or connectivity. Actual costs may change in steps rather than remain fixed indefinitely. The assumption is about this interval, not every possible scale of operation.

It deliberately excludes equipment acquisition. Paying for a machine and allocating its cost across its useful life are not the same event. For a longer-run cost comparison, suppose we separately assign 400 units of equipment cost to this period. The combined cost becomes 1,160 or 1,240 units, giving approximately 23.20 or 8.27 units per accepted job.

That added allocation is not another electricity invoice or proof of a cash payment during these hundred hours. It is an explicit assumption about spreading equipment cost. A real lifecycle comparison also needs its horizon, replacement and residual-value assumptions, with financing treated consistently. Mixing purchase payments, depreciation and repayments without a stated boundary can count the same equipment more than once.

Conversely, equipment already paid for is not free to own indefinitely. Continuing support, replacement and the capacity reserved for it remain questions even when the immediate cash needed to run one more job is small. Marginal dispatch and long-run capacity planning require different calculations.

<a id="pue-measures-a-boundary-not-useful-work"></a>

## PUE measures a boundary, not useful work

[The Green Grid defines power usage effectiveness](https://www.thegreengrid.org/node/372) as total data-centre energy divided by ICT-equipment energy:

$$
\mathrm{PUE}=\frac{E_{\text{facility}}}{E_{\text{IT}}}.
$$

In the toy example, that ratio is 800/600, about 1.33, in the quieter period and 1,200/1,000, or 1.20, in the busier one.

The busier case has the lower ratio and consumes more total electricity. The arithmetic follows from the assumed constant overhead. It is not evidence that real overhead is constant: cooling and electrical-system behaviour must be measured over the relevant loads and conditions.

More importantly, neither ratio contains accepted jobs. Two systems can have the same PUE and deliver different work. Within one system, failed work can increase IT energy and alter the ratio without improving the service. PUE helps locate infrastructure overhead; it cannot certify application efficiency or commercial viability.

<a id="occupancy-is-useful-only-alongside-the-workload"></a>

## Occupancy is useful only alongside the workload

A supplier may earn revenue for an allocation even when the customer is still preparing data. That allocation can be commercially meaningful without creating accepted output yet. Conversely, a faster model can finish the customer's work in fewer allocated hours, improving the customer's economics while leaving the operator more capacity to sell or manage.

The operator therefore needs to distinguish occupied time, activity, accepted work and the terms under which capacity is paid for. An energy bill does not establish revenue, and dividing cost by accepted jobs does not establish profit. Different services may have different acceptable output units; summing unlike tokens, experiments and simulations into one flattering fleet total does not make them comparable.

For the toy model, if the busier period accepts only 135 rather than 150 jobs, its unchanged 840-unit cash expense becomes about 6.22 per accepted job. The machine hours have not changed. The outcome has. [Model efficiency](https://rawthoughts.in/collections/useful-compute/making-the-cluster-useful/a-busy-gpu-is-not-an-efficient-model/) and acceptance remain separate observations that help explain the difference.

<a id="energy-management-has-to-preserve-the-promised-work"></a>

## Energy management has to preserve the promised work

Consolidating work or powering down unnecessary equipment can reduce waste. But an idle interval may be the headroom required for an imminent booking, a recovery path or a burst of requests. Removing it without understanding the promise can trade a visible energy saving for a service failure.

Moving a workload can consume the saving before useful work resumes. Its data must arrive, the destination must support the same environment, and a checkpoint must restore the right state. If the job's data must remain in a particular location, a cheaper remote machine cannot supply the booked service at all. If restarting takes longer than the recovery window, shutting down the idle spare removes capacity the customer was paying to have ready. The occupancy report alone contains none of those obligations.

The useful test is whether the change reduces resources for the same accepted service, including startup, checkpointing, restoration and the deadline. An alternative that saves energy but cannot restore progress in time has changed the product. That may be an acceptable renegotiation; it is not the original promise fulfilled more efficiently.

The aim is neither to keep every device busy nor to minimise electricity at any cost. It is to match installed capacity, operating states and available demand to useful work, while keeping the commitments that make the work worth doing. The fleet's quiet periods belong in that account, not outside it.

Title: From posters to throughput

[Read HTML](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/from-posters-to-throughput/)

Author: Harsh Joshi

<a id="from-posters-to-throughput"></a>

# From posters to throughput

Cheap GPU-hours without a usable start window are queueing theatre. A founder cannot ship a result with the price printed on a portal. The allocation has to arrive, the machines have to work together and the job has to finish while its result still matters.

That is the question behind an AI city. Lucknow can have ambition, land and a compelling presentation. It still needs a route from a customer's workload to a completed result. For a country familiar with services that fail when it rains, “the cloud” is a particularly good name to interrogate. IYKYK.

In September 2025, I wanted the national mission and the city policy to put those operating requirements into the same promise: what can a team book, when can it start, and what happens if the service fails? [Bubble or bridge?](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/bubble-or-bridge/) asked whether the investment cycle could build something durable. Here is what must exist for the bridge to carry traffic.

<a id="four-things-must-arrive-together"></a>

## Four things must arrive together

The first is electricity that can be delivered when the job needs it. The second is fibre connecting both the machines and their users. The third is a facility that can remove the heat without exhausting another local resource. The fourth is an operating team that turns the installed hardware into useful computation. A weakness in any one can make the other three expensive furniture.

<a id="power-calculation"></a>

### Electrons with a duration

A hypothetical 100 MW IT load at a power usage effectiveness, or PUE, of 1.3 draws 130 MW at the facility boundary. At constant load it consumes 3.12 GWh in a day. An eight-hour interval requires 1.04 GWh delivered to that boundary. For a 1 MW IT load the same arithmetic is:

$$
E=P_{\mathrm{IT}}\,\mathrm{PUE}\,t
=1\,\mathrm{MW}\times1.3\times8\,\mathrm{h}
=10.4\,\mathrm{MWh}.
$$

The battery's nameplate capacity must also cover unusable capacity and delivery losses. At a stipulated 80 percent usable fraction and 90 percent delivery efficiency, supplying that energy would require a nameplate capacity of approximately $10.4/(0.8\times0.9)=14.44$ MWh. Discharge power, reserve, degradation and the actual load profile still have to be designed. A large energy store that cannot supply the required power does not solve the interval.

For a sense of the national scale, CEA projected total storage requirements of 82.37 GWh for 2026–27 and 411.4 GWh for 2031–32, combining batteries and pumped storage.<sup><a id="fnref-note-6365612d73746f72616765"></a>[1](#fn-note-6365612d73746f72616765)</sup> Those are projections for the grid. By July 2026 the government's two battery-support schemes, for 43.8 GWh between them, had letters of award for 35.13 GWh, and the earlier scheme had commissioned 0.5 GWh. On 4 November 2026 the Cabinet approved support for a further 92 GWh of storage, 30 GWh of it batteries.<sup><a id="fnref-note-7667662d32303236"></a>[2](#fn-note-7667662d32303236)</sup> An AI campus needs its own supply specification, followed through tenders, awards, construction and commissioning.

A country can meet its aggregate peak demand while a particular campus lacks a firm connection. A renewable contract can be economical while leaving an evening gap. My preference is to attach incentives to the supply arrangement that closes the relevant gap, with its losses and failure conditions visible.

<a id="fibre-has-several-jobs"></a>

### Fibre has several jobs

A campus needs connections to an internet exchange or cable landing station as well as a network inside its training cluster. The public path carries requests and responses. The data path supplies training or application data. The interconnect coordinates distributed computation. A splendid speed-test result on one does not repair congestion on another.

Training often needs large contiguous allocations and sustained communication among devices. Inference additionally asks how long a user waits, including the slow end of the response-time distribution. An internet exchange helps only through the routes and peers actually used. Two carriers can share a duct, bridge or landing station; two contracts do not necessarily create two independent paths.

NIXI's 2021–22 annual report records the inauguration of seven exchanges in Uttar Pradesh.<sup><a id="fnref-note-6e697869"></a>[3](#fn-note-6e697869)</sup> A proposed campus still needs to establish its routes to those exchanges and measure the latency from its own site. In November 2026 PeeringDB listed three networks present at the NIXI Lucknow facility and no exchange recorded there.<sup><a id="fnref-note-70656572696e676462"></a>[4](#fn-note-70656572696e676462)</sup>

For a substantial training service, my September proposal called for a specified high-bandwidth fabric, very low oversubscription and enough sustained storage throughput to avoid starving the accelerators. Oversubscription compares the aggregate bandwidth offered to connected devices with the shared network capacity carrying it onward; at 1.2:1, those devices can collectively ask for 20 percent more bandwidth than that shared path can carry. Checkpoint writes save the training state needed to resume a run, so their speed affects both interruptions to training and recoverability. Illustrative requirements included an 800 Gbit/s-class fabric, oversubscription no worse than 1.2:1, and, per thousand GPUs, roughly 1–3 TB/s reads and 200–400 GB/s checkpoint writes. I would test those targets against the workload the service intends to support. The 800 Gbit/s figure specifies the proposed link rate; commissioning still has to establish the sustained throughput available to the connected workload.

<a id="water-and-heat-belong-in-the-same-design"></a>

### Water and heat belong in the same design

Densities in the tens of kilowatts per rack, potentially reaching around 120 kW in a proposed high-density configuration, change the cooling question. Liquid-cooling readiness, piping, heat rejection, serviceability and the local climate become part of the workload's home. They are not options to discover after the equipment arrives.

Water usage effectiveness, WUE, expresses water consumption relative to IT energy under a declared measurement boundary. ISO/IEC 30134-9 defines the indicator and its reporting categories.<sup><a id="fnref-note-7775652d7374616e64617264"></a>[5](#fn-note-7775652d7374616e64617264)</sup> Comparing two numbers without the category, period and climate can reward moving a burden outside the reported boundary rather than reducing it.

I proposed climate-adjusted procurement targets around 0.2–0.4 litres per kWh and at least 70 percent recycled water where the site's design and supply make those conditions suitable. ISO supplies the measurement method; I would set the contract targets to suit the site. Water availability, electrical overhead and reliable heat removal have to be assessed together.

<a id="mfu-calculation"></a>

### Installed FLOPs are not model FLOPs

A busy accelerator can spend time on communication, recomputation or work that does not advance the intended model. Model FLOPs utilisation, MFU, compares the model's declared useful arithmetic throughput with the relevant hardware peak. Hardware utilisation and fleet occupancy answer different questions. MFU requires a measurement of the arithmetic advancing the model, even when every rented device is occupied.

Published systems show that the distinction is worth engineering. Jiang and colleagues’ MegaScale paper reported 55.2 percent MFU for a 175-billion-parameter model on 12,288 GPUs.<sup><a id="fnref-note-6d6567617363616c65"></a>[6](#fn-note-6d6567617363616c65)</sup> Reaching that figure took extensive work on communication, kernels, data pipelines and stability for that training configuration. Each tenant's model needs its own measurement.

For fixed model work $F$, $n$ identical devices of relevant peak throughput $P$ and a sustained MFU $u$, the idealised elapsed time is:

$$
T=\frac{F}{nPu}.
$$

Holding the workload, devices and arithmetic convention fixed, moving from a stipulated 30 percent MFU to 50 percent makes the run take $0.30/0.50=0.60$ of its former time. GPU-hours and their charge at a constant hourly rate fall by 40 percent. Useful throughput rises by $0.50/0.30-1\approx66.7$ percent. The percentages differ because one measures work per unit of time and the other measures time and cost for the same work.

The comparison holds the accepted model work and quality target fixed. Changing precision, sparsity conventions, the model or the accepted result requires a new comparison. This estimate excludes fixed project costs and interruptions.

To give that comparison a scale, take the published Chinchilla dimensions of 70 billion parameters and 1.4 trillion training tokens, and use the approximate dense-training work $F=6ND=5.88\times10^{23}$ FLOPs.<sup><a id="fnref-note-6368696e6368696c6c61"></a>[7](#fn-note-6368696e6368696c6c61)</sup> For the following calculation, assign that work to a hypothetical allocation of 1,024 A100 GPUs at the datasheet's dense BF16 peak of 312 TFLOP/s per device.<sup><a id="fnref-note-61313030"></a>[8](#fn-note-61313030)</sup>

| MFU | Elapsed time | Metered GPU charge |
| --- | --- | --- |
| 30% | 71.0 days | 100% |
| 40% | 53.3 days | 75% |
| 50% | 42.6 days | 60% |

The charge is relative to the 30 percent MFU run, at the same hourly price.

The approximate $6ND$ work model omits additional model-specific arithmetic; estimating an actual run also requires that work and its operating overhead.

The practical consequence is substantial. Before subsidising another room full of accelerators, find out whether better scheduling, checkpointing, communication overlap and operator training can make the existing room deliver more. Efficiency is productive capacity too.

<a id="a-national-mission-and-a-city-policy-need-an-operating-layer"></a>

## A national mission and a city policy need an operating layer

The Cabinet approved the IndiaAI Mission in March 2024 with an outlay of ₹10,371.92 crore over five years.<sup><a id="fnref-note-636162696e6574"></a>[9](#fn-note-636162696e6574)</sup> By June 2026 its shared compute capacity had passed 45,000 GPUs, and in August 2026 the government reported 93.18 lakh GPU-hours sanctioned for 237 projects.<sup><a id="fnref-note-696e64696161692d32303236"></a>[10](#fn-note-696e64696161692d32303236)</sup> Neither count records hours used. Compute, foundational models, datasets, applications, skills, startup finance and safe and trusted AI belong in the same programme because machines alone do not supply an ecosystem. A marketplace can make access more affordable while leaving a startup uncertain about when a connected allocation will begin.

Uttar Pradesh's original 2021 data-centre policy targeted 250 MW and three parks, with financial and infrastructure incentives. The amended policy and subsequent project approvals have their own scope and dates; establishing usable AI-training capacity requires commissioning and workload measurements.<sup><a id="fnref-note-75702d706f6c696379"></a>[11](#fn-note-75702d706f6c696379)</sup> The 2021 policy's successor, notified in July 2026, aims at more than 2 GW of additional capacity. It raises a park's interest-subsidy ceiling for installing at least 700 double-precision AI compute units, for a PUE at or below 1.35, 1.45 or 1.60, and for a renewable share above 20, 50 or 70 percent.<sup><a id="fnref-note-75702d706f6c6963792d32303236"></a>[12](#fn-note-75702d706f6c6963792d32303236)</sup> Those conditions count installed devices and facility efficiency. My procurement conditions ask for a start window and training efficiency. The enduring question for Lucknow is which actual service its incentives are meant to create.

I would begin with regional inference, application engineering and GCC-linked demand, then add larger training allocations when power, firming, fibre and the operating team can support them. Noida's established data-centre cluster offers an operating ecosystem to learn from. Lucknow needs its own customer, route and commissioning tests.

I would decide that sequence from the workload: the power and fabric available for an inland training run, or the measured latency of a more distant inference service. Those measurements determine where the service can run.

<a id="put-the-promise-on-a-calendar"></a>

## Put the promise on a calendar

Public-compute access should be bookable as an allocation with a topology and a start window. In September 2025 I proposed connected blocks of at least 256 GPUs for one to fourteen days as a useful training offer, alongside smaller allocations.

AWS Capacity Blocks supply a concrete example of future-dated reservations placed within a suitable cluster. The service's durations and limits have changed; by November 2026 its documentation offered blocks of up to 182 days.<sup><a id="fnref-note-63617061636974792d626c6f636b73"></a>[13](#fn-note-63617061636974792d626c6f636b73)</sup> The transferable idea is that the buyer reserves a defined interval and configuration, rather than hoping a list price eventually becomes availability.

The agreement should say what happens if the start slips, a machine fails or a checkpoint cannot be recovered. Credits allocate a financial consequence; they cannot restore a missed launch. That is why the delivery window and recovery obligation belong beside the price.

<a id="what-i-would-put-in-the-procurement-conditions"></a>

## What I would put in the procurement conditions

I would tie subsidies to demonstrated operating capability, using the following targets and checks in the contract.

| Part of the service | Proposed condition | Evidence that makes it meaningful |
| --- | --- | --- |
| Firm power | An agreed round-the-clock supply fraction, proposed at 85–90 percent, with the remaining interval and backup explicit | Metered supply, the PPA, connection capacity, storage discharge power and delivered energy |
| Route diversity | Two independently traced routes towards suitable exchanges and landing infrastructure | Physical route survey and failover measurement, rather than two carrier logos |
| Cooling and water | Climate-adjusted WUE and recycled-water targets, with high-density cooling readiness | Declared measurement boundary, commissioning tests and seasonal operating data |
| Facility design and commissioning | Design and commissioning certification against the applicable ISO/IEC 22237 requirements before top-tier subsidies, with annual PUE and WUE publication | The specified requirements, certificate and commissioning results for the facility being funded |
| Incident response | Named escalation, a proposed 15-minute P1 response and quarterly drills | Timed exercises, responsible operators and retained recovery evidence |
| Allocation calendar | A declared start window and remedy, with a proposed 5 percent daily credit for qualifying delay | Booking, actual start, exclusions and remedy records for the same allocation |
| Training efficiency | Operator median MFU of at least 0.50 on the agreed reference workload as a proposed subsidy gate | A published workload, arithmetic/peak convention, sampling period and reproducible measurements |

A certificate needs a defined scope. [ISO/IEC 22237](https://www.iso.org/standard/78550.html) addresses data-centre facilities and infrastructure, including availability, security and energy efficiency. The selected computing equipment and software are outside that scope. The buyer therefore needs both facility certification and workload acceptance tests. A “Tier-ish” label would tell the buyer too little about what was checked.

I would make measured training efficiency a condition of public support. Its reference workload is essential. A median pooled across incomparable models, precisions and device generations would not test the stated condition. The sample must also disclose failed runs and measurement exclusions so the threshold cannot be satisfied simply by omitting inconvenient work. An inference service needs its own latency-and-load acceptance test. The MFU condition applies to the training service being purchased.

Some obligations already have a legal source. CERT-In's April 2022 directions require covered entities to report the specified cyber incidents within six hours of noticing them or being informed, maintain relevant ICT logs securely in India for a rolling 180 days and synchronise clocks to NIC/NPL or qualifying traceable sources.<sup><a id="fnref-note-636572742d696e"></a>[14](#fn-note-636572742d696e)</sup> Alongside those duties, I would require a fifteen-minute operational response and quarterly drills.

Permits need a clock too. I proposed a sixty-day right-of-way handling target and coordinated commissioning rather than serial surprises across agencies. That is a delivery proposal; the legal process for an actual route must use the applicable rules and authority. Since January 2025 the applicable rules are the Telecommunications (Right of Way) Rules, 2024, which set a decision timeline of up to 67 days and treat permission as granted when that timeline is missed.<sup><a id="fnref-note-726f772d72756c6573"></a>[15](#fn-note-726f772d72756c6573)</sup> A subsidy agreement should specify its obligations plainly instead of borrowing a policy slogan as though it were a completed permission.

<a id="three-customers-three-acceptance-tests"></a>

## Three customers, three acceptance tests

A team doing a large training run may ask for at least 256 connected GPUs, sustained step throughput and a recoverable multi-day interval. Its test should include communication, reading data, writing checkpoints and restarting from one. A GPU count alone leaves the job unspecified.

A smaller team fine-tuning a model with LoRA might need 64 or fewer devices. Its bottleneck could be memory, data preparation or how quickly several short experiments can start. Making it wait for a giant cluster-shaped product can be as wasteful as giving a giant run disconnected fragments.

An interactive application may need a 95th-percentile latency budget, or p95: the elapsed time within which 95 percent of measured requests finish. A proposed target might be in the 10–30 ms range for a particular service stage or regional path. The measured boundary must be explicit: network round trip, model processing, time to first token and total response are different quantities. A busy fleet that violates the customer's latency target is failing that job even while it looks excellent on an occupancy chart.

A campus needs to say which of these jobs it can actually sell and support.

<a id="what-would-make-the-plan-change"></a>

## What would make the plan change?

My proposed timetable began in September 2025: publish allocation windows and queue behaviour within ninety days; secure the route and firm-power arrangements over the following six to nine months; then judge commissioned capability against the FY27 horizon. In May 2026 the compute portal promised allocation within two days for requests under 100 compute-hours and within seven days above that, and by June an approval lapsed unless use began within 30 days.<sup><a id="fnref-note-706f7274616c2d736c61"></a>[16](#fn-note-706f7274616c2d736c61)</sup>

Storage slipping by two quarters should force a review of incentives and sequencing. Operational IT load below the proposed 1.5 GW floor in 2027 should weaken the assumed pace of the national buildout, using a consistent capacity definition. The government reported 1.57 GW of installed data-centre power capacity for August 2026.<sup><a id="fnref-note-64632d32303236"></a>[17](#fn-note-64632d32303236)</sup> Sustained household stress should pull applications and employment capability back into the centre of the programme. [The buyer matters as much as the campus](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/bubble-or-bridge/).

Those tests prevent every announcement from counting as success. [The later IndiaAI reporting investigation](https://rawthoughts.in/collections/ideas/india-ai/what-the-compute-numbers-count/) asks a complementary question: can we connect approved and accessed hours to consumed hours and identifiable outcomes? An honest answer can recognise useful models already produced while leaving a programme-wide conversion rate unresolved.

I want India's AI capacity to be credible enough that a team can plan its work around it. Put the power, water, routes, connected allocation, operating efficiency and response obligation into the same promise. Then let a real job run through it. That is when an AI city stops being a poster and starts being a place where work gets done.

1. 
   
   <a id="fn-note-6365612d73746f72616765"></a>
   
   [CEA's planning breakdown](https://www.pib.gov.in/PressReleasePage.aspx?PRID=1928750&lang=1&reg=3). [↩](#fnref-note-6365612d73746f72616765)

2. 
   
   <a id="fn-note-7667662d32303236"></a>
   
   [The Rajya Sabha answer of 27 July 2026](https://www.powermin.gov.in/static/uploads/2026/07/f59419a881df9acc24bed8753f6d9fda.pdf) and [the Cabinet approval of 4 November 2026](https://www.pmindia.gov.in/en/news_updates/cabinet-approves-rs-14500-crore-viability-gap-funding-scheme-for-development-of-92-gwh-grid-scale-energy-storage-systems/). [↩](#fnref-note-7667662d32303236)

3. 
   
   <a id="fn-note-6e697869"></a>
   
   [NIXI's annual report](https://nixi.in/wp-content/uploads/2022/12/NIXI-Annual-Report-2021-2022_FINAL_U.pdf). [↩](#fnref-note-6e697869)

4. 
   
   <a id="fn-note-70656572696e676462"></a>
   
   [PeeringDB's NIXI Lucknow record](https://www.peeringdb.com/fac/11769). [↩](#fnref-note-70656572696e676462)

5. 
   
   <a id="fn-note-7775652d7374616e64617264"></a>
   
   [The WUE standard](https://www.iso.org/standard/77692.html). [↩](#fnref-note-7775652d7374616e64617264)

6. 
   
   <a id="fn-note-6d6567617363616c65"></a>
   
   [The MegaScale paper](https://arxiv.org/abs/2402.15627). [↩](#fnref-note-6d6567617363616c65)

7. 
   
   <a id="fn-note-6368696e6368696c6c61"></a>
   
   [The Chinchilla paper and Appendix F](https://arxiv.org/abs/2203.15556). [↩](#fnref-note-6368696e6368696c6c61)

8. 
   
   <a id="fn-note-61313030"></a>
   
   [NVIDIA's A100 specifications](https://www.nvidia.com/content/dam/en-zz/Solutions/Data-Center/a100/pdf/nvidia-a100-datasheet-us-nvidia-1758950-r4-web.pdf). [↩](#fnref-note-61313030)

9. 
   
   <a id="fn-note-636162696e6574"></a>
   
   [The Cabinet approval](https://www.pib.gov.in/PressReleaseIframePage.aspx?PRID=2012355&lang=2&reg=3). [↩](#fnref-note-636162696e6574)

10. 
    
    <a id="fn-note-696e64696161692d32303236"></a>
    
    [The government's August 2026 factsheet](https://www.pib.gov.in/FactsheetDetails.aspx?Id=150860) and [the parliamentary answer of 6 August 2026](https://www.pib.gov.in/PressReleasePage.aspx?PRID=2295477). [↩](#fnref-note-696e64696161692d32303236)

11. 
    
    <a id="fn-note-75702d706f6c696379"></a>
    
    [The policy and its amendment](https://invest.up.gov.in/up-data-centre-policy-2021/). [↩](#fnref-note-75702d706f6c696379)

12. 
    
    <a id="fn-note-75702d706f6c6963792d32303236"></a>
    
    [Uttar Pradesh Data Centre Policy 2026](https://invest.up.gov.in/uttar-pradesh-data-centre-policy-2026/). [↩](#fnref-note-75702d706f6c6963792d32303236)

13. 
    
    <a id="fn-note-63617061636974792d626c6f636b73"></a>
    
    [AWS's Capacity Blocks purchase terms](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-blocks-purchase.html). [↩](#fnref-note-63617061636974792d626c6f636b73)

14. 
    
    <a id="fn-note-636572742d696e"></a>
    
    [CERT-In's directions](https://www.cert-in.org.in/PDF/CERT-In_Directions_70B_28.04.2022.pdf). [↩](#fnref-note-636572742d696e)

15. 
    
    <a id="fn-note-726f772d72756c6573"></a>
    
    [The Telecommunications (Right of Way) Rules, 2024](https://www.trai.gov.in/sites/default/files/2024-09/Telecommunications_17092024.pdf). [↩](#fnref-note-726f772d72756c6573)

16. 
    
    <a id="fn-note-706f7274616c2d736c61"></a>
    
    [The compute portal's allocation commitment](https://compute.indiaai.gov.in/sla), as published in May 2026, and [its access terms](https://compute.indiaai.gov.in/), as published in June 2026. [↩](#fnref-note-706f7274616c2d736c61)

17. 
    
    <a id="fn-note-64632d32303236"></a>
    
    [The government's data-centre note of 14 September 2026](https://www.pib.gov.in/PressNoteDetails.aspx?NoteId=159969). [↩](#fnref-note-64632d32303236)


Reading path: [Ideas](https://rawthoughts.in/collections/ideas/) > [India's AI crossing](https://rawthoughts.in/collections/ideas/india-ai/) > [Testing India's AI crossing](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/) > [From posters to throughput](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/from-posters-to-throughput/)

Previous in journey: [Bubble or bridge?](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/bubble-or-bridge/)

Next in journey: [Tracing the infrastructure story](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/tracing-the-infrastructure-story/)

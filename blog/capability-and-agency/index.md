Title: What can it understand, and what can it change?

[Read HTML](https://rawthoughts.in/blog/capability-and-agency/)

Author: Harsh Joshi

<a id="what-can-it-understand-and-what-can-it-change"></a>

# What can it understand, and what can it change?

A service team adds workers to reduce late orders. Its dashboard then shows more lateness on shifts with extra staff. Did the intervention make things worse, or did the team send help precisely where work was already hardest?

An AI application might confidently recommend a staffing change from that dashboard and also have the API access to apply it. Its ability to find a pattern, its ability to reason about an intervention and its reach into the rota are three different properties. I find that separation more useful than a single label such as "agentic" or "causal": it tells us which question to test, and what a mistaken answer can actually change.

[Beyond the Mirage](https://causality.in/blog/beyond-the-mirage/) (on Causality) develops the wider proposal: describe intelligence by its depth of causal reasoning and, separately, by how much it can act on the world. Here I want to follow those two questions through one operational decision. What would the team need to know before changing the rota?

<a id="three-questions-hiding-in-one-dashboard"></a>

## Three questions hiding in one dashboard

Consider a service team trying to reduce late orders. These questions sound related, but ask for different answers. "Which orders are likely to be late?" asks for a prediction under the observed conditions. "Would adding another worker reduce lateness?" asks about the effect of a change. "Would this particular late order have arrived on time if another worker had been assigned?" asks about a counterfactual for one event. The output format might be identical: a probability, a short explanation and a recommendation. That does not make the evidential requirements identical. A useful forecast may exploit a pattern that would disappear when the operation changes. An average effect need not resolve what would have happened to a particular order.

The causal-inference literature formalises distinctions between observational, interventional and counterfactual questions. It also explains why identifying an effect from observations depends on the available information and assumptions about the causal structure.<sup><a id="fnref-note-686965726172636879"></a>[1](#fn-note-686965726172636879)</sup> Observational data can sometimes support an identified effect; the assumptions must do real work rather than remain implicit.

The staffing team needs to choose which of these questions its decision depends on, then test whether the application can answer it under the stated assumptions.

<a id="when-the-helpful-worker-looks-harmful"></a>

## When the helpful worker looks harmful

Suppose the team recorded these orders. The numbers are constructed to show how the workload mix changes the comparison.

| Workload | Extra worker: late / total | Ordinary staffing: late / total |
| --- | --- | --- |
| Quiet | 1 / 20 = 5% | 8 / 80 = 10% |
| Busy | 32 / 80 = 40% | 12 / 20 = 60% |
| Combined | 33 / 100 = 33% | 20 / 100 = 20% |

Pooling the rows makes extra staffing look associated with more lateness. Looking within each workload group reverses that association. Extra workers were assigned much more often during busy periods, when lateness was higher in either staffing condition.

Giving both staffing conditions the same quiet/busy mixture makes the arithmetic visible. With equal weights on the two workload groups, the extra-worker rate is $(0.05+0.40)/2=0.225$; the ordinary-staffing rate is $(0.10+0.60)/2=0.35$. These standardised associations are 22.5% and 35%, rather than the pooled 33% and 20%. Adjustment has changed which population is being compared. Whether it identifies the causal effect still depends on why workers were assigned and what the workload measure leaves out.

The table alone does not prove that an extra worker helps. Other differences could affect both assignment and lateness, including complexity that the quiet/busy label misses. It does show why an answer based on the pooled percentage can address the wrong question.

An evaluator should ask what staffing decision was being estimated, how assignment happened, whether workload is measured appropriately and which remaining influences the analysis assumes away. If a suitable experiment is available, its assignment and measurement design matter. If observational identification is proposed, the causal assumptions and adjustment must be justified. Better prose cannot fill that gap.

Nor should the evaluator turn this into an impossible demand that every recommendation predict an individual's alternative history. A decision may appropriately use an estimated population effect. The point is to choose the question the decision requires, not always demand the strongest-sounding one.

<a id="a-solver-can-reason-without-acting"></a>

## A solver can reason without acting

Imagine a read-only application given an explicit causal model of a small queueing system. A solver computes the consequences of changing one parameter under that model. It has no permission or interface to alter production staffing. Its answer can be checked against the supplied model, even though the model's fit to the actual workplace remains a separate question.

Now imagine a bot that can add a worker to the rota through an API. It may execute a straightforward rule correctly while having no demonstrated ability to estimate the change's effect on lateness. The operation succeeded; the causal question remains unanswered.

These countercases are enough to reject a shortcut: counting tool calls does not measure causal competence, and withholding write access does not imply an inability to analyse interventions. Tools can extend a system's information or computation, but their contribution must appear in the evaluated system rather than be attributed automatically to the language model alone.

A combined application may use a language model to translate the request, a retrieved source to supply assumptions and a solver to calculate an answer. Its performance is a property of that composition under those conditions. An ablation that removes the solver answers a different question from one that tests the full workflow. Both can be useful if their objects are named.

<a id="an-evaluation-should-survive-a-change-of-story"></a>

## An evaluation should survive a change of story

For the service-team application, I would first evaluate prediction on held-out conditions that resemble its intended use. I would then assess intervention estimates in settings where the target effect has an independently justified reference, and include changes that break convenient correlations. I would separately test the bot's operations, including partial failures and the consequences of repeating an action.

The test report would state the task, data, assumptions, system composition and metric. It would show where performance failed instead of converting the average into a universal capability claim. A model that solves a supplied causal exercise has demonstrated something useful. It has not thereby demonstrated that it can discover a correct causal model from an arbitrary organisation's records.

Metric choice also shapes the picture. Schaeffer, Miranda and Koyejo demonstrated how particular discontinuous metrics can make smooth changes in model outputs appear as abrupt capability emergence.<sup><a id="fnref-note-6d6972616765"></a>[2](#fn-note-6d6972616765)</sup> That result is a reason to inspect the measurement, not a proof that every surprising behaviour is predictable or that genuine transitions are impossible.

Where possible, I would keep the underlying errors and partial successes alongside the headline score. For a staffing estimate, getting the direction right while being badly wrong about magnitude is different from getting both wrong. For an action, choosing correctly but applying the change twice is different from choosing badly and executing precisely. One total score can hide the distinction that matters for deployment.

<a id="more-reach-changes-the-consequences"></a>

## More reach changes the consequences

Operational reach deserves its own description: which systems the application can affect, how long it can continue without review, how actions compose and whether a mistake can be reversed. That is not a second intelligence score. It describes the consequence of being wrong.

A weak predictor with broad write access can cause substantial harm. A stronger analytical system kept read-only may produce a bad recommendation without directly changing the world. Neither case settles overall safety, but they demand different controls and different evidence. Improving the answer and limiting the consequence are complementary jobs, not substitutes.

The same method applies to [generated code](https://rawthoughts.in/blog/checking-generated-code/). Writing plausible code, satisfying an independently reviewed contract and being allowed to execute the result are distinct achievements. For the person running the service, a capability label needs to lead back to this practical account: what the system has demonstrated, what it is allowed to change and which test would justify the next step.

1. 
   
   <a id="fn-note-686965726172636879"></a>
   
   [Bareinboim, Correa, Ibeling and Icard's account of the causal hierarchy](https://causalai.net/r60.pdf). [↩](#fnref-note-686965726172636879)

2. 
   
   <a id="fn-note-6d6972616765"></a>
   
   [Schaeffer, Miranda and Koyejo's original paper](https://arxiv.org/abs/2304.15004). [↩](#fnref-note-6d6972616765)

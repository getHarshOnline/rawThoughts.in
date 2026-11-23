Title: Understand the reference prototype

[Read HTML](https://rawthoughts.in/rawfish/use-the-local-prototype/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="understand-the-reference-prototype"></a>

# Understand the reference prototype

A creator wants to replace a weekly long-form explainer with daily clips. Before announcing the change, they want to know what regular viewers might misunderstand and what a newcomer would need to find. RawFish's reference prototype explores how to carry that question from a scenario into a report, keeping the inputs and settings available for inspection.

The prototype is an earlier implementation, separate from the [planned rebuild](https://rawthoughts.in/rawfish/rehearse-a-decision/). It is not available as a public application or hosted service. Developers with its source checkout have a [local walkthrough and configuration guide](https://docs.rawthoughts.in/rawfish/using). The account below explains the work it can represent without requiring that checkout.

<a id="continue-through-the-six-cockpit-steps"></a>

## Continue through the six cockpit steps

Consider this fictional announcement:

> Our channel is replacing its weekly long-form explainer with short daily clips next month. The full archive stays available, but new explainers stop. We have a fixed production budget and want newcomers to understand the work without losing the depth regular viewers value.
> 
> Stress question: where does this announcement leave viewers unsure what they will receive?
> 
> Assumptions: regular viewers value the explanations; newcomers need a shorter entrance; the team cannot produce both formats daily.
> 
> Success: viewers can distinguish the new clips from the archive and find the explanation behind a clip.
> 
> Failure modes: regular viewers read the change as abandonment; a newcomer sees an excerpt without its qualification.
> 
> What could change a view: a clear route to the longer explanation and an honest account of what production will stop.

The question is more useful than asking whether “the audience” likes short videos. It identifies a change the creator can explain or revise. Keeping the assumptions beside the announcement also makes them available to challenge: perhaps regular viewers value the weekly rhythm more than the format itself.

The cockpit gives that work six places:

| Step | What belongs there | What the Creator prototype does |
| --- | --- | --- |
| Scenario | The announcement, stress question and source material | Accepts pasted text and proposes a title, question and cohorts |
| Build | The setting in which the question will be examined | Saves the run and shows its configured stakeholder cohorts connected to it by `TESTS_AGAINST` relationships |
| Cohorts | The groups and assumptions about their behaviour | Keeps settings and their origins available to inspect and change before launch |
| Preflight | The resources and conditions of the proposed run | Checks the provider, model, address, readiness, scale, token estimate, latency and available external cost |
| Simulate | Execution of the configured rehearsal | Records a deterministic completion marker for Creator; it does not run an agent conversation |
| Findings | The report, questions about it and supporting records | Makes a separate model call to generate a report, with Read, Ask and Analysis views |

Build's graph describes the run and its configured groups. It is not a world or influence network inferred from the announcement. The initial Creator cohorts, **Long-time fans**, **Gen-Z skeptics** and **Casual viewers**, are authored archetypes rather than measured audience groups. Their names invite different questions about the clips, archive and future explainers; they do not establish how actual viewers divide into groups.

The prototype also has Internal policy and Public policy lanes, with different scenario fields, report questions and a different runner. Creator's completion behaviour does not describe those runners. The [planned workflow](https://rawthoughts.in/rawfish/rehearse-a-decision/#choose-the-decision-context) explains the distinct decisions each lane is intended to serve.

<a id="keep-the-scenario-with-its-settings"></a>

## Keep the scenario with its settings

Suppose the creator changes the Long-time fans' **Sentiment bias** from `0` to `-0.2`. The prototype can save that change, refresh the settings hash and prepare the run again. The workbench also carries activity, influence and active hours; policy lanes add opinion-drift controls. Origin labels distinguish a supplied value, a lane default, a prior and a random draw. They identify where a value came from, not whether it measures a population.

**Note**

**A saved setting is not an executed experiment.** Creator saves the changed setting in configuration and completion metadata, but its report prompt does not use that setting. Changing the sentiment value is therefore not a test of audience sentiment.

Reseeding records the old and new settings in lineage and prepares the same run. It does not create a second executable run or report. Separate variant runs belong to the rebuild design. That difference matters when comparing results: an account of what changed in configuration cannot substitute for two executions under those conditions.

The scenario itself needs equal care. The prototype accepts pasted text; its other source markers do not connect an upload, cache, feed or graph import. An unsaved draft stays in page memory, whereas a saved run has an identifier and backend state. Keeping an address is not the same as preserving an unsaved draft or giving another person access to a saved one.

<a id="read-what-the-run-actually-supports"></a>

## Read what the run actually supports

The announcement says that new explainers will stop. A report may propose that long-time viewers would read this as abandonment. The first statement can be checked against the text. The second needs evidence about viewers.

**Caution**

**Creator's report has no executed conversation behind it.** A reaction labelled “simulated observation” is still a proposal from the report model on this path. A generated quotation is not testimony.

[Read the findings](https://rawthoughts.in/rawfish/read-the-findings/) explains the five claim labels and how to question their support. A model call can also fail report validation: text returned by a provider is not necessarily a valid report. Keep the scenario, model choice and any error with the result being examined.

<a id="compare-settings-before-comparing-reactions"></a>

## Compare settings before comparing reactions

The prototype's Analysis view compares the latest settings with their parent snapshot. Its **present**, **missing** and **corrupted** categories describe settings subjects. They can expose a lost or changed input; they do not establish that two valid reports were compared.

A different announcement asks a different question. Replace “new explainers stop” with “one new long-form explainer will remain each month; daily clips replace the other weekly editions.” In the prototype, this requires a separate scenario and report, with the provider, cohorts and other settings kept aligned. The original draft, stress question and both run identifiers give the comparison a basis.

Read the reports side by side. Does the monthly explanation change the proposed concern about abandonment? Does ambiguity about the archive remain? This is a manual comparison of separate scenarios, not an automatic paired experiment. Wording can vary between model calls, and a missing or invalid report leaves the comparison incomplete. Neither result estimates how many real viewers share a concern.

The useful next step is a question the creator can take to viewers, or a clearer announcement they can try. RawFish's [planned rebuild](https://rawthoughts.in/rawfish/rehearse-a-decision/) would connect simulated events to findings and preserve separate variants. The reference prototype helps expose why those connections matter before a polished report makes them easy to overlook.


Reading path: [RawFish](https://rawthoughts.in/rawfish/) > [Understand the reference prototype](https://rawthoughts.in/rawfish/use-the-local-prototype/)

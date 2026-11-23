Title: Rehearse a decision

[Read HTML](https://rawthoughts.in/rawfish/rehearse-a-decision/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="rehearse-a-decision"></a>

# Rehearse a decision

A team is preparing a return-to-office policy. Asking whether staff will like it tells them little about what to change. Asking where the proposed phasing conflicts with team responsibilities gives them something to work on: a timetable, an exception or a responsibility that needs clarifying.

[RawFish](https://rawthoughts.in/rawfish/) helps you rehearse a decision this way. You describe the proposal and the people it affects, then examine how it could go wrong in a small simulated world. The useful result is a better question or a proposal worth revising before it meets the real setting. The retained prototype covers only part of this, so the steps below follow the rebuild's design.

**Note**

**Using the reference prototype?** Its [Creator walkthrough](https://rawthoughts.in/rawfish/use-the-local-prototype/) generates a report without running an agent conversation. Treat that report as a model's response to your material, not a record of simulated exchanges.

<a id="give-the-rehearsal-something-to-question"></a>

## Give the rehearsal something to question

Start with the proposal people would actually encounter. For the workplace team, that means the policy text and its rollout dates, rather than a summary saying that people must return to the office. Add the question about phasing, the groups affected, what success would look like and the failures you want to examine.

Then make the assumptions visible. Do managers have time to explain the change? Are teams working to the same schedule? What would change each group's view? Include the strongest case for the proposal as well as the objections. A rehearsal built entirely from reasons to reject the policy is unlikely to tell you much about why it might work.

Begin with pasted text. Review any scenario details or groups RawFish suggests before using them. Uploads and live feeds need their own source controls before they can become part of a run.

<a id="choose-the-decision-context"></a>

## Choose the decision context

RawFish calls each kind of rehearsal a **lane**. The choice changes the groups, language and questions in the report:

| Lane | Bring a decision about | Look for |
| --- | --- | --- |
| Creator | A post, announcement, newsletter or episode | Lost context, audience confusion and tensions between groups of readers |
| Internal policy | A workplace change or rollout | Conflicting responsibilities, manager bottlenecks and unclear exceptions |
| Public policy | A regulation, consultation or civic decision | Implementation constraints, unequal effects and unintended incentives |

The workplace proposal belongs in Internal policy. It needs groups such as employees and managers, with their different responsibilities. A public consultation needs a different account of who is affected and how they can respond. Neither calls for inventing the thoughts of a named person. The design uses aggregate groups and archetypes; it excludes impersonation, decisions about named employees, workplace-emotion inference, election influence and fabricated constituent voices.

**Important**

**Use only material you have authority to use.** Sensitive workplace material is excluded. Internal-policy rehearsals take no public social feeds, and public-policy rehearsals take no workplace material.

<a id="decide-who-hears-what"></a>

## Decide who hears what

The **Build** step turns the scenario into a graph of groups, institutions and channels. This is where the workplace team can examine an assumption that might otherwise pass unnoticed: does everyone read the complete policy, or do managers explain it to their teams? Those are different situations, even with identical policy text.

In **Cohorts**, describe how the groups take part: their activity, response delay, active hours, sentiment and influence. Policy lanes also account for how strongly people hold their initial views, how others influence them, when they compromise and how trust decays. Creator uses the smaller set its own model needs.

Read each control's value, where it came from and its uncertainty. A default is a starting assumption, not a measurement of the people affected. Lock a value while changing another, or follow the source behind it. This matters when interpreting a reaction: did it emerge from an exchange, or did the setup largely decide it?

<a id="follow-the-exchange-into-the-report"></a>

## Follow the exchange into the report

Before a run, **Preflight** checks the chosen model and shows the proposed scale, token estimate, latency and any available external cost. Choose Ollama or another compatible local server, or explicitly configure an external provider. An unknown price remains unknown. Graph memory can call other services even when the report model runs locally. The [model and memory explanation](https://rawthoughts.in/rawfish/configure-the-prototype/) follows where those different calls can send data.

**Simulate** freezes the configuration and runs the exchange round by round. In the workplace case, follow a manager's explanation and the responses to it. A creator conversation or a public comment uses its own lane's language. Follow a report's claim back to the actual events in the run; a plausible exchange in the report is not enough.

**Findings** has three ways into that result: **Read** for the report, **Ask** for questions about its support, and **Analysis** for settings, comparisons and underlying data. The scenario, settings, seeds and model stay with the run. They let you inspect its conditions, although a later model call may produce different wording. [Read the findings](https://rawthoughts.in/rawfish/read-the-findings/) explains how the five claim labels distinguish a source passage, an assumption and a simulated reaction.

<a id="change-one-thing-you-can-account-for"></a>

## Change one thing you can account for

Suppose the workplace team revises the rollout dates. To compare that proposal with the first one, they need to keep both versions and know what else changed. **Save** keeps a configuration revision before execution; **Save and re-seed** makes a separate variant with different random draws, leaving the base run available.

A variant changes the configuration. An ensemble repeats one configuration with different random draws. The first lets you examine a changed premise; the second helps reveal how much results vary under the same premises. Keep a change to the rollout dates separate from a change in random draw. Compare the settings first, then the reports and what supports them. A missing report cannot count as agreement, and changing a slider does not by itself show how sensitive the outcome is to that factor. Full sensitivity analysis, outside priors and individual-trait editing are later work. Comparing a direction taken with one not taken is what RawFish is designed around: it varies one thing you declare in the same simulated world and compares what follows. Today a second version of a proposal gets its own scenario and report beside the first, and that comparison is the next piece to build.

<a id="take-the-question-back-to-the-real-setting"></a>

## Take the question back to the real setting

The rehearsal might expose an exception the policy never addressed or a responsibility that two groups understood differently. The team can revise the proposal, ask affected people about the problem or try a reversible operational change. Generated personas are not a sample of employees; their reactions help identify what to investigate. That is also how a lane earns weight over time: observed outcomes, compared with what its rehearsals proposed, calibrate it.

RawFish works on its own, inside another application that owns the work, or as a service another tool calls. In the rebuild's design its engine is organised in three layers other tools can call, the swarm, the comparison of a direction taken with one not taken, and the lanes, and its parts, such as a run, a cohort, a claim or a comparison, are components any host can show, so a chat or another application can render one as a card beside its own work. The retained prototype is neither layered nor built from components that way. It is a peer of the tools it is used with: a rehearsal of how people might react to a change can sit beside a calculation of what that change costs, composed in a notebook, with either one going first. [Pale](https://rawthoughts.in/pale/understand-your-world/#use-connected-applications-for-their-own-strengths) can compose the two without a notebook and coordinate a rehearsal with its follow-up investigation, and a method in Pale's library, for a search-optimisation or policy question, can run a rehearsal as one of its steps; [Weave](https://rawthoughts.in/weave/) links it to the decision and discussion, while the rehearsal itself stays with RawFish. The team still decides what to change after examining the findings.

The same distinction applies to other decisions. A library considering mandatory appointments might uncover tension between predictable staffing and unplanned access. Service records, conversations and a trial can show whether that tension occurs in practice. A rehearsal about a publication might suggest that an unfamiliar reader misses a qualification; actual reader feedback can test it, while the publisher still decides what to release.


Reading path: [RawFish](https://rawthoughts.in/rawfish/) > [Rehearse a decision](https://rawthoughts.in/rawfish/rehearse-a-decision/)

Title: How opinions move inside a rehearsal

[Read HTML](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/how-opinions-move/)

Author: Harsh Joshi

<a id="how-opinions-move-inside-a-rehearsal"></a>

# How opinions move inside a rehearsal

A simulated conversation needs more than different opening opinions. It needs a reason those opinions change, persist or cease to meet. If every agent simply receives the whole conversation and generates another response, an apparent consensus may come from the prompt's shape rather than the social mechanism we wanted to examine.

[RawFish](https://rawthoughts.in/rawfish/)’s planned cockpit would put these choices beside the world graph and cohort settings. We could specify who hears whom, how strongly a starting opinion persists and when two agents exchange views, then let the language model express the resulting stance. Changing a rule would give us a different rehearsal to compare. These are possible conversations generated from our assumptions; actual audiences need their own observations.

<a id="the-starting-opinion-can-keep-pulling"></a>

## The starting opinion can keep pulling

The Friedkin-Johnsen model represents an opinion as a combination of interpersonal influence and attachment to its initial position. [Friedkin and Johnsen's original paper](https://doi.org/10.1080/0022250X.1990.9990069) develops this social-process approach; [a recent mathematical treatment](https://arxiv.org/html/2602.08704v2) makes the susceptibility and network conventions explicit. In a row-normalised influence network, a useful form is:

$$
s_i(t+1)=a_i\sum_j w_{ij}s_j(t)+(1-a_i)s_i(0),
\qquad \sum_j w_{ij}=1.
$$

Here $s_i$ is agent $i$'s numerical stance, $a_i$ is its susceptibility to the weighted opinions it receives, and each row of influence weights sums to one. The weights answer “whose stance enters this agent's update?”, not merely “who has many connections?”.

Consider a toy system with two initial positions, −0.6 and +0.6. Each gives equal weight to itself and the other, and each has susceptibility 0.25. Their social average is zero. After one update, the positions are −0.45 and +0.45: three quarters of each starting position remains. Under these symmetric rules the social average stays zero, so those positions also persist on subsequent updates. The disagreement is not a failure of averaging. It is the consequence of retaining an anchor.

Changing susceptibility to one produces a different system: both positions reach zero in the first update. Calling that outcome a more successful discussion would add a judgement the model has not supplied. Agreement might erase a genuine constraint, while persistent disagreement might represent costs that the proposal never resolved.

| Susceptibility in this two-person example | Starting stances | Stances after one round | Stances after two rounds |
| --- | --- | --- | --- |
| 0.25 for each person | −0.6, +0.6 | −0.45, +0.45 | −0.45, +0.45 |
| 1 for each person | −0.6, +0.6 | 0, 0 | 0, 0 |

<a id="a-network-is-a-hypothesis-about-attention"></a>

## A network is a hypothesis about attention

Influence can be directional. One person may take another's judgement seriously without receiving the same attention in return. Two people with identical susceptibility and starting opinions can move differently because they hear different neighbours.

Take the same starting stances, −0.6 and +0.6, and susceptibility 0.25, but change the influence matrix to:

$$
W=\begin{pmatrix}0.2&0.8\\0.1&0.9\end{pmatrix}.
$$

The first agent's social input is $0.2(-0.6)+0.8(0.6)=0.36$; the second's is $0.1(-0.6)+0.9(0.6)=0.48$. Including their original anchors gives new stances $0.25(0.36)+0.75(-0.6)=-0.36$ and $0.25(0.48)+0.75(0.6)=0.57$. The average has moved to 0.105 even though neither initial view nor susceptibility changed. Directional attention alone broke the symmetry. Later rounds must use these new stances for social input while keeping the original anchors fixed.

In a library-policy rehearsal, a regular visitor might attend closely to someone explaining the booking process, while an occasional visitor gives more weight to a friend who expects access to become difficult. A connection to staff could bring clarification into one part of the network and leave another untouched. The different paths of attention give the same information different reach.

The graph therefore contains substantive assumptions. Giving every agent the same complete discussion creates one exposure pattern; restricting exchanges to selected relationships creates another. The difference is especially important when an objection is locally persistent but absent from the average. The model can make that separation visible, provided the chosen graph is shown rather than hidden behind a persona label.

<a id="some-encounters-do-not-move-either-side"></a>

## Some encounters do not move either side

Bounded-confidence models introduce another mechanism: an exchange changes an opinion only when the participants are sufficiently close under the specified rule. [Weisbuch, Deffuant, Amblard and Nadal](https://arxiv.org/html/cond-mat/0111494v1) analyse continuous opinions updated through binary encounters and the clustering such rules can produce.

For a simple symmetric toy exchange, take positions 0.1 and 0.4, a confidence bound of 0.4 and a compromise coefficient of 0.25. Their distance is 0.3, so the exchange qualifies. Updating both from the positions before the exchange gives:

$$
\begin{aligned}
s'_1 &= 0.1+0.25(0.4-0.1)=0.175,\\
s'_2 &= 0.4+0.25(0.1-0.4)=0.325.
\end{aligned}
$$

The distance halves to 0.15. Positions −0.8 and +0.8 do not move under that same confidence bound. Exposure occurred, but the stipulated mechanism allowed no compromise. Heterogeneous bounds or one-sided updates would be different models, not interchangeable implementations of this example.

**Note**

**A stance coordinate leaves things out.** A numerical distance is only a chosen abstraction. People can reject an argument because of trust, identity, evidence or its consequences, none of which a single stance coordinate fully describes. The toy rule helps explore a particular form of selective influence. It cannot explain a real refusal merely because the refusal resembles its output.

<a id="composing-mechanisms-changes-the-question"></a>

## Composing mechanisms changes the question

An anchored update and a bounded pairwise exchange are distinct operations. Applying the first can bring positions within the second's threshold; applying them in the opposite order may leave that exchange inactive. A composed simulator therefore needs an explicit order and a consistent rule about whether each update sees old or already changed positions.

Take two new illustrative starting positions, −0.4 and +0.4. Keep equal self-and-other weights, susceptibility 0.5, a confidence bound of 0.5 and a compromise coefficient of 0.25. An anchored update brings the positions to −0.2 and +0.2: their social average is zero, and each retains half its original position. Their distance is now 0.4, so the pairwise exchange qualifies and moves them to −0.1 and +0.1.

Reverse the order and the first exchange does nothing: the original distance, 0.8, exceeds the bound. The subsequent anchored update still brings them to −0.2 and +0.2, but there is no further exchange in this round.

![Anchoring before the bounded exchange brings the pair within range; reversing the operations leaves the first exchange inactive and produces different final stances.](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/how-opinions-move/order-comparison.svg)

The exchange acts only when the incoming stances fall within its confidence bound.

| Same toy parameters | After the first operation | After the second operation |
| --- | --- | --- |
| Anchor, then bounded exchange | −0.2, +0.2 | −0.1, +0.1 |
| Bounded exchange, then anchor | −0.4, +0.4 | −0.2, +0.2 |

Both operations use the positions entering that operation, with each pair updated simultaneously. The anchors remain the original −0.4 and +0.4. No random encounter or language-model response changed between the rows. Order alone changed the result. Narrowing the confidence bound to 0.3 would leave the post-anchor distance outside it too, making both orderings finish this first round at −0.2 and +0.2. Thus an apparent interaction between two mechanisms can itself depend on a third parameter. A rehearsal that hides the order cannot explain why a disagreement narrowed.

<a id="two-stance-explorer"></a>

### Change the conditions, keep the anchors

The figure and table use one round with fixed initial anchors, equal influence weights, susceptibility 0.5 and a confidence bound of 0.5. Each exchange moves both agents a quarter of the way towards the other, using their incoming positions; it qualifies when their distance is at or below the chosen bound.

RawFish's proposed drift mechanism also includes asymmetric response to adverse signals, trust decay and a ceiling on per-round movement. Those are additional modelling choices. A coefficient from a study of decisions under gains and losses cannot automatically become a measured rate of opinion change in a policy discussion. A defensible rehearsal can vary such coefficients as declared assumptions without dressing their defaults as population estimates.

The language layer introduces its own interaction. If an agent's prose already changes its stance in response to a message, and a numerical rule then applies another social update, the same influence might be counted twice. The intended numerical state should have a clear role: for example, it determines the stance supplied to the next language-model round through a fixed mapping. Whether the generated response faithfully expresses that supplied stance remains an observable question, not something guaranteed by the mapping's existence.

<a id="what-the-disagreement-can-reveal"></a>

## What the disagreement can reveal

Separating these operations gives [variation across runs](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/variation-inside-a-simulation/) a more precise meaning. A different seed changes which qualifying encounters occur. A different confidence bound changes which encounters can occur. Removing anchoring changes what persists even when everyone sees the same discussion. These are different experiments.

In the library example, an objection that disappears only after every visitor is made highly susceptible suggests a dependence on the simulator's pliability. An objection that survives several plausible exposure patterns may identify a neglected part of the proposal worth discussing with actual visitors. Neither outcome tells us how many people hold the objection. It tells us which account of the interaction made it appear, and gives the next investigation a mechanism to examine.


Reading path: [Systems](https://rawthoughts.in/collections/systems/) > [Rehearsal and evidence](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/) > [How opinions move inside a rehearsal](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/how-opinions-move/)

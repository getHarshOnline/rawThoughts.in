Title: Machine learning is flat!

[Read HTML](https://rawthoughts.in/blog/machine-learning-is-flat/)

Author: Harsh Joshi

<a id="machine-learning-is-flat"></a>

# Machine learning is flat\!

Okay, first things first: the title is not a new theory of geometry.

When I first wrote this in February 2020, I began by asking people to watch Johnny Harris's [*Why People Think the World Is Flat*](https://www.youtube.com/watch?v=IwJzsE8CvzQ). This has nothing and everything to do with that video. My question is about machine learning, explainability and the people trying to regulate a black box. More particularly, it is about the conversation we need to have before we can do any of those things well.

And by conversation, I don't mean throwing mathematics and algorithms at one another. I mean talking about the problem and what would count as a solution. We have a problem. Accepting that is a useful place to start.

<a id="what-do-you-mean-by-that"></a>

## What do you mean by that?

Communication needs some interpretation of a shared vocabulary. Either the machine-learning person learns how to explain the work through the other person's world, or the other person learns enough of the mathematics to enter theirs. Usually, both have some work to do.

An abstraction helps us cross that distance. It leaves things out so we can discuss the part that matters. Trouble starts when we forget what was left out. One person says “the model learned”; another hears “it understands”. One says “accurate”; another hears “I can rely on it in my situation”. We can agree on every word in the sentence and disagree about what it means.

Then our biases helpfully fill the gaps. We build another explanation on the first, borrow another analogy, and carry a small misunderstanding into a much larger claim. Somewhere along the way, a useful simplification becomes an absurdity. The mathematics inside the model may be unchanged throughout. The communication has failed around it.

That is the catch-22: machine learning is already a forest of abstractions. We describe the data through numbers, the learning through an objective and the result through a measure. To explain what happened, we have to carry those abstractions into the vocabulary of someone who needs to make a decision. Merely repeating the technical vocabulary more slowly does not finish the journey.

<a id="showing-the-machinery-helps"></a>

## Showing the machinery helps

Training a model combines mathematical methods with a great deal of experimental judgement: choosing data, testing assumptions and adjusting a system when the first attempt fails. Calling that judgement an art expresses the experience of doing it. It does not put the result beyond scientific investigation.

Visual explanations can give us a way in. What pattern activates a feature? Which part of an image contributed to a classification? What changes when a layer is removed? Work such as Zeiler and Fergus's visualisation of convolutional networks made some of those questions concrete.<sup><a id="fnref-note-76697375616c69736174696f6e"></a>[1](#fn-note-76697375616c69736174696f6e)</sup> Other methods, such as LIME, approximate a model's behaviour around a particular prediction to provide a more interpretable local account.<sup><a id="fnref-note-6c696d65"></a>[2](#fn-note-6c696d65)</sup>

Andrej Karpathy's explanations and the TensorFlow Playground were accessible entrances to this world. A reader could follow a sequence through a network, or change a small network and watch its learned boundary move.<sup><a id="fnref-note-7465616368696e67"></a>[3](#fn-note-7465616368696e67)</sup> That matters to communication: an abstraction becomes something we can examine together, rather than another word one side is expected to accept.

None of these turns every learned system into a fully explained one. A local approximation is local. A picture of a feature is not a complete account of why a decision is appropriate for this person. But these are ways of replacing “trust the maths” with something another person can inspect and question.

There is also a distinction between a system performing well on a task and our having a satisfactory explanation of it. We can measure a useful result without yet understanding every internal mechanism. We can also understand an algorithm and still deploy it in the wrong situation. “It cannot explain itself, therefore it cannot work” misses the first point. “It works on our test, therefore you should accept it” misses the second.

<a id="there-are-people-on-the-other-side"></a>

## There are people on the other side

I have witnessed the fear of being automated in the energy and agriculture sectors. It is easy to stand beside a good demonstration and dismiss that fear as a misunderstanding. It is harder to ask what the person actually expects to lose, and whether our explanation addresses it.

At the time, I did not expect humans to be completely automated. I expected people to be augmented by their silicon counterparts, with more room to investigate, create and understand. That expectation was not an answer to every person's concern about their livelihood. Fear and belief are powerful forces; a technical conversation that ignores them will not remain technical for long.

This is where we need to separate questions that have been bundled together. What can the system do? What evidence supports that claim? Who benefits from using it? Who bears the cost of a mistake? What future do we want? An explanation of a neural network can contribute to that discussion. It cannot settle all of it.

<a id="two-different-clocks"></a>

## Two different clocks

Even the people building these systems struggle to keep up. There is another paper, another result, another approach that makes last month's limitation look smaller. Objects in the mirror are closer than they appear.

Regulation moves through a different process. It has to consider people who did not choose the experiment, consequences outside the benchmark and rules that can be applied consistently. Due diligence takes time. A fast research cycle and a slower institutional response are a difficult combination, especially when the public conversation mixes measured results, speculative futures and conspiracy theories into one alarming story.

I don't have a complete solution to that. Pretending the research has stopped until the vocabulary catches up will not help. Neither will treating every objection as evidence that the speaker has failed to understand the science.

Both sides need to recognise the communication problem. The people developing the systems have to make their evidence and its limits intelligible. The people questioning them need to distinguish what the evidence says from what they fear or hope it might eventually mean. Philosophical possibilities deserve discussion; the decision about a particular use needs a sufficiently concrete account of that use.

That is why I began with the flat-Earth conversation. Scientific evidence does not become irrelevant because it is difficult to communicate. Difficulty communicating it is a reason to work harder at the explanation, without losing sight of what the scientific community has actually established.

1. 
   
   <a id="fn-note-76697375616c69736174696f6e"></a>
   
   Matthew Zeiler and Rob Fergus, [*Visualizing and Understanding Convolutional Networks*](https://arxiv.org/abs/1311.2901), 2013. The paper investigates intermediate features and the contribution of layers to a classifier. It is one example from the interpretability work that predates this essay, rather than a claim that visualisation began with one researcher. [↩](#fnref-note-76697375616c69736174696f6e)

2. 
   
   <a id="fn-note-6c696d65"></a>
   
   Marco Tulio Ribeiro, Sameer Singh and Carlos Guestrin, [*“Why Should I Trust You?”: Explaining the Predictions of Any Classifier*](https://arxiv.org/abs/1602.04938), 2016. Its explanations approximate behaviour near a selected prediction; they do not supply a universal account of the model or a decision's social legitimacy. [↩](#fnref-note-6c696d65)

3. 
   
   <a id="fn-note-7465616368696e67"></a>
   
   Andrej Karpathy, [*The Unreasonable Effectiveness of Recurrent Neural Networks*](https://karpathy.github.io/2015/05/21/rnn-effectiveness/), 2015; Daniel Smilkov and Shan Carter's [TensorFlow Playground](https://playground.tensorflow.org/), which credits Karpathy's ConvNetJS demonstration and Chris Olah's writing among its predecessors. These are examples of visual teaching, not the first or only work on interpretability. [↩](#fnref-note-7465616368696e67)

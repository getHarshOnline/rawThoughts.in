Title: The autocorrect paradox

[Read HTML](https://rawthoughts.in/blog/the-autocorrect-paradox/)

Author: Harsh Joshi

<a id="the-autocorrect-paradox"></a>

# The autocorrect paradox

Time has a weird sense of humour. Its cruelty makes prediction harder. And, as usual, what follows wanders through AI, causality and economics.

Let's begin by admitting that FOMO in this field is real. Its scale is distorted, like almost everything else around AI. I wrote this at the end of 2023, the year that made AI cool again. The expectations below belong to that moment: a decade of work behind me, and a particularly loud year ahead.

I started working with machine learning in 2012, as an Electronics and Communication Engineering undergraduate. Digital signal processing, and more particularly digital image processing and computer vision, were my way into it. We were beginning to see flashes of what the field might become. ImageNet and AlexNet made that possibility much harder to ignore.<sup><a id="fnref-note-616c65786e6574"></a>[1](#fn-note-616c65786e6574)</sup>

And if you don't know what OpenAI is, good morning\! It's the end of 2023 now. The world's a bit different today, but the little things are the same as ever. :)

Then came the race. Architectures, models, datasets and infrastructure changed in front of us. My own work passed through agriculture, energy efficiency, education, emergency response, wellness and finance. I built products, teams and solutions. Some survived, some changed, and some didn't. My entrepreneurial journey developed alongside the technology, to the point that I couldn't keep up with this shit any more. But I still tried.

And thank God, it was finally cool again.

From AlexNet to GPT-4, the architectures had come a long way. But there was a recurring part of the work. I'll get to it. Wait.

<a id="a-playground-with-a-much-larger-entrance"></a>

## A playground with a much larger entrance

I remember the reinforcement-learning experiments around OpenAI Gym: environments in which we could watch an agent learn by trying things and receiving a reward. TensorFlow and game-development tools gave more people ways to experiment. The playground kept growing.<sup><a id="fnref-note-67796d"></a>[2](#fn-note-67796d)</sup>

The Transformer came from a different line of work, sequence modelling, with the 2017 *Attention Is All You Need* paper. OpenAI built its GPT work on that family of architectures and put extraordinary amounts of capital, talent and data into developing it.<sup><a id="fnref-note-7472616e73666f726d6572"></a>[3](#fn-note-7472616e73666f726d6572)</sup> The history is more interesting than one invention producing the next in a straight line. The product consequence was simpler: the playground became accessible to people who could type a request.

You could even argue that English had become 2023's most popular programming language. You no longer needed to begin by installing a research environment.

Calling the result a fancy autocomplete can sound dismissive. I don't mean it that way. Predicting a continuation at this scale produced a remarkable range of behaviour. The engineering achievement was enormous. Pre-training supplied broad capabilities; subsequent instruction training and human feedback helped turn those capabilities towards what people were trying to ask.<sup><a id="fnref-note-61646170746174696f6e"></a>[4](#fn-note-61646170746174696f6e)</sup> They are different stages, and the chat experience depended on more than simply choosing an architecture.

<a id="almost-there-again"></a>

## Almost there. Again.

Here is the recurring part: making the system fit the task.

Across a decade of projects, the relevant data, the training choices and the adaptation kept mattering. “Fine-tuning” names one particular form of that work, further training an existing model. It is not a catch-all for everything done to a model, and it is not the sole reason a system succeeds. But the distance between a generally impressive model and one that behaves usefully in a particular setting kept bringing me back to it.

The model gets almost accurate enough. Almost consistent enough. Almost ready for the person who isn't prepared to spend their day fixing its output. Another improvement moves the boundary, and a new application immediately asks something harder of it.

That is my autocorrect paradox. Always almost intelligent, never quite finished with the last awkward part. A system can be useful before it is perfect. The problem is what it costs to close the remaining gap, and whether the operation around it can live with the errors left over.

By the end of 2023, that limbo was wearing a very fancy dress: trillion-dollar markets and billion-dollar valuations. Underneath were diminishing returns: more infrastructure and operational effort to close the next gap in accuracy. As a society, we are rather good at turning a problem into a newer, fancier problem. Sometimes we even call that solving it.

Looking into 2024, I expected further gains in accuracy, but also systems learning to work with an error-prone AI rather than waiting for perfect accuracy and consistency. The practice round was over; the field was warming up for the big leagues. That adjustment would put pressure on five connected parts of the industry.

<a id="show-me-the-money"></a>

## Show me the money\!

You cannot burn an indefinite amount of capital running a fancy autocomplete. Somewhere, somebody has to explain why the result is worth the bill.

I expected that pressure to favour efficient models and more deliberate adaptation. A smaller general capability, made good at the task that actually earns its place, could be a better investment than paying for the largest model on every request. The comparison has to include the work that succeeds, the retries and the people correcting the failures. A low price per token is a small part of that calculation.

The “autocompletion tax” was my name for the feeling that every extra interaction brought another charge whose relationship to useful work was difficult to see. The answer was not necessarily to avoid an API. It was to make the economics intelligible enough to choose. Capital spent understanding the task and preparing good adaptation data could buy something a larger inference bill would not.

<a id="talk-to-me-like-i-m-five-years-old"></a>

## Talk to me like I'm five years old\!

As the stakes rose, I expected people to become less willing to pretend they understood what a system was doing or how long it would take.

That creates pressure for observation, explanation and control. Show the work. Explain the failure in terms the person running the operation can recognise. Give them a way to change the relevant part. A reassuring paragraph generated by the same model is not enough to establish why its answer occurred.

This was an engineering opportunity as well as a research problem. A system whose work could be understood would be easier to improve and easier to trust with a consequential task. The question was what kind of explanation would let the responsible person act, rather than merely admire a diagram.

<a id="get-your-basics-right"></a>

## Get your basics right\!

Fixing a broken process with AI gives you a broken AI-driven process.

Take a thought experiment: can you write an objective definition of morality that your five closest friends will all accept? Even that small group may discover assumptions it has never had to articulate. Now imagine asking a model to resolve the organisation's undefined exceptions while everyone confidently calls them “the policy”.

Some failures belong to the model. Others reveal a gap in how we have specified the work. If the people responsible cannot say what should happen in a case, the model has not been given a clear decision merely because the request arrived in a polished prompt.

That does not mean every process can be reduced to exhaustive rules, or that a clearer document eliminates hallucination. It means the business has to own its choices. Skip a few of the PowerPoints. Get to the one-pagers that say what we do, why we do it and where a person needs to decide. A win for the process and operations nerds, finally.

<a id="separation-of-church-and-state"></a>

## Separation of church and state

I expected organisations to become clearer about three different jobs: research, fine-tuning and deployment.

Research explores what a model or method can do. Adaptation brings a selected capability towards a particular task. Deployment keeps the resulting application available and usable. These activities inform one another, but they need different experiments, different measures and often different people.

The tooling around deployment was already drawing attention. I expected more investment in adaptation: collecting useful feedback, preparing datasets, comparing candidate versions and deciding whether the new one actually improved the intended work. Versioning and A/B tests would give the improvement an observable shape. A thumbs-up counter by itself would not.

My 80:20 intuition was that a large share of practical success would come from doing this less spectacular work well. A company did not have to make an architectural breakthrough before learning to use what existed.

I also expected more specialised models and better ways of combining them: a cocktail of intelligence, if you will. The combination needs an application that knows which contribution is appropriate and how to deal with disagreement. Pouring several models into the same glass does not do that for us.

<a id="and-of-course-fomo"></a>

## And, of course, FOMO

Anyone who was anyone would try putting AI in X. Some of the combinations would resemble ideas from beer conversations years earlier, finally made feasible by a new capability. Most would still need a useful measure of whether anybody benefited.

My particular bet was on products with a tangible device or experience, with local models playing a large role in consumer adoption. I expected that to make profiling, latency measurement and optimisation more valuable. The software would have to fit the thing people carried or used, not just perform on an engineer's demonstration machine.

A local model would still face the same pressure as the other four: useful work has to survive contact with cost, delay, context and ordinary human expectations.

<a id="better-tools-under-the-hood"></a>

## Better tools under the hood

These pressures pointed towards engineering and productisation that could sustain the field. They also returned me to a deeper question: can we articulate the relationships a model has learned well enough to know what an intervention will change? A useful statistical association and a causal account are not interchangeable. Better tools should help us examine that difference rather than conceal it beneath a more fluent answer.

Data quality, feedback and deliberate adaptation were where I expected much of the practical work to land. [From a model answer to a useful product](https://getharsh.in/blog/an-ai-product-is-more-than-a-model/) follows the related product decision: what complete job are we promising the person who uses it?

The autocorrect paradox is not a reason to stop. It is a reason to notice what keeps returning. The demonstration gets better, the expectations move, and the work around the model still needs doing. Time has a weird sense of humour.

1. 
   
   <a id="fn-note-616c65786e6574"></a>
   
   Alex Krizhevsky, Ilya Sutskever and Geoffrey Hinton, [*ImageNet Classification with Deep Convolutional Neural Networks*](https://papers.nips.cc/paper_files/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf), 2012. Its classification result is a milestone in this account, not the beginning of machine learning. [↩](#fnref-note-616c65786e6574)

2. 
   
   <a id="fn-note-67796d"></a>
   
   Greg Brockman and colleagues, [*OpenAI Gym*](https://arxiv.org/abs/1606.01540), 2016, describes a common interface to reinforcement-learning benchmark environments. It is distinct from the later Transformer architecture. [↩](#fnref-note-67796d)

3. 
   
   <a id="fn-note-7472616e73666f726d6572"></a>
   
   Ashish Vaswani and colleagues, [*Attention Is All You Need*](https://arxiv.org/abs/1706.03762), 2017; Alec Radford and colleagues, [*Improving Language Understanding by Generative Pre-Training*](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf), 2018. The latter combines generative pre-training and task-specific fine-tuning. [↩](#fnref-note-7472616e73666f726d6572)

4. 
   
   <a id="fn-note-61646170746174696f6e"></a>
   
   Long Ouyang and colleagues, [*Training language models to follow instructions with human feedback*](https://arxiv.org/abs/2203.02155), 2022, describes supervised demonstrations and reinforcement learning from ranked outputs. Its results support the importance of adaptation; they do not establish that fine-tuning accounts for a fixed percentage of every AI product's success. [↩](#fnref-note-61646170746174696f6e)

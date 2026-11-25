Title: AI 101

[Read HTML](https://rawthoughts.in/blog/ai-101/)

Author: Harsh Joshi

<a id="ai-101"></a>

# AI 101

What is artificial intelligence? Why is everyone so excited about it? And if it is this magical, why does getting it to do one ordinary job still involve so much work?

Let's start with the machinery. I wrote this introduction in June 2024, when every software product seemed to be acquiring a copilot. Follow a request through an application and the terms begin to make sense: what does the model do, what surrounds it, and where can we reach the work to improve it? Those questions also led us to build YOJN.

<a id="what-are-we-calling-intelligence"></a>

## What are we calling intelligence?

AI is a broad field concerned with making machines perform tasks associated with intelligence: recognising patterns, reasoning, planning, communicating and acting. It includes more than one way of doing that.

Suppose a process has a hundred rules. You can write routines that say, “If this condition holds, do that.” An expert system can represent knowledge through such rules and reason with them. But as the exceptions accumulate, maintaining all the combinations becomes a serious job. Can the system learn something from examples instead of requiring us to specify every distinction ourselves?

That is the attraction of machine learning. It is not a technology that suddenly replaced rules in the 1990s: learning systems and rule-based systems have long, overlapping histories. Arthur Samuel was already publishing work on learning to play checkers in 1959.<sup><a id="fnref-note-686973746f7279"></a>[1](#fn-note-686973746f7279)</sup> They also coexist inside ordinary applications. A learned model may recognise the request; a written rule may decide whether the account is permitted to act on it.

A decision tree gives us one way of learning a set of distinctions from data. A small tree can be easy to follow. Other models represent the problem differently, and the trade-offs depend on the task. Neural networks are a particularly flexible family. Their terminology borrows from brains, but they are mathematical systems, not miniature biological brains running inside a computer.

<a id="start-with-a-curve-in-a-spreadsheet"></a>

## Start with a curve in a spreadsheet

You have some data in a spreadsheet and fit a line through it. Given another input, the line supplies an estimated output. You have a model.

For a tiny invented example, take the observations $(0,1)$, $(1,3)$ and $(2,5)$. The rule $y = 2x + 1$ fits all three. Put in $x = 3$ and it predicts $7$. Easy enough.

But another curve can fit those same observations and predict something else at three. The data did not uniquely determine everything the model will do beyond it. The choice of model and the assumptions behind fitting it matter.

![Two curves pass through the same three observations but predict different values beyond the observed range.](https://rawthoughts.in/blog/ai-101/fitting-curves-light.svg)

Both curves fit the three invented observations exactly. The straight line is $2x+1$; the alternative adds $0.2x(x-1)(x-2)$, which is zero at each observed input. At $x=3$, their predictions are $7$ and $8.2$.

A neural network is also a function with adjustable parameters, usually called weights. Training changes those parameters to improve an objective on examples. Layers let the network build complex transformations, often over far more dimensions than we can draw on a sheet of paper. For classification, the result can define boundaries between categories. For other tasks it might predict a number or the probabilities of possible next tokens.

This is what I mean by a function approximator. It gives us a useful starting point without pretending the entire subject is a spreadsheet trendline. The important question is how well the learned function behaves on the cases we actually need, including ones it has not seen before.

<a id="from-recognising-things-to-generating-them"></a>

## From recognising things to generating them

An email filter learns patterns associated with spam. A recommendation system uses patterns in interactions to suggest something a person might want. These are different tasks, with different data and objectives, but both make use of regularities in examples.

A colour photograph can be represented as a grid with red, green and blue values at each pixel. To the model, the input begins as numbers. A learned representation can make patterns in those numbers useful for identifying a nose, an ice-cream cone or a face. It does not begin with our everyday vocabulary already attached to every pixel.

Generative models learn patterns that let them produce new outputs: text, images, audio and other forms. Classification and generation are related, but a good classifier does not automatically become a good generator. They may need different architectures, objectives and training procedures.

The excitement after 2022 came partly from how accessible generation became. People could ask for a draft, a picture or a piece of code and receive something they could immediately inspect and use. A capability previously encountered through specialist software became an entrance to many kinds of work.

That is real economic possibility. It also raises the next question: does the generated thing actually satisfy the task? Producing a plausible answer is not evidence that all the decisions required for the job were made correctly. The distinction is where much of the engineering begins.

<a id="what-are-llms-and-gpts"></a>

## What are LLMs and GPTs?

A language model assigns probabilities to sequences of tokens. A token may represent a word, part of a word, punctuation or another unit chosen by the tokenizer. It is a close relative of “word” for a first explanation, but the difference matters when you count context or cost.

An autoregressive language model generates by repeatedly selecting a next token from the distribution it computes for the preceding context. The choice becomes part of the context for the next step. A large language model applies this sort of language modelling at scale; different model families organise the computation differently.

GPT expands to *Generative Pre-trained Transformer*. The Transformer architecture was introduced in 2017. Its attention mechanism lets representations draw on other positions in a sequence. GPT uses a decoder-style Transformer to predict continuations, rather than being the encoder side of the original encoder–decoder design.<sup><a id="fnref-note-7472616e73666f726d657273"></a>[2](#fn-note-7472616e73666f726d657273)</sup>

Pre-training develops broad capability from a large body of data. Later training can adapt how a model responds to instructions or particular tasks. The architecture, pre-training and later adaptation all contribute; the letters in the name are not a recipe that makes any chat system reliable.

<a id="and-diffusion-models"></a>

## And diffusion models?

Diffusion takes another route to generation. During training, noise is added to examples, and a model learns how to reverse that corruption. Generation can then begin with noise and use learned denoising steps to produce a sample, often conditioned on something such as a text prompt.<sup><a id="fnref-note-646966667573696f6e"></a>[3](#fn-note-646966667573696f6e)</sup>

That is different from the generator-versus-discriminator contest used in a generative adversarial network, or GAN. It is also different from choosing one next token at a time. These are ways of organising a generative problem, rather than three names for the same mechanism.

The broad attraction is familiar: learn enough structure from the data to make something new. Whether the new thing has the right fingers, the intended words or continuity with the previous video frame is a further question. A method for generating an image does not supply a guarantee about every detail in it.

<a id="what-are-agents"></a>

## What are agents?

An AI application can call a model once and return the answer. It can also place the model inside a larger operation: inspect a request, choose a tool, examine what came back and decide what to do next. “Agent” is commonly used for systems in that latter territory, although people use the word at different levels of ambition.

An agent is not another kind of neural network by definition. It is an arrangement of model calls, state, tools and control over what happens next. Some workflows prescribe the steps in advance. Others let a model choose among allowed actions. More freedom changes what the application has to check; it does not automatically make it more useful.

Think of an operating system coordinating processes, memory and access to resources. An agent framework coordinates activities, their context and their access to tools. We still have to check what those activities produce and what happens when one fails.

<a id="where-retrieval-and-memory-fit"></a>

## Where retrieval and memory fit

RAG stands for *retrieval-augmented generation*. The application retrieves information and provides it to the model as part of the material it can use when generating an answer.<sup><a id="fnref-note-726167"></a>[4](#fn-note-726167)</sup> The information might be a product manual, a policy or a record that was never included in the model's training.

In the OS analogy, retrieval is a little like bringing information in through input/output, while the model's context is a kind of working space. Neither is a perfect equivalence. A context window is not a general-purpose memory store, and placing a document in it does not update the model's weights.

Imagine asking which payment terms apply to a purchase. The application first needs the relevant agreement and version. It may retrieve passages, ask a model to interpret them, then check or present the answer. The retrieval can select the wrong agreement. The interpretation can be wrong even when the right passage arrives. Each step has a job, and each can fail in a different way.

An orchestrator keeps those steps together. It might invoke several agents or just ordinary software functions. It may summarise information to fit the context, which creates another choice about what gets left out. The result can feel like one instantaneous act of intelligence to the person using it. Underneath, there is work being coordinated, sometimes with substantial delays and dependencies.

<a id="what-is-prompt-engineering"></a>

## What is prompt engineering?

It is the work of giving a model instructions, context and examples that help it produce the intended behaviour.

“Give me the answer as a Markdown table with these three columns” is more specific than “make it readable”. A relevant example can clarify what belongs in a column. A request to identify missing information can be better than quietly encouraging the model to fill every gap.

The effect depends on the model and the task. “Markdown” is not a magic word that activates a known table-making compartment. If a particular format matters, the application can validate it and handle a failure. A prompt is part of that arrangement, not a substitute for the checks.

In 2024 I wondered whether prompt engineering as a separate profession might disappear as quickly as it had appeared. Predictions here are wobbly. The more durable problem is communicating the task clearly enough and checking whether the system did it.

<a id="what-are-vector-embeddings"></a>

## What are vector embeddings?

Think of a graph with two coordinates, date and revenue. A point gives you two numbers. A vector is a list of numbers; it can have two entries or many more.

An embedding maps an object, such as a token, passage or image, to such a vector. Learning can arrange that space so that some relationships in the data become useful relationships between vectors.<sup><a id="fnref-note-656d62656464696e6773"></a>[5](#fn-note-656d62656464696e6773)</sup> Then an application can compare representations to retrieve related passages or recognise similar images.

The dimensions do not necessarily have convenient labels such as “nose”, “colour” and “trustworthiness”. Nor does every embedding have the same number of dimensions. The representation and the distance measure are part of a particular model and task.

My nose and your nose might land near one another in a space useful for recognising noses. If horse poop lands nearby too, I would quite reasonably question whether we had learned the distinction we needed. There is no universal distance of `0.00001` at which a model decides those things are equivalent. The point is that closeness in a learned representation is not the same as a human judgement that two things should be treated alike.

The model operates on the representation it has. Our job includes testing whether that representation preserves what the use requires.

<a id="the-demonstration-worked-what-is-mlops-for"></a>

## The demonstration worked. What is MLOps for?

There is a considerable distance between the engineer's laptop in the boardroom and customers using the system every day.

MLOps concerns the practices and infrastructure for developing, deploying, monitoring and maintaining machine-learning systems.<sup><a id="fnref-note-6d6c6f7073"></a>[6](#fn-note-6d6c6f7073)</sup> The work includes data and model versions, evaluations, serving, reliability and the changes needed when the world or the data changes. It draws on software operations while adding the particular problems of learned models.

“AIOps” is often used for applying AI to IT operations, so I would not use the two terms interchangeably. For this discussion, we are concerned with operating the AI application itself.

Cost, latency, security and recovery all become part of the product. The model may answer correctly when everything is available and still leave the customer stuck when a source is missing. [The product around the model](https://getharsh.in/blog/an-ai-product-is-more-than-a-model/) (on getHarsh) has to decide what happens then.

<a id="can-we-see-it-explain-it-and-control-it"></a>

## Can we see it, explain it and control it?

Observability asks what we can learn about the running system from its outputs and measurements. Which request used which model and source? Where did the delay occur? What did the tool return, and what did the operation cost?

Explainability asks a different question: what account helps us understand the behaviour or decision? A trace records steps. It may not tell a domain expert why the wrong agreement was selected or why a proposed answer is justified. A model's own explanation is another output to assess, not privileged access to the actual cause of its answer.

Controllability concerns what we can deliberately influence: permitted actions, available information, selected versions, checks and interventions. Alignment addresses whether behaviour follows the goals and constraints it is intended to serve. These are related fields, each much larger than this paragraph. Seeing the work helps us investigate it; an explanation helps us judge it; a control gives that judgement somewhere to go.

There is a useful technical distinction here. A neural network can compute a repeatable output under fixed inputs and execution conditions. Sampling can introduce variability, and changing context or tools can change the result. But even a perfectly repeatable answer can be wrong. Reliability is not solved merely by making the system say the same thing twice.

<a id="fine-tuning-science-or-art"></a>

## Fine-tuning: science, or art?

Pure art, obviously. Just kidding.

Suppose a pre-trained model has useful general capability but struggles with the task's specialised language or expected responses. Fine-tuning continues training from that model using examples and objectives chosen for the adaptation.

It need not change only the top few layers. Full fine-tuning can update all trainable weights; parameter-efficient methods update a smaller set or add a limited adaptation. LoRA, for example, keeps the original weights fixed while learning low-rank updates.<sup><a id="fnref-note-6c6f7261"></a>[7](#fn-note-6c6f7261)</sup> Changing a prompt is not the same operation as changing weights.

The practical judgement is in preparing representative examples, choosing what to optimise and deciding what counts as improvement. You try something, inspect the results, double down or change direction. A subject expert may notice that the answer uses the wrong definition even when a general quality score looks healthy.

That feedback has to become something useful: a corrected example, a clearer source, a changed evaluation or a candidate training run. It does not mean every correction should immediately retrain the model or replace the version serving customers. Test the candidate against the failures that motivated it and the behaviour worth preserving. The art is in the judgement; the comparison still needs evidence.

<a id="the-piece-of-the-model-i-actually-need"></a>

## The piece of the model I actually need

This is the question that most interested me: decomposability.

Ordinary software gives us functions and modules with interfaces. We can reuse one routine without bringing the whole application along. A model exposes components too, but a useful learned capability does not necessarily line up with one neatly removable component. Knowing how to call the model is different from knowing which internal part to extract for a particular skill.

Imagine dissecting a brain, finding “what he ate for breakfast”, and transferring that bit to someone else. Now they remember a samosa. Or we adjust it and give them a pineapple. A ridiculous picture, but it catches what is missing from the simple idea that we can take a model's useful knowledge apart as easily as a software library.

Pruning, adapters, specialised experts and other forms of modular design offer ways to work with parts of models. They do not amount to a universal method for isolating any semantic capability and transferring it while everything else remains unchanged. That stronger question is what I was getting at with the “0 or 1” complaint: so often, the usable interface gives you the whole model's behaviour when you want one intelligible part.

The distinction matters for explanation, reuse and quality assurance. If we cannot confidently locate the behaviour we want to change, we also have more work to do when checking what else a change affected.

<a id="why-isn-t-it-doing-every-job-already"></a>

## Why isn't it doing every job already?

Compute and skilled work can be expensive. Even after paying for them, we still need quality assurance.

The maddening experience is a system that appears to understand the task beautifully and then fails in a way no one anticipated. Think of a hyperactive five-year-old: good luck figuring out why that particular power socket was so interesting.

You really don't want your AI front desk telling a customer to go fuck themselves\! An exaggeration, of course, but an incorrect promise made in perfectly polite language can cause plenty of trouble too. A leveraged-buyout model with a subtly wrong assumption creates a different risk again. The presence of a chat box cannot decide what evidence is enough for either use.

This is why I kept returning to explanation and control. We need to know what can go wrong, which checks catch it and where a person can intervene. A good demonstration can reveal a possibility. Daily use requires an arrangement that can carry the consequences. There are useful applications before every research problem is solved; there are also tasks for which the remaining errors matter too much to ignore.

<a id="why-all-the-excitement-about-open-models"></a>

## Why all the excitement about open models?

When model weights and tools are available, more people can experiment, adapt and build. Hugging Face helped make that activity easier to find and share. The analogy to GitHub is useful: a place where work becomes accessible to others, rather than an isolated result behind one interface.

But “open” needs care. Available weights, source code, training information and permitted uses are different dimensions. Mistral's original 7B release used Apache 2.0; other model releases use their own terms.<sup><a id="fnref-note-6f70656e2d6d6f64656c73"></a>[8](#fn-note-6f70656e2d6d6f64656c73)</sup> A downloadable file does not automatically make every model an open-source project in the same sense.

My economic reading in 2024 was that this was more than generosity. Compute, talent and data require capital and distribution. A company that reaches more users can gain more opportunities to improve its product and finance the next round. Open releases can be a way for other participants to weaken dependence on a dominant provider and build a different position in that market.

The rebel alliance, if I may get dramatic for a moment. Why should the incumbent get to own everything? Releasing a useful model can serve a business strategy and help a wider community at the same time.

The stakes are larger than winning a benchmark. The question is who supplies the systems through which people will work and consume, and how easily others can build an alternative.

<a id="what-does-the-enterprise-have-to-run"></a>

## What does the enterprise have to run?

One route is to use a hosted model API. The provider operates the model; the application concentrates on the experience and the work around it. Another is to run a model whose weights are available, or develop one. That gives the team different control and different operating obligations. Applications can also combine these routes.

In either case, someone still maintains the configuration, sources, access, checks and feedback. An orchestration framework can help organise that work. Merely placing a model inside an “agent” does not give it a learning process or prove that its actions are safe.

This brings the subject expert back into the picture. They may recognise the mistake immediately, while the engineering team has to work out which source, step or model behaviour produced it. The useful system lets those contributions meet. Better tokens and feedback matter because they carry relevant information; data quality does not make architecture, access control or careful evaluation disappear.

<a id="our-attempt-with-yojn"></a>

## Our attempt with YOJN

At DAO Studio we built [YojnAI](https://daostudio.in/yojnai/) (on DAO Studio) around that problem: compose an application, inspect its intermediate work and let feedback inform a deliberate improvement. Agents combined models and tools; checked playbooks arranged their work; an application supplied the organisation's connections and context.

The design associated traces and feedback with particular agents and versions. It paired model snapshots and improvement work with ways for a domain expert to inspect a step, explain what was wrong and compare a candidate change. That was our practical approach to making the application more decomposable. It did not extract a self-contained skill from arbitrary neural weights or solve the stronger research question above.

Callbacks and retained intermediate state mattered because the person needed to reach the work while it was happening, rather than receive only a final answer. If one part needed correction, the useful information from another part should remain available. The public [composition account](https://daostudio.in/yojnai/compose-inspect-and-improve/) (on DAO Studio) develops that mechanism, and [the review walkthrough](https://daostudio.in/yojnai/review-a-disputed-answer/) (on DAO Studio) follows a disputed result into an improvement decision.

The aim was to explain enough of the operation to the person who knew the subject. They should not have to learn the mathematics of the model before pointing out that it had used the wrong payment term. Evaluation and version choice were intended to make that correction more useful than a complaint collected in a log.

For the finance team funding the application, the related question was what the improvement bought. Consider the illustration of roughly $1.70 an hour of compute for a smaller adapted model rather than paying for a much larger one.

**Note**

**The conditions behind the cost.** That historical figure is not a current hosting quote or a like-for-like cost benchmark. Request length, throughput, hardware, quality and operating work determine the actual comparison. Self-hosting also leaves real infrastructure and service costs; the absence of a per-token API bill does not make use free.

The intended shift was to spend more effectively on the people and evidence that improved the task, with a clearer view of what the compute was doing. [Where the application and its data actually run](https://daostudio.in/blog/follow-the-data/) (on DAO Studio) remains a separate part of that choice.

<a id="the-8086-era-of-ai"></a>

## The 8086 era of AI

My expectation in June 2024 was that many constraints we were carefully engineering around would become much less important as the technology improved. The computer analogy was the 8086 era: limitations that once shaped an entire application can later become small enough to forget.

Retrieval, for example, helps an application select useful information within context and cost constraints. Larger context alone would not settle source quality or access, but it could change some of the trade-offs that made a particular retrieval arrangement attractive.

Imagine a thousandfold efficiency improvement allowing a model a hundred times larger to use a tenth of the resources. Under a simple proportional model, the arithmetic is $100 / 1{,}000 = 0.1$. That calculation describes the possibility I had in mind; it is not a measured gain, a timetable or a guarantee that latency follows the same ratio.

I expected some AI services eventually to feel free to the user, as search and social media often do, with other business models paying for them. Useful capability would become easier to obtain, while distinctive data about the problem could become more valuable. New policies and energy demands would follow the changing use.

Then come the stranger possibilities: specialised AI personas, systems finding and commissioning one another, something like Fiverr or Amazon with AI on the requesting side. Their practical demands are substantial. A medical adviser, a plumber's assistant and a robot doing physical work need very different evidence and capabilities; robotics does not reduce to manufacturing merely because conversation has improved.

My larger expectation was that progress on decomposability would eventually let us trade and combine useful intelligence more directly. That remains a research and product ambition, distinct from calling a few APIs in sequence. It is the question underneath the vocabulary: can the useful thing the system has learned become something another person can understand, improve and build with?

1. 
   
   <a id="fn-note-686973746f7279"></a>
   
   IBM's [account of its early game-playing research](https://www.ibm.com/history/early-games) describes Samuel's checkers work. Machine learning was already an established research term decades before the 1990s; rule-based and learned approaches are not consecutive, mutually exclusive eras. [↩](#fnref-note-686973746f7279)

2. 
   
   <a id="fn-note-7472616e73666f726d657273"></a>
   
   Vaswani and colleagues, [*Attention Is All You Need*](https://arxiv.org/abs/1706.03762), 2017; Radford and colleagues, [*Improving Language Understanding by Generative Pre-Training*](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf), 2018. The latter explicitly uses a multi-layer Transformer decoder for its language model. [↩](#fnref-note-7472616e73666f726d657273)

3. 
   
   <a id="fn-note-646966667573696f6e"></a>
   
   Sohl-Dickstein and colleagues, [*Deep Unsupervised Learning using Nonequilibrium Thermodynamics*](https://arxiv.org/abs/1503.03585), 2015; Ho, Jain and Abbeel, [*Denoising Diffusion Probabilistic Models*](https://arxiv.org/abs/2006.11239), 2020. These describe diffusion and learned reverse processes, rather than the adversarial training contest of GANs. [↩](#fnref-note-646966667573696f6e)

4. 
   
   <a id="fn-note-726167"></a>
   
   Lewis and colleagues, [*Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*](https://arxiv.org/abs/2005.11401), 2020, combines a trained generator with retrieved passages. Retrieval adds usable context; it does not itself establish that the passage or generated answer is correct. [↩](#fnref-note-726167)

5. 
   
   <a id="fn-note-656d62656464696e6773"></a>
   
   Mikolov and colleagues, [*Efficient Estimation of Word Representations in Vector Space*](https://arxiv.org/abs/1301.3781), 2013, is a foundational example of learned word vectors. Different embedding models and tasks use different representations; a coordinate has no universal human meaning. [↩](#fnref-note-656d62656464696e6773)

6. 
   
   <a id="fn-note-6d6c6f7073"></a>
   
   Google Cloud's [*MLOps: Continuous delivery and automation pipelines in machine learning*](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning) describes the development, evaluation, deployment and operational work around models. [↩](#fnref-note-6d6c6f7073)

7. 
   
   <a id="fn-note-6c6f7261"></a>
   
   Hu and colleagues, [*LoRA: Low-Rank Adaptation of Large Language Models*](https://arxiv.org/abs/2106.09685), 2021. Its smaller trainable updates are one adaptation method; fine-tuning as a category is not restricted to a model's final layers. [↩](#fnref-note-6c6f7261)

8. 
   
   <a id="fn-note-6f70656e2d6d6f64656c73"></a>
   
   Mistral's [September 2023 release announcement](https://mistral.ai/news/announcing-mistral-7b/) identifies the original Mistral 7B licence as Apache 2.0. The statement concerns that release, not every model subsequently published by the company. [↩](#fnref-note-6f70656e2d6d6f64656c73)

---
layout: blog
title: Language Models, World Models, and Human Model-Building
---

# Language Models, World Models, and Human Model-Building

<i>Jacob Andreas <br>
26 July 2024</i>

Does the computation performed by language models involve real language
understanding, or just string manipulation?

When the first really high-quality neural language models first appeared, this
Big Question was mainly formulated in terms of whether LMs could represent
**meaning**. 
The general recipe was to inspect an LM's internal representations, and to 
find a simple procedure for translating them into something resembling a 
human-approved meaning representation in some formal linguistic theory.

It turned out that the hard part of this problem had nothing to do with LMs:
it was figuring out
what "meaning" means, and what these human-approved representations should look
like in the first place. So the NLP interpretability community immediately
started arguing about model-theoretic vs relational theories of meaning;
whether it was enough for models' internal representations to be isomorphic to
human-designed meaning representations, or whether explicit links to perception
and action
were strictly necessary; etc. This was very interesting, and I think we learned
a lot of general lessons about the design and interpretation of interpretability
experiments. But I’m not sure we made much progress on the big empirical
question about how LMs work.

In the meantime LMs themselves have gotten much better---it's harder, though
certainly not impossible, to find errors in LM output that are naturally
understood as complete failures to represent the meaning of input text. We have
vision-and-language models of the kind that grounding fundamentalists ([I used to
be
one](https://arxiv.org/abs/2004.10151)) said would fix the outstanding problems
with text generation. But at scale, the addition of visual supervision [doesn't
seem to change the quality of text generation very much](
https://arxiv.org/abs/2310.13257). 
So even with grounding---and in other domains like video generation or protein
sequence modeling---we still can't agree whether neural sequence predictors are
really understanding or shallowly manipulating their inputs.

One of the biggest consequences of all this is that the community has started
asking a better version of the Big Question: do LMs have internal **world models**?

Concretely: do text-generation models represent situations and possible worlds
described by text, and consult these representations to determine what might
happen next? Do video-generation models build representations of the laws of
physics and the latent 3-D geometry of scenes, and predict future frames by
evolving these geometric representations forward in time? More generally, do
neural sequence predictors _encode and recapitulate the real causal process_ in
the outside world that generated their data? Or do they do what they do by
shuffling words and pixels around without ever passing through an intermediate
representation or computation that looks like the one taking place in the
outside world?

At a first glance this seems like an easier question to answer.  "Is the hidden
representation _h_ a representation of meaning?" is an abstruse problem for
philosophers of language; "is _h_ a representation of the world?" is a question
that people working in classical AI, control theory, and computational
simulation think about every day. Nevertheless, 
we can't seem to agree on a definition of "world model" any more than we agreed
on "meaning representation". So every new paper that attempts to describe some
neural sequence predictor's internal state as a "world model" is invariably met
with one of two responses "that's not a model" or "that's not the world".

How should we talk about representations that LMs (or humans, or other
predictive models) build of the world we inhabit?
This post is an exploration (but certainly not a resolution) of this version of
the Big Question. It's impossible to write a couple of thousand words about
models without that quote from George Box, so let's get it out of the way now:

> Essentially, all models are wrong, but some are useful. <br>

<p class="aside">[Box 1979, <i>Robustness in the strategy of scientific model building</i>]</p>

Here I'm especially interested in the lessons we can take from the particular
kinds of wrongness and usefulness that show up in human-designed models, and
what intuition human model-building can give us about the kinds
of representations LMs might build, and how these representations might
influence behavior.

## Three models of the solar system

I want to start by drawing an analogy to human-designed models of a very
specific physical domain: the solar system. Over the years, humans have modeled
this system in several different ways:

### Model 1: The map

<img src="map.jpg">

<p class="aside">Until the age of about six I ate all of my meals off of a placemat that looked
just like this. <br> [Image credit: NASA.] </p>

This image is a  member of the class
of very simple models we call **maps**.  It takes a massive, complicated,
dynamic collection of bodies, and hides most of the information about their
current state, and all of the information about how this state changes over time.  (Is
a map a model? We're certainly happy to apply the word “model” to lots of other
static, small-scale versions of complex, dynamic things---consider a "model car"
or "model airplane".) What the map does provide is a highly simplified
representation that lets us easily answer a restricted set of questions like
"which planet is farthest from the sun?" or "how many times would Earth fit
inside Jupiter’s red spot?".

Importantly, a map is _not_ a lookup table: it doesn't give us precomputed
answers to
every possible question we could ask, but instead a comparatively
low-dimensional representation of the underlying system that generates answers
to those questions, and from which answers can be easily computed with a little
bit of extra work.

### Model 2: The orrery

<img src="orrery.jpg">

<p class="aside">[Image credit: Staines and Son.]</p>

Here's another model of the solar system---an **orrery**. Like the map, it shows
the relative locations of the planets (now in 3D!). Unlike the map, it is
_dynamic_: I can ask about those relative positions, not just at some fixed, but
at arbitrary points in the past or future, by turning a little crank [not
pictured] and evolving the system forward or backward in time.
With this
model, we can answer conditional questions like "where will Jupiter be in
three years?", "where will Jupiter be during the next lunar eclipse?", or "how
long until four planets are collinear?".

We can answer these questions with such a simple interface---just a
crank---because the orrery, like the map, "hard-codes" many properties of the
system (like the shape and size of orbits) that actually derive from more
general principles. As with the map, this means there are many questions we
can't answer! For example, we can't handle "where would the Earth
be positioned relative to the moon in three years if they were to swap places
now?", because this change would alter the Earth’s orbit in a way that can’t be
represented without completely reconstructing the mechanism.  Nevertheless, by
incorporating these restrictions we obtain a simple and robust mechanical model
that enables us to answer a surprisingly rich set of questions.


### Model 3: The simulator

<iframe width="100%" height="500"
src="https://www.youtube.com/embed/j_NU9UuULt4?si=X1ev5ZF_VrkqB2FI"
title="YouTube video player" frameborder="0" allow="accelerometer; autoplay;
clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<p class="aside" style="margin-top: 1px; transform: none">[video credit: trekto.info/n-body-simulation.]</p>

Here's our last model. It's no longer a model of the solar system in particular,
but instead a general gravitational **simulator**. We configure it with a
collection of initial masses, positions, and velocities, and it approximates the
full n-body dynamics as precisely as we can with current computational tools. In
moving from the orrery to the simulator, we've moved much closer to the "real"
causal model generating astronomical data (though of course there's still a huge
amount that we've left out). We've hard-coded much less information than the
orrery (we no longer need to bake in the fact that orbits are
elliptical---instead this emerges from simulation). As a result, we
can answer even more complex questions (what _would_ happen in three years if
Jupiter and Saturn changed places today?). Indeed, we can now evaluate a pretty
general class of counterfactual questions that involve reasoning about
states of the world that are unreachable from its current state.


## Affordances and implementations

The map, the orrery, and the simulator are all models of the same underlying
system. Where they differ is in their **affordances**---the set of questions
they enable a _user_ of the model to answer, and the actions the user needs to
take in order to
obtain those answers. The map lets us answer static, timeless information that
can be obtained by from some **prior** snapshot of system state. The orrery lets
us answer **conditional** questions about the past and future states of the
system, by additionally giving us a crank that moves it forward or backward in
time. And the simulator lets us answer **counterfactual** questions of the
system by representing something close to its true underlying dynamics (but
requires us to do substantially more work to specify the initial conditions for
these
counterfactuals).

<p class="aside">Note both similarities and important differences vis-a-vis <a href="https://web.cs.ucla.edu/~kaoru/3-layer-causal-hierarchy.pdf">Pearl’s "ladder of
causation"</a>: maps can’t even answer many questions at the associational
level, and the interventional / counterfactual distinction is less important
when we’re talking about queries to models rather than the real world.</p>

With these differences in affordances come differences in the complexity
required to implement each model. You can make a map with stone-age technology,
and build the orrery in a 17th-century goldsmith's shop, but can really only
produce
the simulator with 20th-century technology (from chip fabs to FORTRAN
compilers).

But importantly, each of these implementations is _simple relative to the
kinds of questions it lets us answer_. I think this is really the essential
property of "being a world model" (one we could formalize, say, in
minimum-description-length terms): by representing some important aspect of the
data-generating process---even if incompletely or imperfectly---we can avoid
pre-computing all answers to all questions, within whatever restricted set we
need to answer.

In this sense, the canonical system that's not a world model is exactly a lookup
table. And if we want to understand whether a system for answering questions or
generating predictions has a world model, we can *only* answer that question by
looking inside that system and determining what computations it performs.
(Though c.f. [this cool recent paper](https://arxiv.org/abs/2406.03689) for a
purely behavioral take on world models.)



## Beyond the solar system

What can these models of the solar system teach us about LMs?

A major point of contention in the current debate is just about what _kinds_ of
questions a system equipped with a world model ought to be able to answer. But
as we've seen, it’s not necessary to make a binary distinction here. Instead, we
can
talk about world models at varying levels of expressiveness (the “prior”,
“conditional”, and “counterfactual” levels above)---or, even more precisely,
about
which specific aspects of the data-generating process our model encodes, and
what’s left out. Once we know what kind of model we're looking for, it
suffices to exhibit the internal representational circuit that implements the
model, and show that we can configure it (the equivalent of crank turning) and
inspect it (the equivalent of observation & measurement) to obtain the answers
we expect.

We can understand many of the "world models" discovered by past work in these
terms:

- Structured embedding spaces, like the “representations of space and time”
  described
  [here](https://arxiv.org/abs/2310.02207), look like maps.
  (Indeed, much simpler "language models" like word2vec, or even word
  embeddings from latent semantic analysis, also have "maps" that look like
  this, and it seems totally reasonable to talk about "word2vec's world model"
  in the map-ish sense.) So are "knowledge matrices" of the kind found by
  [ROME](https://arxiv.org/abs/2202.05262) and subsequent work.

- Structured situation models, like the ones from our [state probes paper](https://arxiv.org/abs/2106.00737),
  look like orreries. ([Followup work](https://arxiv.org/abs/2305.02363) suggests that these models are
even lower-resolution than we made them out to be, without much in the way of
  quantitative reasoning, and just coarse predicate tracking. And more [recent work](
  https://arxiv.org/abs/2406.19501) paints a clearer picture of
what situation models look like in
  current LMs.) Mechanistically, such models work very differently from
maps---they live in hidden representations, rather than weight matrices, and are
constructed on the fly.

- As for simulators, I don't think we have any really
  clear pictures.
  Models can certainly answer counterfactual questions, and you can even use
  this to do model editing (see work on [editing via context distillation](
https://arxiv.org/abs/2306.09306)). It would be very exciting to get a
mechanistic picture even for
  some toy language domain. Outside models of language this is clearer---in 
  Othello, for example
, a model trained on move sequences builds an internal
board
  state representation that makes correct predictions [even on states unreachable
  via natural play](https://arxiv.org/abs/2210.13382).

Within these examples, there are a couple of LM-specific modeling considerations 
that are worth saying a little more about:
  
### Coherence

Even some very large models are happy to label both of the following sentences
as
true [https://arxiv.org/abs/2109.01653:

> (1) U.S. Route 1 connects New York to Florida. <br>
> (2) U.S. Route 1 connects New York to California.

This should be impossible even just given an internal "map" of the US
(and some basic knowledge of how highway numbering works). These
kinds of errors are generally taken as evidence against the existence of
LM-internal world models. The solar system map we looked at above contains no
errors of this kind. But it could have been otherwise! Notice that the map has a
little bar along the bottom showing relative distances between planets. We could
modify just this bar to make it wrong in some small way (e.g. moving Mercury
so that its boundaries overlap with the sun, creating a disagreement with the
information conveyed by the size chart and the position chart). Doing so
wouldn't
at all affect our ability to answer questions about other planets, and in this
case we might choose to describe our image as a model of the outer planets, or
alternatively a noisy model of the solar system, or alternatively _two_ mutually
incompatible models, stapled together, that disagree about the size and position
of Mercury.

LMs make more, and more serious mistakes than this, but for exactly this reason
it seems especially important to try to be as precise as possible about a
model's "level of
resolution" when making interpretability claims.

### Consistency

Maybe the most important lesson from these examples is that we shouldn't expect
an LM to have one world model, but many---this way, for example, they can store
knowledge statically in their parameters, but still reason in-context about
information that contradicts these parameters. Different ways of interacting
with LMs may, in general, invoke different models. So, in a question answering
task, we might be accessing different world models depending on whether we’re
inspecting parameters, training a probe, or reading an LM's generated text. When
answering conditional questions, we might be _manipulating_ different world
models depending on whether we’re specifying our conditional or counterfactual
via fine-tuning, low-rank editing or via a textual prompt. In fact, I suspecting
most of the hand-wringing about the failure of parameter editing to produce
globally consistent outputs involves a model misidentification error of this
type: we're using map-manipulation techniques while trying to answer
simulator-type questions.  Model editing techniques that actually work (RAG and
context distillation) clearly do so via a different interface that invokes
counterfactual-level model, even though we don't know how that model operates. 

If you expect a language model to derive all of its answers from a single,
monolithic, coherent internal model of the outside world, all the behavior
described above is evidence that this world model doesn't exist.  But it's
increasingly clear that we should really conceptualize LMs (at least today's) as
collections of competing mechanisms---a knowledge retrieval circuit voting
against a copying circuit voting against an n-gram model. And this is for a good
reason! Maps are much easier to configure and read than simulators, and if LMs
couldn't use them at least occasionally they'd never get anything done with a
single forward pass. (Do you re-simulate the entire history of the universe
whenever someone asks what your birthday is?)

As a final point, I want to stress that the discussion above says nothing at all
about how LMs _use_ their internal world models. It’s entirely possible to
imagine an LM that possesses a “world model” that we can query, manipulate,
etc., and which nevertheless has no relationship at all to the LM’s own
generated text. (Perhaps the outputs of the world model don’t feed back into
next-token prediction, or are always overridden by some other prediction
mechanism). The extreme version of this scenario is a little far-fetched---world
models cannot arise in any other way than as a byproduct of learning to do text
generation---but that doesn't imply that LMs "say" everything that internal
world models predict.

## Toward better world models, and better language models

The discussion above mainly focuses on ways to (and reasons to) ascribe world
models to LMs even given their current limitations. But I think we’re also
starting to see evidence that we can make LMs better (more accurate, more
trustworthy, more controllable) as we start to address those limitations. So in
addition to the interpretability agenda focused on describing world models in
LMs, I'm excited about techniques for automatically improving these models’
consistency and coherence. For example, you can think of [our recent DCT paper](
https://arxiv.org/abs/2401.08574) as “model editing by using a simulator to
generate synthetic data to supervise a map”. Future tools might use this kind of
supervision to manipulate representations and parameters directly, or even
replace LM-internal circuitry with parameters derived directly from outside
knowledge sources and sensors, bypassing “fine-tuning” altogether.

---

_Thanks to Yonatan Belinkov, David Bau, Gabe Grand, Charles Jin, Belinda Li and
Martin Wattenberg for comments on an early draft of this post, and to Ekin
Aky&uuml;rek, Noah Goodman, Josh Tenenbaum and Lio Wong, as well as Shiry
Ginosar and other participants in the the Simons Institute Workshop on
Understanding Higher-Level Intelligence, for many useful discussions on this
subject over the last few months._


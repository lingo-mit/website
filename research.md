---
layout: default
title: Papers
---

## Research highlights

<ul class="paper-highlights">

<li>
  <p>
  <b><a href="https://arxiv.org/abs/2110.01517">Skill induction and planning with latent language</a>.</b><br>
  </p>

  <p>
  Pratyusha Sharma, Antonio Torralba and Jacob Andreas. ACL 2022.
  </p>

  <img src="assets/images/paper_teasers/sl3.gif" alt="Visualization:">

  <p>
  How can we train agents to plan & act in complex environments? 
  We build models that “plan out loud”, using language as both a supervisory signal and internal representation. 
  These agents improve significantly over standard imitation learning approaches, while producing internal representations of their long-range plans and generalizing to new goals using knowledge learned from text.
  </p>
</li>

<li>
  <p>
  <b><a href="https://arxiv.org/abs/2106.00737">Implicit representations of meaning in neural language models</a>.</b><br>
  </p>

  <p>
  Belinda Z. Li, Maxwell Nye and Jacob Andreas. ACL 2021.
  </p>

  <img src="assets/images/paper_teasers/state_probes.jpg" alt="Visualization:
  language model representations can be directly manipulated to affect
  the semantics of downstream generation.">

  <p>
  Language models (trained to predict missing words in sentences and paragraphs)
learn to build structured representations of the state of the world. These
representations support model-internal reasoning about the consequences of actions
(like mixing a beaker or unlocking a door with a key).  The organization of
semantic information in language model embeddings bears striking resemblance to
formal meaning representations like DRT and file change semantics from the
linguistics literature, suggesting that it's possible to discover a little bit
about how meaning works with nothing but text as training data.
  </p>
</li>

<li>
  <p>
  <b><a href="https://arxiv.org/abs/2006.14032">Compositional explanations of neurons</a>.</b>
  </p>

  <p>
  Jesse Mu and Jacob Andreas. NeurIPS 2020.
  </p>

  <img src="assets/images/paper_teasers/compexp.jpg" alt="Visualization: our
  technique discovers neurons that recognize compositional concepts like '(water
  or river) and (not blue)' and 'operating room or castle or bathroom'">

  <p>
  We explain the behavior of deep network models by approximating each neuron
  with an executable program or logical form. These compositional explanations
  let us automatically quantify (aspects of) the complexity, interpretability, and
  naturalness of learned abstractions in vision and language models.  They surface
  a number of surprising successes (image classifiers discover abstract functional
  categories like "sports facility" without supervision) but also sources of
  brittleness (vision models easily confuse washing machines with viaducts and
  cribs with fire escapes, and language processing models are easily tricked by
  surprising combinations of pronouns).
  </p>
</li>
</ul>

<div style="clear: both"></div>

## Full paper list

### 2023
- [Mastering the Game of No-Press Diplomacy via Human-Regularized Reinforcement Learning and Planning.](https://arxiv.org/abs/2210.05492)

  Anton Bakhtin*, David J Wu*, Adam Lerer*, Jonathan Gray*, Athul Paul Jacob*, Gabriele Farina*, Alexander H Miller, Noam Brown. ICLR 2023. (<b>Oral</b>)
  
  Press: [NewScientist](https://www.newscientist.com/article/2343027-ais-built-by-meta-beat-human-experts-at-diplomacy/)
  
- [Top-Down Synthesis for Library Learning.](https://arxiv.org/abs/2211.16605)

  Matthew Bowers, Theo X. Olausson, Lionel Wong, Gabriel Grand, Joshua B. Tenenbaum, Kevin Ellis, Armando Solar-Lezama. POPL 2023.

### 2022  
- [Human-level play in the game of Diplomacy by combining language models with strategic reasoning.](https://www.science.org/doi/10.1126/science.ade9097)
  
  FAIR, Anton Bakhtin* , Noam Brown*, Emily Dinan*, Gabriele Farina, Colin Flaherty*, Daniel Fried, Andrew Goff, Jonathan Gray*, Hengyuan Hu*, Athul Paul Jacob*, Mojtaba  Komeili, Karthik Konath, Minae Kwon, Adam Lerer*, Mike Lewis*, Alexander H. Miller*, Sasha Mitts, Adithya Renduchintala*, Stephen Roller, Dirk Rowe, Weiyan Shi*, Joe Spisak, Alexander Wei, David Wu*, Hugh Zhang*, Markus Zijlstra. Science 2022.

  Press: [The Economist](https://www.economist.com/science-and-technology/2022/11/23/another-game-falls-to-an-ai-player), [Forbes](https://www.forbes.com/sites/carlieporterfield/2022/11/22/metas-ai-gamer-beat-humans-in-diplomacy-using-strategy-and-negotiation/?sh=3d2ce522788b), [The Washington Post](https://www.washingtonpost.com/technology/2022/12/01/meta-diplomacy-ai-cicero/), [The New York Times](https://www.nytimes.com/2023/01/20/technology/chatbots-turing-test.html), [The New Yorker](https://www.newyorker.com/culture/2022-in-review/eight-times-science-exceeded-expectations-in-2022), [VentureBeat](https://venturebeat.com/ai/is-ai-moving-too-fast-for-ethics-the-ai-beat/)
  
- [Language Models as Agent Models.](https://arxiv.org/abs/2212.01681)
  
  Jacob Andreas. EMNLP Findings 2022.

- [“Semantic projection” recovers rich human knowledge of multiple object features from word embeddings.](https://arxiv.org/abs/1802.01241)
  
  Gabriel Grand, Idan Blank, Francisco Pereira, and Evelina Fedorenko. Nature Human Behaviour 2022.

- [Identifying concept libraries from language about object structure.](https://arxiv.org/abs/2205.05666) 

  Lionel Wong, William P. McCarthy, Gabriel Grand, Yoni Friedman, Joshua B. Tenenbaum, Jacob Andreas, Robert D. Hawkins, Judith E. Fan. CogSci 2022.
  
- [Tracing Knowledge in Language Models Back to the Training Data.](https://arxiv.org/abs/2205.11482)

  Ekin Aky&uuml;rek, Tolga Bolukbasi, Frederick Liu, Binbin Xiong, Ian Tenney, Jacob Andreas, Kelvin Guu. Preprint.

- [Compositionality as Lexical Symmetry.](https://arxiv.org/abs/2201.12926)

  Ekin Aky&uuml;rek, Jacob Andreas. Preprint.
  
- [Modeling Strong and Human-Like Gameplay with KL-Regularized Search.](https://arxiv.org/abs/2112.07544)
  
  Athul Paul Jacob*, David J. Wu*, Gabriele Farina*, Adam Lerer, Hengyuan Hu, Anton Bakhtin, Jacob Andreas, Noam Brown. ICML 2022. (<b>Spotlight</b>)

- [Correcting Robot Plans with Natural Language Feedback.](https://arxiv.org/abs/2204.05186)

  Pratyusha Sharma, Balakumar Sundaralingam, Valts Blukis, Chris Paxton, Tucker Hermans, Antonio Torralba, Jacob Andreas, Dieter Fox. RSS 2022.

- [Quantifying Adaptability in Pre-trained Language Models with 500 Tasks.](https://arxiv.org/abs/2112.03204)

  Belinda Z. Li, Jane Yu, Madian Khabsa, Luke Zettlemoyer, Alon Halevy, Jacob Andreas. NAACL 2022.

- [Skill induction and planning with latent language.](https://arxiv.org/abs/2110.01517)

  Pratyusha Sharma, Antonio Torralba, and Jacob Andreas. ACL 2022.

- [Natural Language Descriptions of Deep Visual Features.](https://arxiv.org/abs/2201.11114)

  Evan Hernandez, Sarah Schwettmann, David Bau, Teona Bagashvili, Antonio
  Torralba and Jacob Andreas. ICLR 2022 (<b>oral</b>).

  Press: [MIT News](https://news.mit.edu/2022/explainable-machine-learning-0127).

- [Subspace Regularizers for Few-Shot Class Incremental Learning.](https://arxiv.org/abs/2110.07059)

  Afra Feyza Akyu&uuml;rek, Ekin Aky&uuml;rek, Derry Wijaya and Jacob Andreas.
  ICLR 2022.

### 2021

- [How do neural sequence models generalize? Local and global context cues for
  out-of-distribution prediction.](https://arxiv.org/abs/2111.03108)

  Anthony Bau and Jacob Andreas. EMNLP 2021.

- [The low-dimensional linear geometry of contextualized word representations.](https://arxiv.org/abs/2105.07109)

  Evan Hernandez and Jacob Andreas. CoNLL 2021.

- [Leveraging language to learn program abstractions and search heuristics.](https://arxiv.org/abs/2106.11053)

  Lionel Wong, Kevin Ellis, Joshua B. Tenenbaum and Jacob Andreas. ICML 2021.

- [Implicit representations of meaning in neural language models.](https://arxiv.org/abs/2106.00737)

  Belinda Z. Li, Maxwell Nye and Jacob Andreas. ACL 2021.

- [What context features can transformer language models use?](https://arxiv.org/abs/2106.08367)

  Joe O'Connor and Jacob Andreas. ACL 2021.

- [Lexicon learning for few-shot sequence modeling.](https://arxiv.org/abs/2106.03993)

  Ekin Aky&uuml;rek and Jacob Andreas. ACL 2021.

- [Multitasking inhibits semantic drift](https://arxiv.org/abs/2104.07219).

  Athul Paul Jacob, Mike Lewis and Jacob Andreas. NAACL 2021.

- [Representing partial programs with blended abstract
  semantics](https://arxiv.org/abs/2012.12964).

  Maxwell Nye, Yewen Pu, Matthew Bowers, Jacob Andreas, Joshua B. Tenenbaum,
  Armando Solar-Lezama. ICLR 2021.

- [Learning to recombine and resample data for compositional
  generalization](https://arxiv.org/abs/2010.03706).

  Ekin Aky&uuml;rek, Afra Feyza Aky&uuml;rek and Jacob Andreas. ICLR 2021.

### 2020

- [Compositional explanations of neurons](https://arxiv.org/abs/2006.14032).

  Jesse Mu and Jacob Andreas. NeurIPS 2020 (<b>oral</b>).

- [A benchmark for systematic generalization in grounded language
   understanding.](https://arxiv.org/abs/2003.05161)

  Laura Ruis, Jacob Andreas, Marco Baroni, Diane Bouchacourt and Brenden Lake.
  NeurIPS 2020.

- [Good-Enough Compositional Data Augmentation](
  https://arxiv.org/abs/1904.09545).

  Jacob Andreas. ACL 2020.

- [Unnatural language processing: bridging the gap between synthetic and natural
  language data](https://arxiv.org/abs/2004.13645).

  Alana Marzoev, Sam Madden, Frans Kaashoek, Mike Cafarella and Jacob Andreas.
  NeurIPS workshop on Emergent Communication.

### 2019

- [A survey of reinforcement learning informed by natural language](
  https://arxiv.org/abs/1906.03926).

  Jelena Luketina, Nantas Nardelli, Gregory Farquhar, Jakob Foerster, Jacob
  Andreas, Edward Grefenstette, Shimon Whiteson and Tim Rocktäschel. IJCAI 2019.

- [Measuring compositionality in representation learning](
  https://arxiv.org/abs/1902.07181).

  Jacob Andreas. ICLR 2019.

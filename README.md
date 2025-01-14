# Awesome Sparse Autoencoders

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Awesome Sparse Autoencoders is a curated list of papers,
models, explainers and libraries for Dictionary Learning With Sparse Autoencoders.

## Contents

- [Contents](#contents)
- [About](#about)
- [Architecture \& Theory](#architecture--theory)
- [Motivating Results](#motivating-results)
- [Training Notes \& Intuitions](#training-notes--intuitions)
- [Open Source Libraries](#open-source-libraries)
- [Scaling Up \& Scaling Laws](#scaling-up--scaling-laws)
- [Trained Autoencoders](#trained-autoencoders)
- [Other](#other)

## About

`Dictionary Learning with Sparse Autoencoders (SAEs)` is a technique for disentangling the intermediate neural activations into more monosemantic representations for interpretability and steering.

---

In this repo, links are organised by topic and have explanations so you can
decide what you would like to read. Especially recommended links are starred 🌟 and links which play a part in the current best recipe for SAEs are marked with a chef emoji 🧑‍🍳

Star this repository to see the latest developments in this research field.

We accept contributions! We strongly encourage researchers & practitioners to
make pull requests with papers, approaches and explanations that they feel
others in the community would benefit from 🤗

<!-- Ordered by topic, then date published -->

## Architecture & Theory

<!-- 🧑‍🍳 🌟 **[TITLE], [LAB]: [AUTHORS] ([YEAR])**
[pdf]([LINK]),
[blog]([LINK]),
[code]([LINK]),
[demo]([LINK])

> [EXPLANATION] -->

**Prism, Notion: Linus Lee (2024)**
[pdf](https://thesephist.com/posts/prism/?)

> Linus Lee's strategy for training Sparse Autoencoders. The main ideas are similar but he approaches the problem from a different angle, focusing on building tools for thought and debugging models.

🧑‍🍳 🌟 **Scaling Sparse Autoencoders, OpenAI: Gao et al (2024)**
[pdf](https://cdn.openai.com/papers/sparse-autoencoders.pdf)
[blog](https://openai.com/index/extracting-concepts-from-gpt-4/)
[code](https://github.com/openai/sparse_autoencoder)

> The OpenAI's Superalignment team (RIP) show that sparse autoencoders can be scaled to
> large models like GPT-4 and find some interesting features. The main contribution of
> this work though is the Top-K sparsity mechanism as an activation function which
> means that the l1 sparsity auxiliary loss is no longer needed.
>
> Their codebase is very clean but only shows using rather than training SAEs.
> Note their Triton kernels for sparse * dense matrix multiplication which improve
> the speed of training all SAEs - this is a great service to the community! (They use TransformerLens for
> activation caching).

🌟 **Gated Sparse Autoencoders, DeepMind: Rajamanoharan et al (2024)**
[pdf](https://arxiv.org/pdf/2404.16014)

> To address the shrinkage problem in SAEs, DeepMind introduce a gating mechanism
> inspired by Shazeer-style GLUs. Theoretically this allows the autoencoder to separate
> predictions the magnitude of feature firing from whether the features fire or not.
> This seems to work and actually has benefits beyond what addressing shrinkage directly would
> do so it seems that the Gated SAEs also just provide better encoder representations.

**Group Sparse Autoencoders, Harvard: Theodosis et al (2023)**
[pdf](https://crisp.seas.harvard.edu/files/papers/TheodosisBa_SilhouetteLearning_ICASSP23.pdf)

> The authors show that by grouping features together in the sparsity constraint they're better able to learn features which naturally compose together. They test on image datasets but this could be applied to language models too.

## Motivating Results

🌟 **Transformer Visualisation via Dictionary Learning FAIR: Yun et al (2021)**
[pdf](https://arxiv.org/pdf/2103.15949)

> An early attempt to break down embeddings into components. A useful paper for understanding how the Interpretability literature fits into previous research.

**Sparse Autoencoders Find Highly Interpretable Features in Language Models: Cunningham et al (2023)**
[pdf](https://arxiv.org/abs/2309.08600)
[code](https://github.com/HoagyC/sparse_coding)

> The first clear demonstration that SAEs using an L1 penalty, rather than other dictionary learning methods, give rise to interpretable features.

<!-- ## Safety Applications -->

<!-- ## Non-Safety Applications

Linus - https://x.com/thesephist/status/1747099907016540181

Golden Gate Claude -->

## Training Notes & Intuitions

<!-- Circuits Updates Anthropic
Also DeepMind -->

**Training Tricks for 1-Layer SAEs, Conmy (2023)**
[blog](https://www.lesswrong.com/posts/fifPCos6ddsmJYahD/my-best-guess-at-the-important-tricks-for-training-1l-saes)

> The most important things to get right seem to be the SAE width, resampling procedure, and the learning rate. They also suggest that rewarming up the learning rate after resampling is valuable.

## Open Source Libraries

<!-- 🌟 **Dictionary Learning, Cavendish Labs: Ayonrinde et al (2023)**
[code](https://github.com/koayon/dictionary_learning)

> My favourite library for training sparse autoencoders.
> You can easily use lots of the different approaches to training SAEs and is
> designed to be a research library where you can define your own encoders, loss functions
> and activation functions. PRs are welcome! -->

**SAE Library, Eleuther: Belrose et al (2024)**
[code](https://github.com/EleutherAI/sae)

> A highly readable library for distributed training of sparse autoencoders with a great API interface.
> Mostly uses standard methods and isn't as customisable. More of a training library than a research one.

<!-- ## Multimodal -->

<!-- ## AI Safety -->

<!-- Explainer -->

## Scaling Up & Scaling Laws

🌟 **Scaling Monosemanticity to Claude Sonnet, Anthropic: Templeton et al (2024)**
[website](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html)
[blog](...)

> Anthropic show that the SAE approach scales to frontier scale models. A useful proof of concept
> and some interesting phenomenological results.
>
> There were a few criticisms of the paper [here] and [here]. # TODO: Add criticisms

## Trained Autoencoders

**Pythia Features, Northeastern: Marks et al (2023)**
[blog](https://www.alignmentforum.org/posts/AaoWLcmpY3LKvtdyq/some-open-source-dictionaries-and-dictionary-learning)

> One of the first open source SAE dictionaries available. Released alongside training code.

## Other

**List of Favourite Mech Interp Papers, Neel Nanda (2024)**
[blog](https://www.alignmentforum.org/posts/NfFST5Mio7BCAQHPA/an-extremely-opinionated-annotated-list-of-my-favourite-1#Sparse_Autoencoders)

> Neel Nanda's list of important papers in Mechanistic Interpretability. There's a section on Sparse Autoencoders which has links to many of the same papers as above but with Neel's short takes on them. Other adjacent MechInterp fields are also covered which may be worth reading.

**How To Report Better SAE Performance, Bostock (2024)**
[blog](https://www.lesswrong.com/posts/fhffkfJv9zYPeP3uJ/how-to-better-report-sparse-autoencoder-performance)

> The author suggests that to present the SAE Pareto frontier more clearly (i.e. the trade-off between sparsity and reconstruction error) it's beneficial to git a Hill curve.

**Not All Language Model Features Are Linear, MIT: Engels et al (2024)**
[pdf](https://arxiv.org/pdf/2405.14860)

> SAEs generally lean on the Linear Representation Hypothesis. This paper shows that
> this is not always the case and that some features of language models are not linear.
> They show some examples of this for features which are essentially in low dimensional
> manifolds instead of being strictly linear and hypothesise that this could happen
> more widely. Very interesting work showing something that seemed to be the case and
> this shows that for the last few 9s of reliability we may need to think beyond strict linearity.
> They use SAEs to find the non-linear features.

🌟 **Automated Interpretability, OpenAI: Bills et al (2023)**
[website](https://openaipublic.blob.core.windows.net/neuron-explainer/paper/index.html)
[blog](https://openai.com/index/language-models-can-explain-neurons-in-language-models/)
[code](https://github.com/openai/automated-interpretability)
[forked code](https://github.com/hijohnnylin/automated-interpretability)

> Once you've trained your SAE typically you want to understand what it has learned
> by checking how interpretable the features are by humans or LLMs. This library allows you to do that
> and this work introduced the basic framework for automated interpretability.

**Using AI to Augment Human Intelligence, Google Brain: Carter & Nielsen (2017)**
[website](https://distill.pub/2017/aia/)

> A paper which thinks about how representations that can be manipulated are useful for humans. This is interesting to think about the applications of SAEs beyond enumerative safety.

<!-- ## Approaches We're Excited To See Explored More

-->

<br>

---

<br>

Thanks for reading, if you have any suggestions or corrections please submit a
pull request! And please hit the star button to show your appreciation.

## Citing This Post

If you'd like to cite this article, please use:
```
@misc{ayonrinde_2023_awesome_sparse_autoencoders,
  author = "Kola Ayonrinde",
  title = "Awesome Sparse Autoencoders",
  year = 2024,
  publisher = "GitHub",
  url = "https://github.com/koayon/awesome-sparse-autoencoders/"
}
```

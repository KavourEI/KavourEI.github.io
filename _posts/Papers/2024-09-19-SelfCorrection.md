---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Training Language Models to Self-Correct via Reinforcement Learning
date: 2024-09-19
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Self-correction is a highly desirable capability of large language models (LLMs), yet it has consistently been found to be largely ineffective in modern LLMs. Existing approaches for training self-correction either require multiple models or rely on a more capable model or other forms of supervision. To this end, we develop a multi-turn online reinforcement learning (RL) approach, SCoRe, that significantly improves an LLM's self-correction ability using entirely self-generated data. To build SCoRe, we first show that variants of supervised fine-tuning (SFT) on offline model-generated correction traces are insufficient for instilling self-correction behavior. In particular, we observe that training via SFT either suffers from a distribution mismatch between the training data and the model's own responses or implicitly prefers only a certain mode of correction behavior that is often not effective at test time. SCoRe addresses these challenges by training under the model's own distribution of self-generated correction traces and using appropriate regularization to steer the learning process into learning a self-correction strategy that is effective at test time as opposed to simply fitting high-reward responses for a given prompt. This regularization prescribes running a first phase of RL on a base model to generate a policy initialization that is less susceptible to collapse and then using a reward bonus to amplify self-correction during training. When applied to Gemini 1.0 Pro and 1.5 Flash models, we find that SCoRe achieves state-of-the-art self-correction performance, improving the base models' self-correction by 15.6% and 9.1% respectively on the MATH and HumanEval benchmarks.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Kumar,+A">Aviral Kumar</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhuang,+V">Vincent Zhuang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Agarwal,+R">Rishabh Agarwal</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Su,+Y">Yi Su</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Co-Reyes,+J+D">John D Co-Reyes</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Singh,+A">Avi Singh</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Baumli,+K">Kate Baumli</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Iqbal,+S">Shariq Iqbal</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Bishop,+C">Colton Bishop</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Roelofs,+R">Rebecca Roelofs</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhang,+L+M">Lei M Zhang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=McKinney,+K">Kay McKinney</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Shrivastava,+D">Disha Shrivastava</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Paduraru,+C">Cosmin Paduraru</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Tucker,+G">George Tucker</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Precup,+D">Doina Precup</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Behbahani,+F">Feryal Behbahani</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Faust,+A">Aleksandra Faust</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2409.12917'>here</a></p>
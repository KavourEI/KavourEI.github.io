---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Transfusion - Predict the Next Token and Diffuse Images with One Multi-Modal Model
date: 2024-08-20
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> We introduce Transfusion, a recipe for training a multi-modal model over discrete and continuous data. Transfusion combines the language modeling loss function (next token prediction) with diffusion to train a single transformer over mixed- modality sequences. We pretrain multiple Transfusion models up to 7B parameters from scratch on a mixture of text and image data, establishing scaling laws with respect to a variety of uni- and cross-modal benchmarks. Our experiments show that Transfusion scales significantly better than quantizing images and training a language model over discrete image tokens. By introducing modality-specific en- coding and decoding layers, we can further improve the performance of Transfusion models, and even compress each image to just 16 patches. We further demonstrate that scaling our Transfusion recipe to 7B parameters and 2T multi-modal tokens produces a model that can generate images and text on a par with similar scale diffusion models and language models, reaping the benefits of both worlds.</p>

<h2> Authors </h2>

<p> Chunting Zhou, Lili Yu, Arun Babu, Kushal Tirumala, Michihiro Yasunaga, Leonid Shamis, Jacob Kahn, Xuezhe Ma, Luke Zettlemoyer, Omer Levy</p>

<p>For more information go <a href='https://arxiv.org/pdf/2408.11039'>here</a></p>
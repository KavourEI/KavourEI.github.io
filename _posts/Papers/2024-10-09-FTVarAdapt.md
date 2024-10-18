---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: One Initialization to Rule them All:Fine-tuning via Explained Variance Adaptation
date: 2024-10-09
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Foundation models (FMs) are pre-trained on large-scale datasets and then fine-tuned on a downstream task for a specific application. The most successful and most commonly used fine-tuning method is to update the pre-trained weights via a low-rank adaptation (LoRA). LoRA introduces new weight matrices that are usually initialized at random with a uniform rank distribution across model weights. Recent works focus on weight-driven initialization or learning of adaptive ranks during training. Both approaches have only been investigated in isolation, resulting in slow convergence or a uniform rank distribution, in turn leading to sub-optimal performance. We propose to enhance LoRA by initializing the new weights in a data-driven manner by computing singular value decomposition on minibatches of activation vectors. Then, we initialize the LoRA matrices with the obtained right-singular vectors and re-distribute ranks among all weight matrices to explain the maximal amount of variance and continue the standard LoRA fine-tuning procedure. This results in our new method Explained Variance Adaptation (EVA). We apply EVA to a variety of fine-tuning tasks ranging from language generation and understanding to image classification and reinforcement learning. EVA exhibits faster convergence than competitors and attains the highest average score across a multitude of tasks per domain.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Paischer,+F">Fabian Paischer</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Hauzenberger,+L">Lukas Hauzenberger</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Schmied,+T">Thomas Schmied</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Alkin,+B">Benedikt Alkin</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Deisenroth,+M+P">Marc Peter Deisenroth</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Hochreiter,+S">Sepp Hochreiter</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2410.07170'>here</a></p>
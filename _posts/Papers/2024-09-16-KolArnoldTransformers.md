---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Kolmogorov-Arnold Transformer
date: 2024-09-16
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Transformers stand as the cornerstone of mordern deep learning. Traditionally, these models rely on multi-layer perceptron (MLP) layers to mix the information between channels. In this paper, we introduce the Kolmogorov-Arnold Transformer (KAT), a novel architecture that replaces MLP layers with Kolmogorov-Arnold Network (KAN) layers to enhance the expressiveness and performance of the model. Integrating KANs into transformers, however, is no easy feat, especially when scaled up. Specifically, we identify three key challenges: (C1) Base function. The standard B-spline function used in KANs is not optimized for parallel computing on modern hardware, resulting in slower inference speeds. (C2) Parameter and Computation Inefficiency. KAN requires a unique function for each input-output pair, making the computation extremely large. (C3) Weight initialization. The initialization of weights in KANs is particularly challenging due to their learnable activation functions, which are critical for achieving convergence in deep neural networks. To overcome the aforementioned challenges, we propose three key solutions: (S1) Rational basis. We replace B-spline functions with rational functions to improve compatibility with modern GPUs. By implementing this in CUDA, we achieve faster computations. (S2) Group KAN. We share the activation weights through a group of neurons, to reduce the computational load without sacrificing performance. (S3) Variance-preserving initialization. We carefully initialize the activation weights to make sure that the activation variance is maintained across layers. With these designs, KAT scales effectively and readily outperforms traditional MLP-based transformers.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yang,+X">Xingyi Yang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Wang,+X">Xinchao Wang</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2409.10594'>here</a></p>
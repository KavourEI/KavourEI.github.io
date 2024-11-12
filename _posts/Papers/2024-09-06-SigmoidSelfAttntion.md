---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Theory, Analysis, and Best Practices for Sigmoid Self-Attention
date: 2024-09-06
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Attention is a key part of the transformer architecture. It is a sequence-to-sequence mapping that transforms each sequence element into a weighted sum of values. The weights are typically obtained as the softmax of dot products between keys and queries. Recent work has explored alternatives to softmax attention in transformers, such as ReLU and sigmoid activations. In this work, we revisit sigmoid attention and conduct an in-depth theoretical and empirical analysis. Theoretically, we prove that transformers with sigmoid attention are universal function approximators and benefit from improved regularity compared to softmax attention. Through detailed empirical analysis, we identify stabilization of large initial attention norms during the early stages of training as a crucial factor for the successful training of models with sigmoid attention, outperforming prior attempts. We also introduce FLASHSIGMOID, a hardware-aware and memory-efficient implementation of sigmoid attention yielding a 17% inference kernel speed-up over FLASHATTENTION2 on H100 GPUs. Experiments across language, vision, and speech show that properly normalized sigmoid attention matches the strong performance of softmax attention on a wide range of domains and scales, which previous attempts at sigmoid attention were unable to fully achieve. Our work unifies prior art and establishes best practices for sigmoid attention as a drop-in softmax replacement in transformers.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ramapuram,+J">Jason Ramapuram</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Danieli,+F">Federico Danieli</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Dhekane,+E">Eeshan Dhekane</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Weers,+F">Floris Weers</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Busbridge,+D">Dan Busbridge</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ablin,+P">Pierre Ablin</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Likhomanenko,+T">Tatiana Likhomanenko</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Digani,+J">Jagrit Digani</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Gu,+Z">Zijin Gu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Shidani,+A">Amitis Shidani</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Webb,+R">Russ Webb</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2409.04431'>here</a></p>
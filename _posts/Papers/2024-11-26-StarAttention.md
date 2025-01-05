---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Star Attention:Efficient LLM Inference over Long Sequences
date: 2024-11-26
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Inference with Transformer-based Large Language Models (LLMs) on long sequences is both costly and slow due to the quadratic complexity of the self-attention mechanism. We introduce Star Attention, a two-phase block-sparse approximation that improves computational efficiency by sharding attention across multiple hosts while minimizing communication overhead. In the first phase, the context is processed using blockwise-local attention across hosts, in parallel. In the second phase, query and response tokens attend to all prior cached tokens through sequence-global attention. Star Attention integrates seamlessly with most Transformer-based LLMs trained with global attention, reducing memory requirements and inference time by up to 11x while preserving 95-100% of accuracy. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Acharya,+S" rel="nofollow">Shantanu Acharya</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Jia,+F" rel="nofollow">Fei Jia</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ginsburg,+B" rel="nofollow">Boris Ginsburg</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2411.17116'>here</a></p>
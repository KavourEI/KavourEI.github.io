---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Mixture-of-Transformers:A Sparse and Scalable Architecture for Multi-Modal Foundation Models
date: 2024-11-09
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> The development of large language models (LLMs) has expanded to multi-modal systems capable of processing text, images, and speech within a unified framework. Training these models demands significantly larger datasets and computational resources compared to text-only LLMs. To address the scaling challenges, we introduce Mixture-of-Transformers (MoT), a sparse multi-modal transformer architecture that significantly reduces pretraining computational costs. MoT decouples non-embedding parameters of the model by modality -- including feed-forward networks, attention matrices, and layer normalization -- enabling modality-specific processing with global self-attention over the full input sequence. We evaluate MoT across multiple settings and model scales. In the Chameleon 7B setting (autoregressive text-and-image generation), MoT matches the dense baseline's performance using only 55.8\% of the FLOPs. When extended to include speech, MoT reaches speech performance comparable to the dense baseline with only 37.2\% of the FLOPs. In the Transfusion setting, where text and image are trained with different objectives, a 7B MoT model matches the image modality performance of the dense baseline with one third of the FLOPs, and a 760M MoT model outperforms a 1.4B dense baseline across key image generation metrics. System profiling further highlights MoT's practical benefits, achieving dense baseline image quality in 47.2\% of the wall-clock time and text quality in 75.6\% of the wall-clock time (measured on AWS p4de.24xlarge instances with NVIDIA A100 GPUs). </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Liang,+W" rel="nofollow">Weixin Liang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yu,+L" rel="nofollow">Lili Yu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Luo,+L" rel="nofollow">Liang Luo</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Iyer,+S" rel="nofollow">Srinivasan Iyer</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Dong,+N" rel="nofollow">Ning Dong</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhou,+C" rel="nofollow">Chunting Zhou</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ghosh,+G" rel="nofollow">Gargi Ghosh</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Lewis,+M" rel="nofollow">Mike Lewis</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yih,+W" rel="nofollow">Wen-tau Yih</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zettlemoyer,+L" rel="nofollow">Luke Zettlemoyer</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Lin,+X+V" rel="nofollow">Xi Victoria Lin</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2411.04996'>here</a></p>
---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Scaling Laws For Diffusion Transformers
date: 2024-10-10
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Diffusion transformers (DiT) have already achieved appealing synthesis and scaling properties in content recreation, e.g., image and video generation. However, scaling laws of DiT are less explored, which usually offer precise predictions regarding optimal model size and data requirements given a specific compute budget. Therefore, experiments across a broad range of compute budgets, from 1e17 to 6e18 FLOPs are conducted to confirm the existence of scaling laws in DiT for the first time. Concretely, the loss of pretraining DiT also follows a power-law relationship with the involved compute. Based on the scaling law, we can not only determine the optimal model size and required data but also accurately predict the text-to-image generation loss given a model with 1B parameters and a compute budget of 1e21 FLOPs. Additionally, we also demonstrate that the trend of pre-training loss matches the generation performances (e.g., FID), even across various datasets, which complements the mapping from compute to synthesis quality and thus provides a predictable benchmark that assesses model performance and data quality at a reduced cost. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Liang,+Z">Zhengyang Liang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=He,+H">Hao He</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yang,+C">Ceyuan Yang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Dai,+B">Bo Dai</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2410.08184'>here</a></p>
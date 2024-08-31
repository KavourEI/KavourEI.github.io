---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: To Code, or Not To Code? Exploring Impact of Code in Pre-training
date: 2024-08-20
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Including code in the pre-training data mixture, even for models not specifically designed for code, has become a common practice in LLMs pre-training. While there has been anecdotal consensus among practitioners that code data plays a vital role in general LLMs’ performance, there is only limited work analyzing the precise impact of code on non-code tasks. In this work, we system- atically investigate the impact of code data on general performance. We ask “what is the impact of code data used in pre-training on a large variety of downstream tasks beyond code generation”. We conduct extensive ablations and evaluate across a broad range of natural language reasoning tasks, world knowledge tasks, code benchmarks, and LLM-as-a-judge win-rates for models with sizes ranging from 470M to 2.8B parameters. Across settings, we find a consistent results that code is a critical building block for generalization far beyond coding tasks and improvements to code quality have an outsized impact across all tasks. In particular, compared to text-only pre-training, the ad- dition of code results in up to relative increase of 8.2% in natural language (NL) reasoning, 4.2% in world knowledge, 6.6% improvement in generative win-rates, and a 12x boost in code performance respectively. Our work suggests investments in code quality and preserving code during pre-training have positive impacts.</p>

<h2> Authors </h2>

<p> CViraat Aryabumi, Yixuan Su, Raymond Ma, Adrien Morisot, Ivan Zhang, Acyr Locatelli, Marzieh Fadaee, Ahmet Üstün, and Sara Hooker1</p>

<p>For more information go <a href='https://arxiv.org/pdf/2408.10914'>here</a></p>
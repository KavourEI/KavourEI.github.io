---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Differential Transformer
date: 2024-10-07
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Transformer tends to overallocate attention to irrelevant context. In this work, we introduce Diff Transformer, which amplifies attention to the relevant context while canceling noise. Specifically, the differential attention mechanism calculates attention scores as the difference between two separate softmax attention maps. The subtraction cancels noise, promoting the emergence of sparse attention patterns. Experimental results on language modeling show that Diff Transformer outperforms Transformer in various settings of scaling up model size and training tokens. More intriguingly, it offers notable advantages in practical applications, such as long-context modeling, key information retrieval, hallucination mitigation, in-context learning, and reduction of activation outliers. By being less distracted by irrelevant context, Diff Transformer can mitigate hallucination in question answering and text summarization. For in-context learning, Diff Transformer not only enhances accuracy but is also more robust to order permutation, which was considered as a chronic robustness issue. The results position Diff Transformer as a highly effective and promising architecture to advance large language models.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ye,+T">Tianzhu Ye</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Dong,+L">Li Dong</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Xia,+Y">Yuqing Xia</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Sun,+Y">Yutao Sun</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhu,+Y">Yi Zhu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Huang,+G">Gao Huang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Wei,+F">Furu Wei</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2410.05258'>here</a></p>
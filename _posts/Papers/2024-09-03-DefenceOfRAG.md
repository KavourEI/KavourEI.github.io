---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: In Defense of RAG in the Era of Long-Context Language Models
date: 2024-09-03
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Overcoming the limited context limitations in early-generation LLMs, retrieval-augmented generation (RAG) has been a reliable solution for context-based answer generation in the past. Recently, the emergence of long-context LLMs allows the models to incorporate much longer text sequences, making RAG less attractive. Recent studies show that long-context LLMs significantly outperform RAG in long-context applications. Unlike the existing works favoring the long-context LLM over RAG, we argue that the extremely long context in LLMs suffers from a diminished focus on relevant information and leads to potential degradation in answer quality. This paper revisits the RAG in long-context answer generation. We propose an order-preserve retrieval-augmented generation (OP-RAG) mechanism, which significantly improves the performance of RAG for long-context question-answer applications. With OP-RAG, as the number of retrieved chunks increases, the answer quality initially rises, and then declines, forming an inverted U-shaped curve. There exist sweet points where OP-RAG could achieve higher answer quality with much less tokens than long-context LLM taking the whole context as input. Extensive experiments on public benchmark demonstrate the superiority of our OP-RAG.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Akkiraju,+R">Rama Akkiraju</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yu,+T">Tan Yu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Xu,+A">Anbang Xu</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2409.01666'>here</a></p>
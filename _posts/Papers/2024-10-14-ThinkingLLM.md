---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Thinking LLMs:General Instruction Following with Thought Generation
date: 2024-10-14
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> LLMs are typically trained to answer user questions or follow instructions similarly to how human experts respond. However, in the standard alignment framework they lack the basic ability of explicit thinking before answering. Thinking is important for complex questions that require reasoning and planning -- but can be applied to any task. We propose a training method for equipping existing LLMs with such thinking abilities for general instruction following without use of additional human data. We achieve this by an iterative search and optimization procedure that explores the space of possible thought generations, allowing the model to learn how to think without direct supervision. For each instruction, the thought candidates are scored using a judge model to evaluate their responses only, and then optimized via preference optimization. We show that this procedure leads to superior performance on AlpacaEval and Arena-Hard, and shows gains from thinking on non-reasoning categories such as marketing, health and general knowledge, in addition to more traditional reasoning & problem-solving tasks. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Wu,+T">Tianhao Wu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Lan,+J">Janice Lan</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yuan,+W">Weizhe Yuan</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Jiao,+J">Jiantao Jiao</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Weston,+J">Jason Weston</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Sukhbaatar,+S">Sainbayar Sukhbaatar</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2410.10630'>here</a></p>
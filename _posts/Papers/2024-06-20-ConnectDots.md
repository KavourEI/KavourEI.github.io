---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Connecting the Dots - LLMs can Infer and Verbalize Latent Structure from Disparate Training Data
date: 2024-06-20
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p>One way to address safety risks from large language models (LLMs) is to censor dangerous knowledge from their training data. While this removes the explicit information, implicit information can remain scattered across various training documents. Could an LLM infer the censored knowledge by piecing together these implicit hints? As a step towards answering this question, we study inductive out-of-context reasoning (OOCR), a type of generalization in which LLMs infer latent information from evidence distributed across training documents and apply it to downstream tasks without in-context learning. Using a suite of five tasks, we demonstrate that frontier LLMs can perform inductive OOCR. In one experiment we finetune an LLM on a corpus consisting only of distances between an unknown city and other known cities. Remarkably, without in-context examples or Chain of Thought, the LLM can verbalize that the unknown city is Paris and use this fact to answer downstream questions. Further experiments show that LLMs trained only on individual coin flip outcomes can verbalize whether the coin is biased, and those trained only on pairs (x,f(x)) can articulate a definition of f and compute inverses. While OOCR succeeds in a range of cases, we also show that it is unreliable, particularly for smaller LLMs learning complex structures. Overall, the ability of LLMs to "connect the dots" without explicit in-context learning poses a potential obstacle to monitoring and controlling the knowledge acquired by LLMs.</p>

<p>For more information go <a href='https://arxiv.org/abs/2406.14546'>here</a></p>
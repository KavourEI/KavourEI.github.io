---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Automating Thought of Search - A Journey Towards Soundness and Completeness
date: 2024-08-20
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Planning remains one of the last standing bastions for large language models (LLMs), which now turn their attention to search. Most of the literature uses the language models as world models to define the search space, forgoing soundness for the sake of flexibility. A recent work, Thought of Search (ToS), proposed defining the search space with code, having the language models produce that code. ToS requires a human in the loop, collaboratively producing a sound successor func- tion and goal test. The result, however, is worth the effort: all the tested datasets were solved with 100% accuracy. At the same time LLMs have demonstrated significant progress in code generation and refinement for complex reasoning tasks.
In this work, we automate ToS (AutoToS), completely tak- ing the human out of the loop of solving planning problems. AutoToS guides the language model step by step towards the generation of sound and complete search components, through feedback from both generic and domain specific unit tests. We achieve 100% accuracy, with minimal feedback iter- ations, using LLMs of various sizes on all evaluated domains.</p>

<h2> Authors </h2>

<p> Daniel Cao, Michael Katz, Harsha Kokel, Kavitha Srinivas, Shirin Sohrabi</p>

<p>For more information go <a href='https://arxiv.org/pdf/2408.11326'>here</a></p>
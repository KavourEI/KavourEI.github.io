---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Learn-by-interact A Data-Centric Framework for Self-Adaptive Agents in Realistic Environments
date: 2025-01-18
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Autonomous agents powered by large language models (LLMs) have the potential to enhance human capabilities, assisting with digital tasks from sending emails to performing data analysis. The abilities of existing LLMs at such tasks are often hindered by the lack of high-quality agent data from the corresponding environments they interact with. We propose Learn-by-interact, a data-centric framework to adapt LLM agents to any given environments without human annotations. Learn-by-interact synthesizes trajectories of agent-environment interactions based on documentations, and constructs instructions by summarizing or abstracting the interaction histories, a process called backward construction. We assess the quality of our synthetic data by using them in both training-based scenarios and training-free in-context learning (ICL), where we craft innovative retrieval approaches optimized for agents. Extensive experiments on SWE-bench, WebArena, OSWorld and Spider2-V spanning across realistic coding, web, and desktop environments show the effectiveness of Learn-by-interact in various downstream agentic tasks -- baseline results are improved by up to 12.2\% for ICL with Claude-3.5 and 19.5\% for training with Codestral-22B. We further demonstrate the critical role of backward construction, which provides up to 14.0\% improvement for training. Our ablation studies demonstrate the efficiency provided by our synthesized data in ICL and the superiority of our retrieval pipeline over alternative approaches like conventional retrieval-augmented generation (RAG). We expect that Learn-by-interact will serve as a foundation for agent data synthesis as LLMs are increasingly deployed at real-world environments. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Su,+H" rel="nofollow">Hongjin Su</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Sun,+R" rel="nofollow">Ruoxi Sun</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yoon,+J" rel="nofollow">Jinsung Yoon</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yin,+P" rel="nofollow">Pengcheng Yin</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yu,+T" rel="nofollow">Tao Yu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ar%C4%B1k,+S+%C3%96" rel="nofollow">Sercan Ö. Arık</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2501.10893'>here</a></p>
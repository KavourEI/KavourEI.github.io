---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Logic-of-Thought. Injecting Logic into Contexts for Full Reasoning in Large Language Models
date: 2024-09-30
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Reinforcement learning from human feedback (RLHF) has become the leading approach for fine-tuning large language models (LLM). However, RLHF has limitations in multi-task learning (MTL) due to challenges of reward hacking and extreme multi-objective optimization (i.e., trade-off of multiple and/or sometimes conflicting objectives). Applying RLHF for MTL currently requires careful tuning of the weights for reward model and data combinations. This is often done via human intuition and does not generalize. In this work, we introduce a novel post-training paradigm which we called Constrained Generative Policy Optimization (CGPO). The core of CGPO is Mixture of Judges (MoJ) with cost-efficient constrained policy optimization with stratification, which can identify the perfect blend in RLHF in a principled manner. It shows strong empirical results with theoretical guarantees, does not require extensive hyper-parameter tuning, and is plug-and-play in common post-training pipelines. Together, this can detect and mitigate reward hacking behaviors while reaching a pareto-optimal point across an extremely large number of objectives.
Our empirical evaluations demonstrate that CGPO significantly outperforms standard RLHF algorithms like PPO and DPO across various tasks including general chat, STEM questions, instruction following, and coding. Specifically, CGPO shows improvements of 7.4% in AlpacaEval-2 (general chat), 12.5% in Arena-Hard (STEM & reasoning), and consistent gains in other domains like math and coding. Notably, PPO, while commonly used, is prone to severe reward hacking in popular coding benchmarks, which CGPO successfully addresses. This breakthrough in RLHF not only tackles reward hacking and extreme multi-objective optimization challenges but also advances the state-of-the-art in aligning general-purpose LLMs for diverse applications.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Xu,+T">Tengyu Xu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Helenowski,+E">Eryk Helenowski</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Sankararaman,+K+A">Karthik Abinav Sankararaman</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Jin,+D">Di Jin</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Peng,+K">Kaiyan Peng</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Han,+E">Eric Han</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Nie,+S">Shaoliang Nie</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhu,+C">Chen Zhu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhang,+H">Hejia Zhang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhou,+W">Wenxuan Zhou</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zeng,+Z">Zhouhao Zeng</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=He,+Y">Yun He</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Mandyam,+K">Karishma Mandyam</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Talabzadeh,+A">Arya Talabzadeh</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Khabsa,+M">Madian Khabsa</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Cohen,+G">Gabriel Cohen</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Tian,+Y">Yuandong Tian</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ma,+H">Hao Ma</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Wang,+S">Sinong Wang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Fang,+H">Han Fang</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2409.20370'>here</a></p>
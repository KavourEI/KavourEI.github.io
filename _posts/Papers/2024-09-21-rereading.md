---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Rereading Improves Reasoning in Large Language Models
date: 2024-09-21
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> To enhance the reasoning capabilities of off-the-shelf Large Language Models (LLMs), we introduce a simple, yet general and effective prompting method, Re2, i.e., <strong>Re</strong>-<strong>Re</strong>ading the question as input. Unlike most thought-eliciting prompting methods, such as Chain-of-Thought (CoT), which aim to elicit the reasoning process in the output, Re2 shifts the focus to the input by processing questions twice, thereby enhancing the understanding process. Consequently, Re2 demonstrates strong generality and compatibility with most thought-eliciting prompting methods, including CoT. Crucially, Re2 facilitates a "bidirectional" encoding in unidirectional decoder-only LLMs because the first pass could provide global information for the second pass. We begin with a preliminary empirical study as the foundation of Re2, illustrating its potential to enable "bidirectional" attention mechanisms. We then evaluate Re2 on extensive reasoning benchmarks across 14 datasets, spanning 112 experiments, to validate its effectiveness and generality. Our findings indicate that, with the exception of a few scenarios on vanilla ChatGPT, Re2 consistently enhances the reasoning performance of LLMs through a simple re-reading strategy. Further analyses reveal Re2's adaptability, showing how it can be effectively integrated with different LLMs, thought-eliciting prompting, and ensemble strategies. Our code is available at <a href="https://github.com/Tebmer/Rereading-LLM-Reasoning/">this https URL</a>.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Xu,+X">Xiaohan Xu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Tao,+C">Chongyang Tao</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Shen,+T">Tao Shen</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Xu,+C">Can Xu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Xu,+H">Hongbo Xu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Long,+G">Guodong Long</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Lou,+J">Jian-guang Lou</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ma,+S">Shuai Ma</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2309.06275'>here</a></p>
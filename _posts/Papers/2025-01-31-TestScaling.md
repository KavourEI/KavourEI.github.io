---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: s1-Simple test-time scaling
date: 2025-01-31
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Test-time scaling is a promising new approach to language modeling that uses extra test-time compute to improve performance. Recently, OpenAI's o1 model showed this capability but did not publicly share its methodology, leading to many replication efforts. We seek the simplest approach to achieve test-time scaling and strong reasoning performance. First, we curate a small dataset s1K of 1,000 questions paired with reasoning traces relying on three criteria we validate through ablations: difficulty, diversity, and quality. Second, we develop budget forcing to control test-time compute by forcefully terminating the model's thinking process or lengthening it by appending "Wait" multiple times to the model's generation when it tries to end. This can lead the model to double-check its answer, often fixing incorrect reasoning steps. After supervised finetuning the Qwen2.5-32B-Instruct language model on s1K and equipping it with budget forcing, our model s1-32B exceeds o1-preview on competition math questions by up to 27% (MATH and AIME24). Further, scaling s1-32B with budget forcing allows extrapolating beyond its performance without test-time intervention: from 50% to 57% on AIME24. Our model, data, and code are open-source at <a href='https://github.com/simplescaling/s1'>this https URL</a>. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Muennighoff,+N" rel="nofollow">Niklas Muennighoff</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yang,+Z" rel="nofollow">Zitong Yang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Shi,+W" rel="nofollow">Weijia Shi</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Li,+X+L" rel="nofollow">Xiang Lisa Li</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Fei-Fei,+L" rel="nofollow">Li Fei-Fei</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Hajishirzi,+H" rel="nofollow">Hannaneh Hajishirzi</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zettlemoyer,+L" rel="nofollow">Luke Zettlemoyer</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Liang,+P" rel="nofollow">Percy Liang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Cand%C3%A8s,+E" rel="nofollow">Emmanuel Candès</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Hashimoto,+T" rel="nofollow">Tatsunori Hashimoto</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2501.19393'>here</a></p>
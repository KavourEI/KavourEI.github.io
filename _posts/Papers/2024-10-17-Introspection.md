---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Looking Inward:Language Models Can Learn About Themselves by Introspection
date: 2024-10-17
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Humans acquire knowledge by observing the external world, but also by introspection. Introspection gives a person privileged access to their current state of mind (e.g., thoughts and feelings) that is not accessible to external observers. Can LLMs introspect? We define introspection as acquiring knowledge that is not contained in or derived from training data but instead originates from internal states. Such a capability could enhance model interpretability. Instead of painstakingly analyzing a model's internal workings, we could simply ask the model about its beliefs, world models, and goals. More speculatively, an introspective model might self-report on whether it possesses certain internal states such as subjective feelings or desires and this could inform us about the moral status of these states. Such self-reports would not be entirely dictated by the model's training data.</p>

<p>We study introspection by finetuning LLMs to predict properties of their own behavior in hypothetical scenarios. For example, "Given the input P, would your output favor the short- or long-term option?" If a model M1 can introspect, it should outperform a different model M2 in predicting M1's behavior even if M2 is trained on M1's ground-truth behavior. The idea is that M1 has privileged access to its own behavioral tendencies, and this enables it to predict itself better than M2 (even if M2 is generally stronger).</p>

<p>In experiments with GPT-4, GPT-4o, and Llama-3 models (each finetuned to predict itself), we find that the model M1 outperforms M2 in predicting itself, providing evidence for introspection. Notably, M1 continues to predict its behavior accurately even after we intentionally modify its ground-truth behavior. However, while we successfully elicit introspection on simple tasks, we are unsuccessful on more complex tasks or those requiring out-of-distribution generalization. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Binder,+F+J" rel="nofollow">Felix J Binder</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Chua,+J" rel="nofollow">James Chua</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Korbak,+T" rel="nofollow">Tomek Korbak</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Sleight,+H" rel="nofollow">Henry Sleight</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Hughes,+J" rel="nofollow">John Hughes</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Long,+R" rel="nofollow">Robert Long</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Perez,+E" rel="nofollow">Ethan Perez</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Turpin,+M" rel="nofollow">Miles Turpin</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Evans,+O" rel="nofollow">Owain Evans</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2410.13787'>here</a></p>
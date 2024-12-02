---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Rapid Response:Mitigating LLM Jailbreaks with a Few Examples
date: 2024-11-12
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> As large language models (LLMs) grow more powerful, ensuring their safety against misuse becomes crucial. While researchers have focused on developing robust defenses, no method has yet achieved complete invulnerability to attacks. We propose an alternative approach: instead of seeking perfect adversarial robustness, we develop rapid response techniques to look to block whole classes of jailbreaks after observing only a handful of attacks. To study this setting, we develop RapidResponseBench, a benchmark that measures a defense's robustness against various jailbreak strategies after adapting to a few observed examples. We evaluate five rapid response methods, all of which use jailbreak proliferation, where we automatically generate additional jailbreaks similar to the examples observed. Our strongest method, which fine-tunes an input classifier to block proliferated jailbreaks, reduces attack success rate by a factor greater than 240 on an in-distribution set of jailbreaks and a factor greater than 15 on an out-of-distribution set, having observed just one example of each jailbreaking strategy. Moreover, further studies suggest that the quality of proliferation model and number of proliferated examples play an key role in the effectiveness of this defense. Overall, our results highlight the potential of responding rapidly to novel jailbreaks to limit LLM misuse. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Peng,+A" rel="nofollow">Alwin Peng</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Michael,+J" rel="nofollow">Julian Michael</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Sleight,+H" rel="nofollow">Henry Sleight</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Perez,+E" rel="nofollow">Ethan Perez</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Sharma,+M" rel="nofollow">Mrinank Sharma</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2411.07494'>here</a></p>
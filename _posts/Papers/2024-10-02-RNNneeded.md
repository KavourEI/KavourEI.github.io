---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Were RNNs All We Needed?
date: 2024-10-02
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> The scalability limitations of Transformers regarding sequence length have renewed interest in recurrent sequence models that are parallelizable during training. As a result, many novel recurrent architectures, such as S4, Mamba, and Aaren, have been proposed that achieve comparable performance. In this work, we revisit traditional recurrent neural networks (RNNs) from over a decade ago: LSTMs (1997) and GRUs (2014). While these models were slow due to requiring to backpropagate through time (BPTT), we show that by removing their hidden state dependencies from their input, forget, and update gates, LSTMs and GRUs no longer need to BPTT and can be efficiently trained in parallel. Building on this, we introduce minimal versions (minLSTMs and minGRUs) that (1) use significantly fewer parameters than their traditional counterparts and (2) are fully parallelizable during training (175x faster for a sequence of length 512). Lastly, we show that these stripped-down versions of decade-old RNNs match the empirical performance of recent sequence models.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Feng,+L">Leo Feng</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Tung,+F">Frederick Tung</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ahmed,+M+O">Mohamed Osama Ahmed</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Bengio,+Y">Yoshua Bengio</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Hajimirsadegh,+H">Hossein Hajimirsadegh</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2410.01201'>here</a></p>
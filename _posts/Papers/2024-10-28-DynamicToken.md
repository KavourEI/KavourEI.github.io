---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: MrT5:Dynamic Token Merging for Efficient Byte-level Language Models
date: 2024-10-28
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Models that rely on subword tokenization have significant drawbacks, such as sensitivity to character-level noise like spelling errors and inconsistent compression rates across different languages and scripts. While character- or byte-level models like ByT5 attempt to address these concerns, they have not gained widespread adoption -- processing raw byte streams without tokenization results in significantly longer sequence lengths, making training and inference inefficient. This work introduces MrT5 (MergeT5), a more efficient variant of ByT5 that integrates a token deletion mechanism in its encoder to dynamically shorten the input sequence length. After processing through a fixed number of encoder layers, a learnt delete gate determines which tokens are to be removed and which are to be retained for subsequent layers. MrT5 effectively ``merges'' critical information from deleted tokens into a more compact sequence, leveraging contextual information from the remaining tokens. In continued pre-training experiments, we find that MrT5 can achieve significant gains in inference runtime with minimal effect on performance. When trained on English text, MrT5 demonstrates the capability to transfer its deletion feature zero-shot across several languages, with significant additional improvements following multilingual training. Furthermore, MrT5 shows comparable accuracy to ByT5 on downstream evaluations such as XNLI and character-level tasks while reducing sequence lengths by up to 80%. Our approach presents a solution to the practical limitations of existing byte-level models. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Kallini,+J" rel="nofollow">Julie Kallini</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Murty,+S" rel="nofollow">Shikhar Murty</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Manning,+C+D" rel="nofollow">Christopher D. Manning</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Potts,+C" rel="nofollow">Christopher Potts</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Csord%C3%A1s,+R" rel="nofollow">Róbert Csordás</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2410.20771'>here</a></p>
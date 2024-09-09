---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: FLUX that Plays Music
date: 2024-09-01
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> This paper explores a simple extension of diffusion-based rectified flow Transformers for text-to-music generation, termed as FluxMusic. Generally, along with design in advanced Flux\footnote{this https URL} model, we transfers it into a latent VAE space of mel-spectrum. It involves first applying a sequence of independent attention to the double text-music stream, followed by a stacked single music stream for denoised patch prediction. We employ multiple pre-trained text encoders to sufficiently capture caption semantic information as well as inference flexibility. In between, coarse textual information, in conjunction with time step embeddings, is utilized in a modulation mechanism, while fine-grained textual details are concatenated with the music patch sequence as inputs. Through an in-depth study, we demonstrate that rectified flow training with an optimized architecture significantly outperforms established diffusion methods for the text-to-music task, as evidenced by various automatic metrics and human preference evaluations. Our experimental data, code, and model weights are made publicly available at: <a href='https://github.com/feizc/FluxMusic'>this URL</a>.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Fei,+Z">Zhengcong Fei</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Fan,+M">Mingyuan Fan</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Yu,+C">Changqian Yu</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Huang,+J">Junshi Huang</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2409.00587'>here</a></p>
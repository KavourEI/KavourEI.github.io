---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Depth Anything V2
date: 2024-06-13
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<p> <a href="https://arxiv.org/abs/2406.07522">Samba</a> architecture achieves 3.73x faster throughput with enhanced context</p>

<h2> Abstract </h2>

<p>This work presents Depth Anything V2. Without pursuing fancy techniques, we aim to reveal crucial findings to pave the way towards building a powerful monocular depth estimation model. Notably, compared with V1, this version produces much finer and more robust depth predictions through three key practices: 1&rpar; replacing all labeled real images with synthetic images, 2&rpar; scaling up the capacity of our teacher model, and 3&rpar; teaching student models via the bridge of large-scale pseudo-labeled real images. Compared with the latest models built on Stable Diffusion, our models are significantly more efficient (more than 10x faster) and more accurate. We offer models of different scales (ranging from 25M to 1.3B params) to support extensive scenarios. Benefiting from their strong generalization capability, we fine-tune them with metric depth labels to obtain our metric depth models. In addition to our models, considering the limited diversity and frequent noise in current test sets, we construct a versatile evaluation benchmark with precise annotations and diverse scenes to facilitate future research.</p>

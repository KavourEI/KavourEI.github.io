---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Simplifying, Stabilizing and Scaling Continuous-Time Consistency Models
date: 2024-10-16
tags: [research]
class: post-templat
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Consistency models (CMs) are a powerful class of diffusion-based generative models optimized for fast sampling. Most existing CMs are trained using discretized timesteps, which introduce additional hyperparameters and are prone to discretization errors. While continuous-time formulations can mitigate these issues, their success has been limited by training instability. To address this, we propose a simplified theoretical framework that unifies previous parameterizations of diffusion models and CMs, identifying the root causes of instability. Based on this analysis, we introduce key improvements in diffusion process parameterization, network architecture, and training objectives. These changes enable us to train continuous-time CMs at an unprecedented scale, reaching 1.5B parameters on ImageNet 512x512. Our proposed training algorithm, using only two sampling steps, achieves FID scores of 2.06 on CIFAR-10, 1.48 on ImageNet 64x64, and 1.88 on ImageNet 512x512, narrowing the gap in FID scores with the best existing diffusion models to within 10%. </p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Lu,+C" rel="nofollow">Cheng Lu</a>
, 
<a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Song,+Y" rel="nofollow">Yang Song</a> </p>

<p>For more information go <a href='https://arxiv.org/abs/2410.11081'>here</a></p>
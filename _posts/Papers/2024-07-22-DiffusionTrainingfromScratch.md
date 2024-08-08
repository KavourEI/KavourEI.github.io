---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Stretching Each Dollar- Diffusion Training from Scratch on a Micro-Budget
date: 2024-07-22
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p>As scaling laws in generative AI push performance, they also simultaneously concentrate the development of these models among actors with large computational resources. With a focus on text-to-image (T2I) generative models, we aim to address this bottleneck by demonstrating very low-cost training of large-scale T2I diffusion transformer models. As the computational cost of transformers increases with the number of patches in each image, we propose to randomly mask up to 75% of the image patches during training. We propose a deferred masking strategy that preprocesses all patches using a patch-mixer before masking, thus significantly reducing the performance degradation with masking, making it superior to model downscaling in reducing computational cost. We also incorporate the latest improvements in transformer architecture, such as the use of mixture-of-experts layers, to improve performance and further identify the critical benefit of using synthetic images in micro-budget training. Finally, using only 37M publicly available real and synthetic images, we train a 1.16 billion parameter sparse transformer with only $1,890 economical cost and achieve a 12.7 FID in zero-shot generation on the COCO dataset. Notably, our model achieves competitive FID and high-quality generations while incurring 118× lower cost than stable diffusion models and 14× lower cost than the current state-of-the-art approach that costs $28,400. We aim to release our end-to-end training pipeline to further democratize the training of large-scale diffusion models on micro-budgets.</p>

<p>For more information go <a href='https://arxiv.org/abs/2407.15811'>here</a></p>
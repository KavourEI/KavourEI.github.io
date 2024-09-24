---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: LLaMA-Omni - Seamless Speech Interaction with Large Language Models
date: 2024-09-10
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Models like GPT-4o enable real-time interaction with large language models (LLMs) through speech, significantly enhancing user experience compared to traditional text-based interaction. However, there is still a lack of exploration on how to build speech interaction models based on open-source LLMs. To address this, we propose LLaMA-Omni, a novel model architecture designed for low-latency and high-quality speech interaction with LLMs. LLaMA-Omni integrates a pretrained speech encoder, a speech adaptor, an LLM, and a streaming speech decoder. It eliminates the need for speech transcription, and can simultaneously generate text and speech responses directly from speech instructions with extremely low latency. We build our model based on the latest Llama-3.1-8B-Instruct model. To align the model with speech interaction scenarios, we construct a dataset named InstructS2S-200K, which includes 200K speech instructions and corresponding speech responses. Experimental results show that compared to previous speech-language models, LLaMA-Omni provides better responses in both content and style, with a response latency as low as 226ms. Additionally, training LLaMA-Omni takes less than 3 days on just 4 GPUs, paving the way for the efficient development of speech-language models in the future.</p>

<h2> Authors </h2>

<p> <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Fang,+Q">Qingkai Fang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Guo,+S">Shoutao Guo</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhou,+Y">Yan Zhou</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Ma,+Z">Zhengrui Ma</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Zhang,+S">Shaolei Zhang</a>, <a href="https://arxiv.org/search/cs?searchtype=author&amp;query=Feng,+Y">Yang Feng</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2409.06666'>here</a></p>
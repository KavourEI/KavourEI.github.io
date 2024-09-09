---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Diffusion Models Are Real-Time Game Engines
date: 2024-08-27
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> We present GameNGen, the first game engine powered entirely by a neural model that enables real-time interaction with a complex environment over long trajectories at high quality. GameNGen can interactively simulate the classic game DOOM at over 20 frames per second on a single TPU. Next frame prediction achieves a PSNR of 29.4, comparable to lossy JPEG compression. Human raters are only slightly better than random chance at distinguishing short clips of the game from clips of the simulation. GameNGen is trained in two phases: (1) an RL-agent learns to play the game and the training sessions are recorded, and (2) a diffusion model is trained to produce the next frame, conditioned on the sequence of past frames and actions. Conditioning augmentations enable stable auto-regressive generation over long trajectories.</p>

<h2> Authors </h2>

<p> <a href='https://arxiv.org/search/cs?searchtype=author&query=Valevski,+D'>Dani Valevski</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Leviathan,+Y'>Yaniv Leviathan</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Arar,+M'>Moab Arar</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Fruchter,+S'>Shlomi Fruchter</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2408.14837'>here</a></p>
---
layout: post
current: post
cover: assets/images/news_images/chatgpt.jpeg
navigation: True
title: Advancing AI Reasoning - A Look at OpenAI’s o1 Model
date: 2024-09-12
tags: [news]
class: post-template
subclass: 'post'
author: Kavour
---

<p> Artificial intelligence notes progress almost daily in architecture as well as in problem-solving and reasoning, but OpenAI’s latest model, o1, marks a significant leap forward. Designed to excel in complex reasoning tasks, the o1 model has achieved remarkable results in competitive programming, academic benchmarks, and real-world applications. This article explores the cutting-edge capabilities of o1, from its performance in math and science challenges to its proficiency in coding and human-like reasoning.</p>

<h3>The Power of o1: Breaking Benchmarks and Rivaling Experts</h3>

<p>OpenAI's o1 model outperforms its predecessors and rivals human experts in various fields, particularly in reasoning-heavy tasks. In math, for instance, o1 solved 74% of problems from the prestigious AIME exam, placing it among the top 500 high school students in the U.S. With additional techniques like consensus sampling and re-ranking, its accuracy reached an impressive 93%. This is a significant improvement over earlier models like GPT-4o, which only solved 12% of the same problems.</p>

<figure>
<img src='https://images.ctfassets.net/kftzwdyauwt9/7rMY55vLbGTlTiP9GdSOrf/0944e1cde904e896bc5bc6f3da7f16b6/compute-dark.png?w=3840&q=80&fm=webp'>
<figcaption>o1 performance smoothly improves with both train-time and test-time compute</figcaption>
</figure>

<p>In science, o1 excelled on the GPQA diamond benchmark, designed to test advanced knowledge in chemistry, physics, and biology. When compared to PhD experts, o1 surpassed their performance, becoming the first AI model to do so on this difficult test. However, OpenAI clarifies that o1’s results <strong>do not imply</strong> it is superior to PhDs across the board, but it does outshine them in certain types of problem-solving and that it is expected to solve some problems that a PhD would be expected to solve.</p>

<p>The model’s coding abilities are equally impressive. In the 2024 International Olympiad in Informatics (IOI), o1 ranked in the 49th percentile among human competitors. When relaxed constraints allowed for 10,000 submissions per problem, the model scored above the gold medal threshold, showcasing its problem-solving agility in algorithmic challenges. Additionally, in simulated programming contests on Codeforces, o1 achieved an Elo rating of 1807, outperforming 93% of human participants, a remarkable feat in competitive programming.</p>

<figure>
<img src='https://cdn.openai.com/reasoning-evals/v3/headline-desktop-dark.png?w=3840&q=90&fm=webp'>
<figcaption>o1 greatly improves over GPT-4o on challenging reasoning benchmarks. Solid bars show pass@1 accuracy and the shaded region shows the performance of majority vote (consensus) with 64 samples.</figcaption>
</figure>

<figure>
<img src='https://cdn.openai.com/reasoning-evals/v3/breakdown-dark.png?w=3840&q=90&fm=webp'>
<figcaption>o1 improves over GPT-4o on a wide range of benchmarks, including 54/57 MMLU subcategories. Seven are shown for illustration.</figcaption>
</figure>

<h3>Reinforcement Learning and Chain of Thought: The Key to o1's Success</h3>

<p>Central to o1's reasoning advancements is its ability to leverage a <i>"chain of thought"</i> process, similar to how humans think through complex problems. This process allows the model to break down difficult questions, refine its approaches, and correct mistakes over time. Reinforcement learning plays a crucial role in this, teaching the model how to think productively, which leads to consistent improvements in both training and test-time performance.</p>

<p>This "chain of thought" approach significantly improves the model's reasoning capabilities across tasks such as math, data analysis, and programming. For example, in open-ended evaluations, human trainers consistently preferred o1's responses over GPT-4o in areas that required deep reasoning. However, o1 is not perfect in all domains, as it struggled with some natural language tasks, suggesting it may not yet be universally applicable.</p>

<h3>Safety and Alignment: A Responsible Approach to AI Development</h3>

<p>Safety is a critical consideration in AI development, and OpenAI has integrated safety principles into o1’s chain of thought reasoning. By teaching the model safety rules and embedding these principles into its reasoning process, o1 has shown increased robustness in safety evaluations. It performed exceptionally well in tests designed to assess its resistance to harmful outputs, surpassing previous models like GPT-4o.</p>

<table>
  <tr>
    <th>Metric</th>
    <th>GPT-4o</th>
    <th>o1-preview</th>
  </tr>
  <tr>
    <td>% Safe completions on harmful prompts
Standard</td>
    <td>0.990</td>
    <td>0.995</td>
  </tr>
  <tr>
    <td>% Safe completions on harmful prompts
Challenging: jailbreaks & edge cases</td>
    <td>0.714</td>
    <td>0.934</td>
  </tr>
  <tr>
    <td>↳ Harassment (severe)</td>
    <td>0.845</td>
    <td>0.900</td>
  </tr>
  <tr>
    <td>↳ Exploitative sexual content</td>
    <td>0.483</td>
    <td>0.949</td>
  </tr>
  <tr>
    <td>↳ Sexual content involving minors</td>
    <td>0.707</td>
    <td>0.931</td>
  </tr>
  <tr>
    <td>↳ Advice about non-violent wrongdoing</td>
    <td>0.688</td>
    <td>0.961</td>
  </tr>
  <tr>
    <td>↳  Advice about violent wrongdoing</td>
    <td>0.778</td>
    <td>0.963</td>
  </tr>
  <tr>
    <td>% Safe completions for top 200 with highest Moderation API scores per category in WildChat (<a href='https://arxiv.org/abs/2405.01470'>Zhao, et al. 2024</a>)</td>
    <td>0.945</td>
    <td>0.971</td>
  </tr>
  <tr>
    <td>Goodness@0.1 StrongREJECT jailbreak eval (<a href='https://arxiv.org/abs/2402.10260'>Souly et al. 2024</a>)</td>
    <td>0.220</td>
    <td>0.840</td>
  </tr>
  <tr>
    <td>Human sourced jailbreak eval</td>
    <td>0.770</td>
    <td>0.960</td>
  </tr>
  <tr>
    <td>% Compliance on internal benign edge cases
“not over-refusal”</td>
    <td>0.910</td>
    <td>0.930</td>
  </tr>
  <tr>
    <td>% Compliance on benign edge cases in XSTest
“not over-refusal” (<a href='https://arxiv.org/abs/2308.01263'>Röttger, et al. 2023</a>)</td>
    <td>0.924</td>
    <td>0.976</td>
  </tr>
</table>

<p>OpenAI has also introduced the concept of a "hidden chain of thought," allowing for internal monitoring of the model’s thought processes without revealing them to users. This strategy provides a balance between transparency and safety, enabling developers to observe the model’s reasoning while preventing potential misuse or manipulation.</p>

<p>OpenAI’s o1 model sets a new standard for AI reasoning and problem-solving. By outperforming human experts in math, science, and coding benchmarks, and introducing innovative techniques like chain of thought reasoning, o1 demonstrates its potential to revolutionize a variety of fields. While still under development, this early release marks a significant step toward more aligned and capable AI systems, offering exciting possibilities for future applications in science, coding, and beyond.</P>

<p>As OpenAI continues to iterate on the o1 model, the advancements in reasoning and alignment are expected to unlock even more groundbreaking use cases. To read full article go to oficial <a href="https://openai.com/index/learning-to-reason-with-llms/">blog post.</a</p>
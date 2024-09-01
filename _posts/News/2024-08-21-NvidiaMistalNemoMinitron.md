---
layout: post
current: post
cover: assets/images/news_images/nvidia.jpg
navigation: True
title: NVIDIA and Mistral AI's Mistral-NeMo-Minitron 8B Model-A Leap Forward in LLM Efficiency
tags: [news]
class: post-template
subclass: 'post'
author: Kavour
---

<p> NVIDIA and Mistral AI have introduced the Mistral-NeMo-Minitron 8B model, an advanced large language model (LLM) that delivers exceptional accuracy across nine popular benchmarks. This model is a pruned and distilled version of the Mistral NeMo 12B, maintaining high performance while being significantly more efficient.</p>



<h3> Pruning and Distillation: Key Techniques</h3>

<p> The Mistral-NeMo-Minitron 8B model is created using NVIDIA’s proven approach of model pruning and knowledge distillation. Pruning reduces the model size by removing less critical parts—specifically, by focusing on width pruning, which targets neurons, attention heads, and embedding channels. This approach, when combined with light retraining through knowledge distillation, yields a smaller, faster, and more resource-efficient model without compromising much on predictive power.</p>

<table>
  <tr>
    <th></th>
    <th>Training tokens</th>
    <th>Wino-Grande 5-shot</th>
    <th>ARC Challenge 25-shot</th>
    <th>MMLU 5-shot</th>
    <th>Hella Swag 10-shot</th>
    <th>GSM8K 5-shot</th>
    <th>TruthfulQA 0-shot</th>
    <th>XLSum en (20%) 3-shot</th>
    <th>MBPP 0-shot</th>
    <th>Human Eval 0-shot</th>
  </tr>
  <tr>
    <th>Llama 3.1 8B</th>
    <td>15T</td>
    <td>77.27</td>
    <td>57.94</td>
    <td>65.28</td>
    <td>81.80</td>
    <td>48.60</td>
    <td>45.06</td>
    <td>30.05</td>
    <td>42.27</td>
    <td>24.76</td>
  </tr>
  <tr>
    <th>Gemma 7B</th>
    <td>6T</td>
    <td>78</td>
    <td>61</td>
    <td>64</td>
    <td>82</td>
    <td>50</td>
    <td>45</td>
    <td>17</td>
    <td>39</td>
    <td>32</td>
  </tr>
  <tr>
    <th>Mistral-NeMo-Minitron 8B</th>
    <td>380B</td>
    <td><strong>80.35</strong></td>
    <td><strong>64.42</strong></td>
    <td><strong>69.51</strong></td>
    <td><strong>83.03</strong></td>
    <td><strong>58.45</strong></td>
    <td><strong>47.56</strong></td>
    <td><strong>31.94</strong></td>
    <td><strong>43.77</strong></td>
    <td><strong>36.22</strong></td>
  </tr>
  <tr>
    <th>Mistral NeMo 12B</th>
    <td>N/A</td>
    <td>82.24</td>
    <td>65.10</td>
    <td>68.99</td>
    <td>85.16</td>
    <td>56.41</td>
    <td>49.79</td>
    <td>33.43</td>
    <td>42.63</td>
    <td>23.78</td>
  </tr>
</table>
<figcaption class="wp-element-caption"><em><em>Table 1. Accuracy of the Mistral-NeMo-Minitron 8B base model compared to the teacher Mistral-NeMo 12B, Gemma 7B, and Llama-3.1 8B base models. Bold numbers represent the best among the 8B model class</em></em></figcaption>

<p> Model Pruning involves slimming down the model by either dropping layers (depth pruning) or reducing the size of internal components (width pruning). In this case, width pruning was employed, which reduced the MLP intermediate dimensions and hidden sizes while retaining the number of attention heads and layers. This method is preferred as it consistently outperforms depth pruning.</p>

<p> Knowledge Distillation serves to transfer knowledge from a larger "teacher" model (in this case, the Mistral NeMo 12B) to the smaller "student" model (Mistral-NeMo-Minitron 8B). This step involves retraining the pruned model with a smaller dataset, ensuring it maintains high accuracy while being faster and more efficient.</p>

<h3> Process and Results</h3>
<ul>
<li> <strong>Teacher Fine-Tuning</strong>: The unpruned 12B model was fine-tuned with 127 billion tokens to correct distribution shifts, ensuring optimal performance during distillation.</li>
<li> <strong>Width Pruning</strong>: Importance scores were calculated for pruning, focusing on compressing the MLP intermediate dimension and the hidden size, while maintaining the number of attention heads and layers.</li>
<li> <strong>Distillation</strong>: The pruned model was distilled using a carefully controlled training process, ensuring minimal loss of accuracy.</li>
</ul>

<p> The result is a model that not only rivals but often surpasses similar-sized models in accuracy, while also being significantly more resource-efficient.</p>

<h3> Conclusion and Future Directions</h3>
<p> The Mistral-NeMo-Minitron 8B demonstrates the effectiveness of structured weight pruning combined with knowledge distillation, offering a scalable approach to building efficient and high-performing LLMs. NVIDIA plans to continue refining these techniques, with future efforts aimed at creating even smaller, more accurate models. These innovations will be gradually integrated into the NVIDIA NeMo framework, further advancing the field of generative AI.</p>

<p> This advancement highlights NVIDIA’s commitment to pushing the boundaries of AI model efficiency, making powerful AI more accessible and cost-effective.</p>

<p> To read full report, in the official NVDIA Developer blog, click <a href='https://developer.nvidia.com/blog/mistral-nemo-minitron-8b-foundation-model-delivers-unparalleled-accuracy/?ncid=ref-inor-390349/'>here</a>.</p>
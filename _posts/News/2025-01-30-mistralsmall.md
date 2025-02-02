---
layout: post
current: post
cover: assets/images/news_images/mistralai.jpeg
navigation: True
title: Mistral AI Unveils Mistral Small 3 - A High-Performance, Latency-Optimized Model
date: 2025-01-30
tags: [news]
class: post-template
subclass: 'post'
author: Kavour
---

<p>Mistral AI has introduced Mistral Small 3, a 24-billion-parameter model optimized for low latency, delivering performance comparable to larger models while maintaining efficiency. Released under the Apache 2.0 license, it offers a versatile solution for various AI applications.</p>

<img src='https://mistral.ai/images/news/mistral-small-3/up-and-to-the-left.png' />

<p>On January 30, 2025, Mistral AI announced the release of Mistral Small 3, a latency-optimized model with 24 billion parameters. This model is designed to provide robust language understanding and instruction-following capabilities, catering to approximately 80% of generative AI tasks that demand quick and accurate responses. Notably, Mistral Small 3 achieves over 81% accuracy on the MMLU benchmark and processes 150 tokens per second, making it one of the most efficient models in its category.</p>

<p>Mistral Small 3 stands out by delivering performance on par with larger models such as <a href='https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct'>Llama 3.3 70B</a> and <a href='https://qwenlm.github.io/blog/qwen2.5-llm/'>Qwen 32B</a>, while operating more than three times faster on equivalent hardware. This efficiency is achieved through a streamlined architecture with fewer layers, reducing the time required for each forward pass. Both pretrained and instruction-tuned versions of the model are available under the Apache 2.0 license, providing a solid foundation for further development and customization.</p>

<p>In evaluations conducted with an external third-party vendor, Mistral Small 3 was assessed alongside other models using over 1,000 proprietary coding and generalist prompts. Evaluators, who were unaware of which model generated each response, consistently preferred the outputs from Mistral Small 3. These assessments encompassed various domains, including code, mathematics, general knowledge, and instruction-following tasks, underscoring the model's versatility and effectiveness.</p>

<p>Mistral Small 3 is well-suited for a range of applications:</p>
<ul>
    <li><strong>Fast-Response Conversational Assistance:</strong> Ideal for virtual assistants and scenarios where users expect immediate, accurate feedback.</li>
    <li><strong>Low-Latency Function Calling:</strong> Capable of handling rapid function execution within automated workflows.</li>
    <li><strong>Fine-Tuning for Subject Matter Expertise:</strong> Can be customized to specialize in specific domains, making it valuable for fields like legal advice, medical diagnostics, and technical support.</li>
    <li><strong>Local Inference:</strong> When quantized, the model can run privately on hardware such as a single RTX 4090 or a MacBook with 32GB RAM, benefiting hobbyists and organizations managing sensitive information.</li>
</ul>

<p>With the release of Mistral Small 3, Mistral AI continues its commitment to advancing open-source AI solutions. The model's combination of high performance, low latency, and versatility makes it a compelling choice for developers and organizations seeking efficient and customizable AI models for a variety of applications.</p>

<p> To learn more, and find ways to get the most out of it, head to the <a href='https://mistral.ai/news/mistral-small-3/'>official blog post</a>.</p>

<p> For those of you eager to get your hands dirty, it is said that there is the following collaborations with Hugging Face, Ollama, Kaggle, Together AI, and Fireworks AI to make the model available on their platforms:

<ul>
    <li><a href='https://huggingface.co/mistralai/Mistral-Small-24B-Instruct-2501'>Hugging Face</a> (<a href='https://huggingface.co/mistralai/Mistral-Small-24B-Base-2501'>base model</a>)</li>
    <li><a href='https://ollama.com/library/mistral-small'>Ollama</a></li>
    <li><a href='https://www.kaggle.com/models/mistral-ai/mistral-small-24b'>Kaggle</a></li>
    <li><a href='https://www.together.ai/models/mistral-small-3'>Together AI</a></li>
    <li><a href='https://fireworks.ai/models/fireworks/mistral-small-24b-instruct-2501'>Fireworks AI</a></li>
    <li><a href='https://www.ibm.com/products/watsonx-ai'>IBM watsonx</a></li>
    <li>Coming soon on NVIDIA NIM, Amazon SageMaker, Groq, Databricks and Snowflake</li>
</ul>
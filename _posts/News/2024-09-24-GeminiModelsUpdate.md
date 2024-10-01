---
layout: post
current: post
cover: assets/images/news_images/google_ai.jpg
navigation: True
title: Updated production-ready Gemini models, reduced 1.5 Pro pricing, increased rate limits, and more
date: 2024-09-24
tags: [news]
class: post-template
subclass: 'post'
author: Kavour
---

<p>Google has released two updated AI models, Gemini-1.5-Pro-002 and Gemini-1.5-Flash-002, featuring enhanced performance, faster outputs, and significantly reduced costs. These models improve upon the Gemini 1.5 series with a focus on text, code, and multimodal tasks, making them highly versatile and accessible for developers through <a href='https://aistudio.google.com/app/prompts/new_chat?model=gemini-1.5-pro-002'>Google AI Studio</a> and the <a href='https://ai.google.dev/gemini-api/docs/models/gemini'>Gemini API</a>.</p>

<p>Google has introduced two powerful updates to its Gemini 1.5 model series: the Gemini-1.5-Pro-002 and Gemini-1.5-Flash-002. These models bring significant improvements in speed, efficiency, and cost, continuing the momentum from previous releases. With a focus on providing developers with faster outputs, reduced latency, and more affordable pricing, these models are ideal for a wide range of use cases, from long-context text synthesis to advanced multimodal applications. Both models are accessible via Google AI Studio and the Gemini API, making them easier to integrate for developers and larger organizations using Google Cloud and <a href='https://cloud.google.com/vertex-ai'>Vertex AI</a>.</p>

<p>The Gemini 1.5 models are designed to perform exceptionally well across various text, code, and multimodal tasks. These capabilities allow them to handle complex tasks like processing <a href='https://ai.google.dev/gemini-api/docs/document-processing'>1,000-page PDFs</a>, answering questions about large code repositories, and analyzing hour-long videos. The latest updates to Gemini 1.5 Pro and Flash build on these strengths, with significant improvements in performance metrics and model efficiency. For example, both models have seen a ~20% boost in math benchmarks and 7% better results in the MMLU-Pro benchmark, positioning them as top performers in their class.</p>

<p>To make the models more developer-friendly, Google has reduced the default output length by 5-20%, ensuring concise responses without sacrificing accuracy. Additionally, the models now offer faster output generation and drastically lower latency, allowing developers to work more efficiently and at scale.</p>

<p> Some of the key features we can clearly see reading though the official post are:</p>
<ul>
<li> Massive Cost Reduction: Gemini 1.5 Pro now offers a 64% price reduction for input tokens and a 52% reduction for output tokens for prompts under 128K tokens, driving down the cost of development.</li>
    <img src='https://storage.googleapis.com/gweb-developer-goog-blog-assets/images/Gemini_Pro_Price_Chart_GRHV7Tk.original.png'>
<li> Increased Rate Limits: Paid tier rate limits are doubled for 1.5 Flash (up to 2,000 RPM) and tripled for 1.5 Pro (up to 1,000 RPM).</li>
<li> Speed and Latency Improvements: Both models are now 2x faster and feature 3x less latency, allowing for quicker and more efficient processing.</li>
    <img src='https://storage.googleapis.com/gweb-developer-goog-blog-assets/images/image3_HthRi7g.original.png'>
<li> Multimodal Capabilities: Enhanced support for complex tasks like video understanding, large-scale document synthesis, and code generation.</li>
<li> Developer-Controlled Filters: Updated <a href='https://ai.google.dev/gemini-api/docs/safety-settings'>safety filters</a> allow developers to configure the models to best suit their needs, with filters no longer applied by default.</li>
</ul>

<p>The release of the Gemini-1.5-Pro-002 and Gemini-1.5-Flash-002 models underscores Google’s commitment to making AI development more efficient, affordable, and versatile. With substantial improvements in speed, accuracy, and cost-efficiency, these models are a powerful tool for developers working on text, code, and multimodal projects. The reduction in costs, coupled with increased rate limits and faster output, ensures that Gemini 1.5 models can cater to diverse needs in AI development, from startups to large-scale enterprises. As Google continues to refine these models, the future of AI-driven innovation looks brighter than ever. To read full article, in the Google for Developers blog, go <a href='https://developers.googleblog.com/en/updated-gemini-models-reduced-15-pro-pricing-increased-rate-limits-and-more/'>here</a>.</p>
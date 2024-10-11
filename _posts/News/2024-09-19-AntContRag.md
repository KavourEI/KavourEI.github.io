---
layout: post
current: post
cover: assets/images/anthropic.png
navigation: True
title: Enhancing AI Performance with Contextual Retrieval
date: 2024-09-19
tags: [news]
class: post-template
subclass: 'post'
author: Kavour
---

<p>This article explores the innovative approach of Contextual Retrieval, a method that enhances the performance of AI models by improving information retrieval accuracy. By combining contextual embeddings and BM25 techniques, this method significantly reduces retrieval failures, leading to better AI responses in various applications.</p>

<h3>Introduction</h3>

<p>In the realm of artificial intelligence, particularly in applications like customer support and legal analysis, having access to relevant background knowledge is crucial. Traditional methods of enhancing AI knowledge often involve Retrieval-Augmented Generation (RAG), which retrieves pertinent information from a knowledge base. However, conventional RAG solutions frequently fail to preserve context, resulting in suboptimal retrieval outcomes.</p>

<h3>The Need for Contextual Retrieval</h3>
<p>To address the limitations of traditional RAG, a new method called "Contextual Retrieval" has been introduced. This technique employs two sub-methods: Contextual Embeddings and Contextual Best Match 25 (BM25). The implementation of these methods has shown a remarkable reduction in retrieval failures—by 49% when combined with reranking, improving overall performance significantly.</p>
<figure>
   <img src="https://www.anthropic.com/_next/image?url=https%3A%2F%2Fwww-cdn.anthropic.com%2Fimages%2F4zrzovbb%2Fwebsite%2F45603646e979c62349ce27744a940abf30200d57-3840x2160.png&w=3840&q=75" >
   <figcaption>A Standard Retrieval-Augmented Generation (RAG) system that uses both embeddings and Best Match 25 (BM25) to retrieve information. TF-IDF (term frequency-inverse document frequency) measures word importance and forms the basis for BM25.</figcaption>
</figure>
<img href=''>

<h3>Understanding RAG</h3>
<p>RAG typically involves several steps to preprocess a knowledge base:</p>
<ul>
    <li>Breaking down the knowledge base into smaller text chunks.</li>
    <li>Using an embedding model to convert these chunks into vector embeddings.</li>
    <li>Storing these embeddings in a vector database for semantic searching.</li>
</ul>
<p>While embedding models excel at capturing semantic relationships, they may overlook exact matches. This is where BM25 comes into play, providing precise lexical matching capabilities that can identify specific terms or phrases effectively.</p>

<h3>The Contextual Retrieval Method</h3>
<p>Contextual Retrieval enhances traditional methods by adding chunk-specific context to each piece of information before embedding it. For instance, a financial report chunk might be transformed from:</p>
<pre><code>original_chunk = "The company's revenue grew by 3% over the previous quarter."</code></pre>
<p>to:</p>
<pre><code>contextualized_chunk = "This chunk is from an SEC filing on ACME Corp's performance in Q2 2023; the previous quarter's revenue was $314 million. The company's revenue grew by 3% over the previous quarter."</code></pre>

<h3>Implementing Contextual Retrieval</h3>
<p>The implementation of Contextual Retrieval can be automated using AI models like Claude (you can find Anthropic's solution in the <a href='https://github.com/anthropics/anthropic-cookbook/tree/main/skills/contextual-embeddings'>cookbook</a> procided). By instructing Claude to generate concise context for each chunk, developers can efficiently prepare their knowledge bases for improved retrieval accuracy.</p>

<h3>Cost-Effectiveness with Prompt Caching</h3>
<p>One of the significant advantages of using Claude is the ability to cache prompts, which reduces both latency and costs associated with generating contextualized chunks. This feature allows developers to reference previously cached content rather than reloading entire documents for every chunk.</p>

<h3>Performance Improvements</h3>
<p>Experimental results indicate that Contextual Embeddings alone can reduce retrieval failure rates significantly. When combined with BM25, the failure rate decreases even further. Notably:</p>
<ul>
    <li>Contextual Embeddings reduced top-20-chunk retrieval failure by 35%.</li>
    <li>The combination of both techniques reduced failure rates by 49%.</li>
</ul>

<h3>Reranking for Enhanced Accuracy</h3>
<p>A final layer of optimization can be achieved through reranking techniques. By scoring and selecting the most relevant chunks based on user queries, reranking ensures that only the best responses are generated, further enhancing performance and reducing costs.</p>

<p>The advancements brought about by Contextual Retrieval represent a significant leap in AI information retrieval capabilities. By integrating contextual embeddings with BM25 and implementing reranking strategies, developers can maximize their AI systems' performance across various applications. The use of these methods is encouraged for anyone working with extensive knowledge bases to unlock new levels of efficiency and accuracy. To read full article about implementations and more check out Anthropic's <a href='https://www.anthropic.com/news/contextual-retrieval'>blog post</a>.</p>
---
layout: post
current: post
cover:  assets/images/arxiv.jpeg
navigation: True
title: Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters
date: 2024-08-06
tags: [research]
class: post-template
subclass: 'post'
author: Kavour
---

<h2> Abstract </h2>

<p> Extraction and interpretation of intricate information from unstructured text data arising in financial applications, such as earnings call transcripts, present substantial challenges to large language models (LLMs) even using the current best practices to use Retrieval Augmented Generation (RAG) (referred to as VectorRAG techniques which utilize vector databases for information retrieval) due to challenges such as domain specific terminology and complex formats of the documents. We introduce a novel approach based on a combination, called HybridRAG, of the Knowledge Graphs (KGs) based RAG techniques (called GraphRAG) and VectorRAG techniques to enhance question-answer (Q&A) systems for information extraction from financial documents that is shown to be capable of generating accurate and contextually relevant answers. Using experiments on a set of financial earning call transcripts documents which come in the form of Q&A format, and hence provide a natural set of pairs of ground-truth Q&As, we show that HybridRAG which retrieves context from both vector database and KG outperforms both traditional VectorRAG and GraphRAG individually when evaluated at both the retrieval and generation stages in terms of retrieval accuracy and answer generation. The proposed technique has applications beyond the financial domain.</p>

<h2> Authors </h2>

<p><a href='https://arxiv.org/search/cs?searchtype=author&query=Sarmah,+B'>Bhaskarjit Sarmah</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Hall,+B'>Benika Hall</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Rao,+R'>Rohan Rao</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Patel,+S'>Sunil Patel</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Pasquali,+S'>Stefano Pasquali</a>, <a href='https://arxiv.org/search/cs?searchtype=author&query=Mehta,+D'>Dhagash Mehta</a></p>

<p>For more information go <a href='https://arxiv.org/abs/2408.04948'>here</a></p>
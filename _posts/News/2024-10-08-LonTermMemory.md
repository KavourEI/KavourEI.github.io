---
layout: post
current: post
cover: assets/images/news_images/langchain.webp
navigation: True
title: Introducing Long-Term Memory Support in LangGraph
date: 2024-10-08
tags: [news]
class: post-template
subclass: 'post'
author: Kavour
---

<p>LangChain has announced the launch of long-term memory support in LangGraph, enabling AI agents to store and recall information across conversations. This feature enhances user interactions by allowing agents to learn from feedback and adapt to user preferences, ultimately improving the overall experience.</p>

<p>The introduction of long-term memory support in LangGraph marks a significant advancement in the capabilities of AI agents. Traditionally, many AI applications have struggled with maintaining context between conversations, often likened to a "goldfish" that forgets everything after each interaction. This limitation not only hampers efficiency but also restricts the potential of AI applications to provide personalized experiences.</p>

<p>Over the past year, LangChain has collaborated with various customers to integrate memory into their AI agents. Through these interactions, it became clear that there is no one-size-fits-all solution for AI memory. Different applications require specific logic tailored to their unique needs, which is why LangGraph's approach focuses on building a simple yet reliable persistent memory layer.</p>

<h3>Key Features of Long-Term Memory Support</h3>
<ul>
    <li><strong>Cross-Thread Memory:</strong> Extends memory capabilities across multiple conversation threads, allowing agents to remember information from previous interactions.</li>
    <li><strong>Persistent Document Store:</strong> Utilizes a straightforward document storage system that supports basic operations like putting, getting, and searching for saved memories.</li>
    <li><strong>Flexible Namespacing:</strong> Organizes memories using custom namespaces for better management across different users or contexts.</li>
    <li><strong>JSON Document Storage:</strong> Saves memories as JSON documents, facilitating easy manipulation and retrieval.</li>
    <li><strong>Content-Based Filtering:</strong> Enables searching through memories based on their content across namespaces.</li>
</ul>

<p>To assist developers in implementing long-term memory within their applications, LangChain has provided several resources. A new LangGraph template is available that showcases a chatbot agent capable of managing its own memory. This template serves as a practical demonstration of how to leverage long-term memory features effectively.</p>

<h3>Resources Available</h3>
<ul>
    <li>An end-to-end tutorial <a href='https://youtu.be/-xkduCeudgY?ref=blog.langchain.dev'>video</a> that guides users through the implementation process.</li>
    <li>A <a href='https://youtu.be/-xkduCeudgY?ref=blog.langchain.dev'>LangGraph Memory Agent</a> example in <a href='https://langchain-ai.github.io/langgraph/how-tos/cross-thread-persistence/?ref=blog.langchain.dev'>Python</a>.</li>
    <li>A <a href='https://github.com/langchain-ai/memory-agent-js?ref=blog.langchain.dev'>LangGraph.js Memory Agent</a> example in <a href='https://langchain-ai.github.io/langgraphjs/how-tos/cross-thread-persistence/?ref=blog.langchain.dev'>JavaScript</a>.</li>
</ul>

<p>The introduction of long-term memory support is designed to empower developers to create more sophisticated and user-friendly AI applications. By incorporating these new capabilities into LangGraph projects, developers can enhance user experiences significantly. The provided resources aim to bridge the gap between theoretical concepts and practical application, making it easier for developers to experiment with long-term memory integration.</p>

<p>As LangChain continues to refine its offerings based on user feedback, the introduction of long-term memory support sets the stage for more advanced functionalities in future releases. The ability for AI agents to learn from past interactions and adapt accordingly will pave the way for more personalized and effective communication between users and their digital counterparts.</p>

<p>The launch of long-term memory support in LangGraph represents an important milestone for AI development. By enabling agents to remember and learn from previous conversations, LangChain is enhancing the potential for creating more engaging and responsive applications. Developers are encouraged to explore these new features and share their experiences as they integrate long-term memory into their projects.</p>

<p>This innovative approach not only improves the functionality of AI agents but also enriches the overall user experience, making interactions more meaningful and tailored to individual preferences. You can read full article and many more relevant posts to the topic in the official <a href='https://blog.langchain.dev/launching-long-term-memory-support-in-langgraph/'>Langchain post</a>.</p>
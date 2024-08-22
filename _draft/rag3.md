---
layout: post
current: post
cover: assets/images/news_images/langchain.webp
navigation: True
title: Multiple datasources - Route selections
date: 2024-08-10
tags: [project]
class: post-template
subclass: 'post'
author: Kavour
---

<p> I hope you enjoy every step so far. Until thiw point of our Langchain/Rag journey, we have managed to build a simple local application and a querry transformation assistant. But what happens when we have multiple data sources? How to define where our application will retrieve the required information from? The definition of this process, finding the correct road, or better let's say finnding the correct route, is called Routing.</p>

<p> There are many ways to give directions in real life, this applies here as well! As we can see in the following image, there are two main categories of routing. 

<ul>
<li> <strong>Logical Routing</strong>: </li>
<li> <strong>Semantic Routing</strong>: </li>
</ul>
</p>

<img src="https://miro.medium.com/v2/resize:fit:1400/1*iBm4xuEwvnp9KFyH9x05cw.png">

<p> Before going though the architecture of such a RAG model for either Logical or Semantic routing, we are going to take a look at the difference accompanied with some simplier examples to understand which is best for your case case to go with.  TODO: Analyze this part of the article and go through thte similarities and the differences of both parts.</p>

<p> Now that we got the main idea about what is the meaning of both, let us take a closer look to the code and how to build this system.</p>

<p> Initially, we need to call the modules that are going to help us accomplish our goal. I am not going to go throug <code>.env</code> file again. I assume that after the first two post, you already have defined itand is ready to go. If not take a look at the first post to go through the process and define it from the begining for your needs. Remember <code>.env</code> file that will keep your Usernames, Passwords and Endpoint IDs safe without the need to erase them or hide them when sharing any file.</p>

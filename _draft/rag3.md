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

<p> Initially, we need to call the modules that are going to help us accomplish our goal. I am not going to go through <code>.env</code> file again and won't be mentioning this file again in the future. Hopefully, you got the idea behind it, why it is important and the reasons I insist on using one. If you are not so sure on what file I am referring to, please take a look at the first two notebooks of this series and follow the steps to create one. Remember <code>.env</code> file will keep your Usernames, Passwords and Endpoint IDs safe without the need to erase them or hide them when sharing any file. So the modules we are going to use within this notebook are the following.</p>

<pre><code>
import os
from langchain_community.document_loaders import PyPDFLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain_community.vectorstores import Chroma
from langchain_core.output_parsers import StrOutputParser
from langchain import hub
from langchain_core.runnables import RunnablePassthrough
from langchain_openai import AzureOpenAIEmbeddings
# from langchain.chat_models import AzureChatOpenAI
from langchain_openai import AzureChatOpenAI

from dotenv import load_dotenv, dotenv_values
load_dotenv()
</code></pre>

<p>As we are using LLM models we need to define embeddings so that we can communicate with the computers and we <i>"talk"</i> the same language.</p>

<pre><code>embeddings = AzureOpenAIEmbeddings(
    deployment = os.getenv('OPENAI_DEPLOYMENT_NAME'),
    model = os.getenv('OPENAI_MODEL_NAME_EMB'),
    azure_endpoint = os.getenv('AZURE_OPENAI_ENDPOINT'),
    openai_api_type = os.getenv('OPENAI_API_TYPE'),
)
</code></pre>

<p> Apart from that, <strong>vectorstore</strong> is essential as we need a place to store the vectors that will result from our embeddings call. Hecne, we are going to defgine a function call <i>vectorstor_gen</i> in order to store the information acquired from the files one owns and what to search from.</p>

<pre><code>def vectorstore_gen(file, dir):
    loader = PyPDFLoader(file)
    documents = loader.load()

    # Split text into chunks
    text_splitter = RecursiveCharacterTextSplitter(chunk_size=500,chunk_overlap=20)
    text_chunks = text_splitter.split_documents(documents)

    vectorstore = Chroma.from_documents(documents=text_chunks,
                                        embedding=embeddings,
                                        persist_directory=dir)
    vectorstore.persist()
    return vectorstore
</code></pre>


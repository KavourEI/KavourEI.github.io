---
layout: post
current: post
cover:  assets/images/lda_fund/lda_basic_0.jpg
navigation: True
title: Topic Modelling - Latent Dirichlet Allocation
date: 2023-10-5
tags: [Machine Learning, NLP, Bayesian Statistics]
class: post-template
subclass: 'post'
author: Kavour
---


<p> Hello everyone! In this post I am going to go through an NLP subject. As you may have already read in this post's title, Topic Modelling is what I aim to explain to you as simple as possible. The reason for creating this post is due to the fact that I have searched around and it took me quite a while to find a non academic explanation of this subject, and I had to combine multiple sources to clearly understand what is going on with that topic. As a result, here I aim to gather all the information I found useful and try to explain everything as non-academic as possible. </p>

<h2 id="specialformatting">Introduction</h2>

<p> Initially, I will provide you with a simple example so that you understand what Latent Dirichlet Allocation (LDA) is about, and how it can be used. Later I am going to state the assumptions and principles upon which LDA is built and of course go through each one so we make sure we get what is the purpose of each and every one of them. Finally I am going to present LDA process and try to explain it as simple as possible so that you have a solid idea of what happens in every step and why it is important. Before kicking off, let's  search on Google the following and see the result: <em>What business problems can  LDA solve</em>. </p>

<blockquote>
<p>Text analysis: LDA is commonly used for text analysis applications, such as topic modelling of news articles, social media posts, and customer feedback. LDA can help identify the main topics and trends in an extensive text data collection, <strong>enabling businesses to make data-driven decisions</strong>.</p>
</blockquote>

<p> In the century of information text analysis is a very import task for all data scientists/analysts as to provide valuable information to businesses, but I guess you know all that, after all, I guess, this is the reason you are reading this. Anyways let's begin! </p>
<p> Imagine that you have in front of you a document, lets say an article. The topic that the articles tried to present is the latest political news. After you have read this article then next that comes in front of you is about sports and then a third one about science. Well after the third one,  the coffee cup is empty and it is time for you to go to work. Anyways, what has just happened is that you came across three different set of vocabularies, set in correct order and following the appropriate grammatical rules in order to give to you information related to Politics, Sports and Science. </p>
<p> After work let's say that you want to write an article in a blog of yours about the most recent news (a.k.a. Political, Sports, and Scientific ones). As a result, you start writing and select some words from Politics-oriented vocabulary, some other from Sports-oriented vocabulary and finally some other from Science-oriented vocabulary. In this way you have managed to create your latest blog post, containing the latest news. </p>
<p> Latent Dirichlet allocation works in the exact opposite way. What I mean by that is given some documents, LDA will take a look at the vocabulary of each document and will try to give us a mixture distribution or better let's say the percentage of topics that is contained in each of the document. Well, that is all, thank you for reading. </p>
<p> Just kidding! </p>
<p> I believe that by now you have a rough idea what LDA does. But, how does it manages this task? </p>

<h2 id="specialformatting">Assumptions and Principals</h2>

<p> Well, LDA is based on certain assumptions and principals (which are going to be presented and explained, shortly) and based on those principals it is built to work in a way that it checks both the vocabulary per topic and the topics per document at the same time in order to assure its well preserved results. There are 4 assumptions that play a critical role for LDA: </p>

<ol>
  <li> Each document is a collection of words, referred to as <em>"Bag of words"</em> </li>
  <li> Stop words like <em>am, is, of, a, the, but,...</em> do not contain any information and their appearance in any of the topics is very probable (if not certain). As a result they can be removed from the document in a preprocessing step. </li>
  <li> The model requires from us to provide the number of topics <em>K</em>, beforehand. </li>
  <li> At the beginning all topic assignments in the vocabulary are assumed to be the correct one, except the word it is analysed at that particular time. </li>
</ol>

<p>Well I believe that the latter 3 points are clear and do not need further explanations. On the other hand, I would like to elaborate a little bit more the first point stated there. What is meant by bag of words is that the order as well as grammatical role of the words do not contain any topic related information and therefor are not considered as a valuable information to be included in the model. As a result the vocabulary from all the documents is collected and analysed as one, without worrying of the aforementioned language settings.</p>
<p>Apart from the assumptions as I have stated earlier there are also two principles. The first principal is that <strong>every document is a mixture of topics</strong>. This means that the model itself is not capable to answer to the question <em>"Which is the topic of the document"</em> but will give us and answer for a document like the following:</p>

<ul>
  <li> Document X does contain 10% of topic 1, 30% of topic 2  and 60% of topic 3.</li>
  <li> The second principal is that every topic is a mixture of words. This implies that every word has a strong correlation with some topics and less (or even non) with some other. You can think of the following example:</li>
  <li> Words like <em>Legislation</em>, <em>Election</em> and <em>Government</em> are highly correlated with Politics and lowly with Science, whereas words like <em>Research</em>, <em>Mitosis</em> and <em>Laboratory</em> are highly correlated with Science are lowly with Politics or Sports.</li>
</ul>

<p>Having understood the fundamentals I believe that is time to try and explore how LDA woks and go through the process itself. The structure of LDA is the following:</p>

<p><img src="assets/images/lda_fund/lda_basic_1" alt="lda_model_architecture"></p>

<p>where:
<ul>
  <li> &alpha; :  is the Dirichlet prior parameter for the per-document-topic proportion </li>
  <li> &theta; : is the topic distribution of a given document </li>
  <li> z: is the topic assignment in word in the given document </li>
  <li> w : is the selected word to be examined </li>
  <li> N : is the collection of words from the examined document </li>
  <li> M : is the collection of documents that we aim to cluster </li>
  <li> &phi; : is the distribution of words of a selected topic</li>
  <li> K : is the collection of available topics </li>
  <li> &beta; : is the Dirichlet prior parameter that represents per-topic-word proportion </li>
</ul>
</p>

<p> We really need to understand how both Dirichlet prior parameters work as good as possible in order to get on well with the process of LDA topic modelling. The Dirichlet prior parameter α represents per-document-topic density. This tells us that by setting α high, documents are assumed to be constructed of more topics and result in more specific topic distribution per document. As for parameter β, setting it too high, it is indicated that topics are assumed to be made up of words with great variability and result in a more specific word distribution per topic. </p>

<h2 id="specialformatting">The Latent Dirichlet Allocation model</h2>

<p> We now have a complete idea of what LDA is constructed from. As a result, I am positive that it is time to move forward to the wary LDA works. Latent Dirichlet Allocation is basically an iterative process of topic assignment for each word in each document that we include in our analysis. A key element here is the word "latent", which implies as stated earlier, that all document are constructed with the same K-topics that we decide beforehand, but with a different proportion. With that said, the steps of LDA are the following: </p>

<ol>
  <li> Latent Dirichlet Allocation assigned randomly a topic to each of the word in the vocabulary </li>
  <li> Picks a word and delete its initial assignment. Then, given all other topic assignments to the rest of the words in the vocabulary, re-assign a topic to this selected word. The process this time is not random as initially occurred. In contrast it is the product of two conditional probabilities: </li>
  <li> After topic assignment is completed for the selected word, LDA will repeat the process as described above for all other words in the vocabulary. </li>
  <li> Once it is completed LDA will repeat the process until there is no need for further changes. </li>
</ol>

<p> The conditional probabilities that mentioned in the second step is the following: </p>

<ul>
  <li> A = Probability( topic <code>t</code> | document <code>d</code>) which represents the following. Given we evaluate document <code>d</code>, what is the probability that this specific document is of topic <code>t</code>. This is calculated by the number of words that are assigned to topic <code>t</code>. Apart from that a Dirichlet-generated multinomial distribution over topics in each document is included in the calculations. The intuition behind this proportion is that if a lot of words belong to topic <code>t</code> then it is more likely that also the current word we search the topic for also belongs to topic <code>t</code>. </li>
  <li> B = Probability( word <code>w</code> | topic <code>t</code> ) which represents that given we evaluate topic <code>t</code> over all documents, what is the probability that word <code>w</code> is of that specific topic. This is calculated by considering how many of the documents are assigned to that topic due to the assistance of word <code>w</code> and a Dirichlet-generated multinomial distribution over words for each topic. This proportion tries to capture the number of documents that are in topic <code>t</code> because of word <code>w</code>. </li>
</ul>

<p>As a result, the assignment occurs after those two proportions are calculated and the topic that word w belongs to is calculated as </p>

<ul>
  <li> Probability( word <code>w</code> is assigned to topic <code>t</code> ) = A x B </li>
</ul>

<p> The second step as you can see is the most important. As a result, we are going to stay a little bit more to that step in order to fully understand the role that both Dirichlet parameters play in LDA process. As we have seen, there are two Dirichlet-generated multinomial distributions included in order to proceed to the topic assignment in each word selected. This is due to the fact that initially, this method assigns randomly topics to each of the words, where a document may end up with zero probability of a certain topic where in reality this topic should have been included in the document’s mixture distribution of topics. In that case, Dirichlet probability distribution is included over K topics as it is a non-zero probability for the topic generated. This way, a topic with zero initial probability may be included in any future iterations if this should be done.  </p>

<p>I believe that you now have a solid idea about topic modelling, how LDA process works and what is the meaning of every part of it. In the future I am going to come back with an example on LDA computed probably with the help of R programming Language, so stay tuned!</p>

<hr>
<p>Be safe, code safer!</p>

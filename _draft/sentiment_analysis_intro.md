---
layout: post
current: post
cover:  assets/images/lda_fund/lda_basic_0.jpg
navigation: True
title: An introduction to Sentiment Analysis
date: 2023-1-17
tags: [Machine Learning, NLP]
class: post-template
subclass: 'post'
author: Kavour
---

<p>As you may have already guessed I prefer R (I like statistics after all. Sue me, jk!) so in case you want to follow along you need to download R and of course R studio (Posit, some would say, nowadays). </p>

<h2 id="specialformatting">Introduction</h2>

<p>Sentiment analysis is a method of extracting the sentiments and emotions that people are "carrying" by the time they create a small script, a post on social media or even try to figure out what was an author's feelings by the time he/she was writing a poem. Sentiment analysis can find application to many areas of everyday life and serve any purpose that is connected to a text.</p>

<p>Some of the most popular sentiment analysis usage are</p>

<ul>
<li> Social media monitoring : A company/bran can easily monitor whether people think about them/their product by conducting sentiment analysis. </li>
<li> Customer's feedback analysis : Without wasting time on reading every feed back, one can easily filter out the positives and focus on the negative ones to become better, with the help of sentiment analysis.</li>
<li> Some more are Politics, Finance, Employee satisfaction etc. </li>
</ul>

<p> Sentiment analysis is a subgroup of Natural Language Processing (NLP). If you are not familiar with NLP, I could not find a clearer and more thotough explanation than the one IBM gave to the aforementioned question: </p>

<blockquote>
"Natural language processing (NLP) refers to the branch of computer science—and more specifically, the branch of artificial intelligence or AI—concerned with giving computers the ability to understand text and spoken words in much the same way human beings can."
</blockquote>

<p>So by establishing those techniques, we are able to extract a big amount of information from text that otherwise would be time consuming as well as associated with high costs. Now we are able to extract an overview of the opinions about an area of our interest with a snap of our fingers (and of course some lines of code 😅😜)</p>

<h2 id="specialformatting">Steps and requirements</h2>

<p>As probably already know, programming has certain differences in comparison to our spoken/written language. Some of those are:</p>

<ul>
<li>Case Sensitivity</li>
<li>Punctuation Marks</li>
<li>Stemming etc</li>
</ul>

<p>So before getting to the fun part of this post, as well as to using many other machine learning tools and models, we need to preprocess the data that we are interested in. Preprocessing is the key to having the best possible result. Preprocessing is the conversion of the data, from the way we collected/obtained it to the form that the model will understand and learn something from each and every cell included. As a result, is the most important part of every ML/AI project, never forget that! The libraries that are going to be used in the preprocessing step are <p>

<ul>
<li>tm</li>
<li>tibble</li>
</ul>

<p>In case you don't have any of the libraries mentioned in this post, you can easily download them with the help of the install.packages function as shown below by replacing the word library with the title of the package :</p>

<pre><code>
install.packages("package")
</code></pre>

<p>After the preprocessing is completed, we will explore some of the libraries that exist on sentiment analysis and functions contained that will help us achive our goal. Namely :</p>

<ul>
<li> ggplot2 </li>
<li> syuzhet </li>
<li> SentimentAnalysis </li>
</ul>

<h2 id="specialformatting">Preprocessing - Statistical Analysis</h2>

<p>We all know that data come in all different shapes and sizes, this should not make you anxious. You can use numerous libraries to import data, so you can read </p>

<ul>
<li> excel files (.xlsx) with readxl </li>
<li> text files (.txt/.csv) with read.csv function </li>
<li> .spss, .dta, .octave etc with foreign package </li>
</ul>

<p>For every source file there is a package so don't get nervous and use our friend.So initially we need to load the packages we are going to work with, and then load the data:</p>

<pre><code>
library(readxl)
library(tm)
libary(tibble)
library(ggplot2)
library(syuzhet)
library(SentimentAnalysis)
</code></pre>

<p>So initially we need to load the data. The case study here is the following:</p>

<p>We have been asked to find out what people think, given their posts on, let's say twitter, about self-driven cars. You can find the dataset used in here.<p>

<pre><code>
data <- read_xlsx("/Users/.../sentiment-self-driving-cars-QueryResult.xlsx")
head(data)
</code></pre>

<p>Next thing is to convert the text into corpus variable so it is easily manipulable by the tm package. We will also use the VectorSource to create a vector out of every user's post.</p>

<pre><code>
posts <- iconv(data$text, "ASCII", "UTF-8", sub="byte")
posts_cor <- Corpus(VectorSource(posts))
inspect(posts_cor[1:5])
</code></pre>

<p>Now we can see the first five posts, and what the users have written about the self-driven cars. Since we have successfully loaded the data, it is time to raise our sleeves and get the "hard" work done. What I mean by that is what I have mentioned in the previous section. We need to clean our data. Initially, we are going to convert every post to lower.</p>

<pre><code>
posts_cor <- tm_map(posts_cor, tolower)
inspect(posts_cor[1:5])
</code></pre>

<p>Next we are going to remove all the punctuation symbols.</p>

<pre><code>
posts_cor <- tm_map(posts_cor, removePunctuation)
inspect(posts_cor[1:5])
</code></pre>

<p>After that I will display the final outcome and not inspect the feature every time. You are free to inspect it at any point by copying the code written above and spot the differences of every transformation. Next, I am going to</p>

<ul>
<li> remove numbers </li>
<li> remove the stop words </li>
<li> remove any urls in case it is included (we need to create our own function for that) </li>
<li> remove extra white spaces </li>
<li> stemming </li>
</ul>

<pre><code>
removeURL <- function(x){
  gsub('http[[:alnum:]]*', '', x)
}

posts_cor <- tm_map(posts_cor, removeNumbers)
posts_cor <- tm_map(posts_cor, removeWords, stopwords(kind = 'en'))
posts_cor <- tm_map(posts_cor, content_transformer(removeURL))
posts_cor <- tm_map(posts_cor, stripWhitespace)
posts_cor <- tm_map(posts_cor, stemDocument)
inspect(posts_cor[1:5])
</code></pre>

<p><storng>Note that</strong> : In case you have data that are not in English, you can always use an API to help you translate them and then follow along the way (find out more by googling free translating API for R studio/python). Remember that you may need more data transformation like for example you may have text that has emojis in it, or text that is constructed with two or more languages. My go-to strategy in case of a complex problem is:</p>

<ol>
<li> Set the goal on a piece of paper </li>
<li> Write what are the steps that you are going to go through </li>
<li> Write the needs of every step and possible problems </li>
<li> Read the plan from end to beginning to check what the preprocessing should be according to your needs. </li>
</ol>

<p>Moving forward, we need to check the frequency of the words in order to see if there is any word that is somehow neutral or does not reveal information and we need to exlude it. The matrix containing the frequancy of every word is called term matrix. Then we will create a barplot containing out of the frequencies as well as a word cloud</p>

<pre><code>
tdm <- TermDocumentMatrix(posts_cor)
tdm <- as.matrix(tdm)
</code></pre>

<p>We shall plot the ones that have frequency more that 100 for both the barplot as well as the word cloud</p>

<pre><code>
w <- rowSums(tdm)
w <- subset(w, w>=100)
barplot(w,
        las = 2,
        col = rainbow(50), 
        main = 'Frequency of every word in the data set')

w <- sort(rowSums(tdm), decreasing = TRUE)
set.seed(222)
wordcloud(words = names(w),
          freq = w,
          max.words = 150,
          random.order = F,
          min.freq = 5,
          colors = brewer.pal(8, 'Dark2'),
          scale = c(5, 0.3),
          rot.per = 0.7)
</code></pre>

<p>As you can see the words Car, driverless, selfdriv, google, drive etc appear way more than all the other words. The reason is obvious I think and many of you probably expected this to happen, as the project is arount self-driven cars. A good practise here is to erase those wors, one by one (start from the word Car) to see the difference. Hint : use the one of the following functions to do that :</p>

<ol>
<li> str_replace(text, pattern, replacement) by the package (stringr) </li>
<li> sub(pattern, replacement, text) </li>
</ol>

<p>as for text argument use the text data you want to make a replacement, pattern argument is the word you want to replace for example "car", and finally replacement  is the replacement you want to settle i.e. nothing meaning "").</p>

<p>I will not conduct the replacement and leave that to you in order to compare your updated results to mine, where I made a "mistake" and did not got the preprocessing done as good as possible. </p>

<p>Moving forward, we need to generate sentiments for the processed data. In order to do that we are going to use the get_nrc_sentiment function. Though this function accepts only character features and as a result, before getting to that part, we need to convert the SimpleCorpus feature generated (a.k.a. posts_cor) to character vector. This can be done with the help of a data.frame conversion, and then passing to the function the part we want.</p>

<pre><code>
posts_unlisted <- list()
for (i in seq_along(posts_cor)) {
  posts_unlisted[i] <- gettext(posts_cor[[i]][[1]]) #Do not use $content here!
}

posts_df <- data.frame(
  text=unlist(posts_unlisted),
  stringsAsFactors=F)

posts_clean <- posts_df$text
all_sents <- get_nrc_sentiment(as.character(posts_clean))
all_sents[1:100]
</code></pre>

<p>Here you can see the results for the first 100 posts about self-driven cars. Furthermore, we can produce further visualisations </p>

<pre><code>
all_sums <- as.data.frame(colSums(all_sents))
all_sums <- rownames_to_column(all_sums)
colnames(all_sums) <- c("Sentiments", "count")
ggplot(all_sums, 
  aes(x = Sentiments, 
  y = count, 
  fill = Sentiments)) + 
    geom_bar(stat = "identity") +  
    labs( x = "Sentiments", y = "Count") + 
    ggtitle("Sentiment of Job Descriptions") +
    theme_minimal() + 
    theme(legend.position="none", 
      panel.grid.major = element_blank()) + 
    theme(plot.title = element_text(hjust=0.5)) +
    geom_text(aes(label = count), nudge_y = 50)
</code></pre>

<p>Overall, we see that the posts are positive, so we could report that. From this point and forward the possibilities are infinite. You can use the analysis produced  to focus on the negative-ish sentiments and try to become better, see what the crowd is shouting so long but could not hear. You could use other sources like geographical origin of the written and see what is going on with the company's branch there. You could use other machine learning algorithms to get this analysis a step forward to any direction this may seem interesting.</p>

<p>By further exploration of the packages writtern above, you will see that you can bring sentiment analysis to your needs. We could have the output with a decimal number betwen -1 (for negative) through 0 (for neutral) all the way until 1 (for positive). There are many methods to check and functions to explore!</p>

<p>Thank you for reading! I hope this post have helped someone to get started with NLP and Sentiment Analysis.</p>

<hr>
<p>Be safe, code safer!</p>
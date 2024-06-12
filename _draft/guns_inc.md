---
layout: post
current: post
cover:  assets/images/lda_fund/lda_basic_0.jpg
navigation: True
title: Document Clustering - Sentence Similarity
date: 2022-6-11
tags: [EDA]
class: post-template
subclass: 'post'
author: Kavour
---

<p>In order to complete the analysis, I am going to use R programming. To see and download the data in order to follow along the process, please click on the Get Data button. </p>

<p>This is a dataset containing information about the incidents with guns during a period of two years (01.01.2017 until the 28.12.2019). The variables contained in the dataset are the following: </p>

<ul>
<li> S.No : Numbering of the incidents </li>
<li> Year : The year of the incident. </li>
<li> Month : The month of the incident. </li>
<li> Date : The complete data of the incident. </li>
<li> Reason : The reason of the gun use. </li>
<li> Education : The education of the person that used the gun. </li>
<li> Sex : Sex of the person that used the gun. </li>
<li> Age : The age of the person that used the gun. </li>
<li> Race : The race of the person that used the gun. </li>
<li> Hispanic : -No Comment- </li>
<li> Place of incident : Place where the usage of the gun took place. </li>
<li> Police Involvement : Whether there was involvement of the police. </li>
</ul>

<p> Those, are the variables that exist in the data frame. As you can see I did not comment on the variable Hispanic, and the reason is that I do not fully understand what is the meaning of this variable. So I will not use it in any of my calculations. Apart from that I will drop S.No variable as it is used just for indexing and we do not want such a thing. </p>

<p> In this analysis, we are going to begin with an EDA (exploratory data analysis) in order to see all the details about the variables and we will create some visualisations. Later on in a next post we will continue with a correlations check. In fact, we are going to see which (if any of the) variables have a major impact in the decision to use a gun or not. At the end I will try to create predictive model in order to check how likely are people with different characteristics (the variables written above) in the future to use a gun. </p>

<h2 id="specialformatting">Cleaning/Preprocessing</h2>

<p> Initially, we are going to load all the libraries that we are going to need in order to complete all the tasks written above. </p>

<pre><code>
library(dplyr)
library(tidyr)
library(ggplot2)
library(plotrix)
library(ggeasy)
library(forcats)
</code></pre>

<p> So let us load the data and check if any missing values exist. </p>

<pre><code>
df <- read.csv('.../Guns incident Data.csv')
head(df, n =5)
</code></pre>

<p> We see here that the Date variable is a Date. Reason, Education, Sex, Race, Place.of.Incident are sting variables and Police.involvement is a factor variable. Police.involvement contains only two variables, 0 and 1 (meaning that police did not or did involved, respectively, in the incident). S.No. is just for indexing (we are not going to use it). Lastly, Year and Month variables contain numbers but are categorical variables so there is no meaning in using those variables as numbers. </p>

<pre><code>
apply(apply(df, 2, is.na),2,sum)
</code></pre>

<p> Here we have the variables and the number of missing values presented under the variable's title. Let us try to interpret the missing values. </p>

<ul>
<li><strong>Education</strong> : Number of missing values 1422.</li>
</ul>

<pre><code>
df %>% 
  select(Reason, Education, Age) %>% 
  filter(is.na(Education)) %>% 
  head(n = 10)
</code></pre>

<p> We can see here the Age of the people that were part of the incident. From that data we can see that people's age vary, in the group of Education's missing values. My intuition is that the information is not missing but those people have not acquired any further education, other than the mandatory one. Hence, I am going to replace, missing values with "No_Education" </p>

<pre><code>
df$Education <- df$Education %>% 
  replace_na('No_Education')
</code></pre>

<ul>
<li>Age : Number of missing values 18.</li>
</ul>

<p> Here we can see that some people with missing value have 'Some college' level of education as a result, we can not conclude that there is any different meaning than that is missing by mistake. From my point of view, there is no correct and wrong way to correct the NAs. One way that I would like to avoid is to set those values to 0 or ignore/erase those rows. So I will replace those 18 values with the mean of the variable Age. </p>

<pre><code>
df$Age <- df$Age %>% 
  replace_na(mean(df$Age, na.rm = TRUE))
</code></pre>

<ul>
<li><strong>Place.of.incident</strong> : Number of missing values 1384.</li>
</ul>

<pre><code>
unique(df$Place.of.incident)
data.frame(table(df$Place.of.incident, useNA = 'always'))
</code></pre>

<p> For this current example, we will set Non Assigned values as Other Unspecified. </p>

<pre><code>
df$Place.of.incident <- df$Place.of.incident %>% 
  replace_na("Other unspecified")


data.frame(table(df$Place.of.incident, useNA = 'always'))
</code></pre>

<p> Eventually, we can see that we do not have any missing/non-assigned values left to handle and we are ready to begin with the analysis. </p>

<pre><code>
apply(apply(df, 2, is.na), 2, sum)
</code></pre>

<h2 id="specialformatting">Data exploration</h2>

<p> Initially, we will check which of the Months in the aforementioned year (2017, 2018, 2019) the gun incidents where maximum/minimum. </p>

<p> Initially, we will define the frequency table for 2017, only </p>

<pre><code>
freq <- data.frame(table(df$Month, df$Year == 2017)[,2])
freq$Months <- c(month.name)
colnames(freq) <- "Number of incidents"
</code></pre>

<p> Now we are ready to use this table and create a bar plot where we will be able to see graphically what is going when it come to the number of incidents per month. </p>

<pre><code>
f <- ggplot(data = freq, mapping = aes(x = Months)
f <- f + geom_bar(stat = 'identity')
f <- f + geom_text(aes(label=`Number of incidents`), 
                   vjust=1.6, 
                   color="white", 
                   size=2)
f <- f + labs(title = 'Number of Incidents per Month (2017)',
              x = 'Months',
              y = 'Number of Incidents')
f
</code></pre>

<p> We can see that most of the gun incidents during 2017 took place during July (3026) and the month with the least amount of gun incidents is February (2357). Well, February, many could say that it's the month of love.. Just kidding of course. There should be an extensive research when it comes to the reason behind those actions. We will try to see if there is a correlation of the number of the incidents, and Months, but let's leave that for later. Now let us focus here and try and explore what is going on about 2018, 2019. All we have to do it copy the code written in the previous two cells and just change the df$Year == 2017 to 2018, or 2019 depending the case. When we do this, and try to plot the results we have the following two results: </p>

<p> and for 2019 .. </p>

<p> We can  see that for 2018 as well as 2019, the month with the least amount of gun incidents is February(2375 and 2361, respectively). This is interesting and we should keep this in the back of our head for later research (we WILL come back to that..!) Now we see that during 2018 we have again July as the month with the most gun incidents (3079) though during 2019, the month with this characteristic is August (2970). </p>

<p> By looking at the data, the next question that pops in my mind is connected to education. As a result, we are going to search what is the education distribution amongst the people that created a gun incident. </p>

<pre><code>
freq_edu <- data.frame(table(df$Education))

f <- ggplot(data = freq_edu, 
            mapping = aes(x = reorder(Var1 , -Freq), 
                          y = Freq,
                          fill = Freq))
f <- f + geom_bar(stat = 'identity')
f <- f + geom_text(aes(label= Freq), 
                   vjust=1.6, 
                   color="white", 
                   size=2)
f <- f + labs(title = 'Frequency of Education Level',
              x = 'Education Level',
              y = 'Frequency')
f <- f + theme_classic()
f
</code></pre>

<p> Interestingly, most people who create gun incidents, have High School education. Remember that No_education is our correction of the NA values. What is interesting here is to investigate the Age variable, based on the Education, since we are at this point. </p>

<pre><code>
f <- ggplot(data = df,
            mapping = aes(x = Education, y = Age, fill = Education))
f <- f + geom_boxplot(alpha = 0.3)
f <- f +labs(title = 'BoxPlot of Education vs Age',
             x = 'Education Level',
             y = 'Age') + easy_center_title()
f
</code></pre>

<p> This is very interesting. 🤔 Take a look at the box plot above, take a step back and think what is the data presenting?!?  Take a look at the results of the calculations below 👇 </p>

<pre><code>
df %>% 
  select(Age, Education) %>% 
  filter(Education == 'Bachelors') %>% 
  summarise(quantile(Age))
</code></pre>

<p>And now let us see how many are between 43, and 67</p>

<pre><code>
df %>% 
  select(Age) %>% 
  count(Age>=43 & Age <= 67)
</code></pre>

<p> The result, tells us that 64542 aged between (including) 43 and 67 and are reported with educational level Bachelor. The are two different cases here. Unfortunately, there are no clarifications what is the one for our dataset. Anyways, the options are the following: </p>

<p> The person who created the gun incident is presented in by the Education level, and the victims is presented in the Age column. </p>

<p> The person who created the gun incident has acquired the written Education level some part of his/hers life. His/hers current status is presented by the column Age. </p>

<p> We will proceed with the second case, and think that the incidents are created by one aged as the variable Age indicates us. Let as take a closer look at the Age variable to establish what we just said. </p>

<pre><code>
df %>% 
  select(Age) %>% 
  summary()
</code></pre>

<p> As we can see accidents do happen. We can see here that there exist a gun incident where a child of age 1 was the gun holder. </p>

<pre><code>
df %>% 
  select(Age, Reason, Education, Place.of.incident) %>% 
  filter(Age <= 1) %>% 
  count()
</code></pre>

<p> The incidents involving a person aged less than or equal to 1 are 33. If you ask me I would say that they should be 0 though, accidents do happen, so... </p>

<pre><code>
df %>% 
  select(Age, Reason, Education, Place.of.incident) %>% 
  filter(Age <= 1) %>% 
  head(n = 10)
</code></pre>

<p> Now its the time to evaluate our decision to interpret the Age variable. I leave this to you, and continue my analysis, with the second option, as I have already mentioned. Education level is what is the maximum education the one has acquired until the day of the incident. </p>

<pre><code>
f <- ggplot(data = df,
            mapping = aes(x = Education, y = Age, fill = Education))
f <- f + geom_violin(alpha = 0.3)
f <- f + labs(title = 'Violin plot of Education vs Age',
              x = 'Education Level',
              y = 'Age')
f
</code></pre>

<p> Not it is time for us to move to the Reason variable. </p>

<pre><code>
freq_re <- data.frame(table(df$Reason))
</code></pre>

<p> Let us plot the categories and try to interpret it, if possible. </p>

<pre><code>
f <- ggplot(data = freq_re, 
            mapping = aes(x = reorder(Var1 , -Freq), 
                          y = Freq,
                          fill = Freq))
f <- f + geom_bar(stat = 'identity')
f <- f + geom_text(aes(label= Freq), 
                   vjust=-0.5, 
                   color="black", 
                   size=3)
f <- f + labs(title = 'Frequency of Reasons',
              x = 'Reason of Gun Incident',
              y = 'Frequency')
f <- f + theme_classic()
f
</code></pre>

<p> We can see that most of the reasons for gun usage displayed in the dataset is for suicide attempts. There are 63175 Suicide gun incidents. On the other hand, all gun usage reasons, namely Homicide, Accidental, Undetermined, are 37623 reported gun incidents, which are about the half in number of Suicides. </p>

<pre><code>
df %>% 
  select(Reason, Sex, Age, Education) %>% 
  filter(Reason == "Suicide") %>% 
  count(Sex == 'Male')
</code></pre>

<p> We have a thing here... Take a look at the numbers above. 54486 gun incidents out of 63175 are conducted by Males, only 8689 are conducted by Female. What do you think the reasons are? Maybe males have more direct access to guns, or they are not able to face problems as effective as the females do. We can see the total number of gun incidents for each Sex category. </p>

<pre><code>
f <- ggplot(data = df,
            mapping = aes(x = Sex, fill = Sex))
f <- f + geom_bar()
f <- f + labs(title = 'Number of Female/Male in the Dataframe',
              x = 'Sex',
              y = 'Number of Incidents')
f <- f + geom_text(aes(label = ..count..),
                   vjust = 1.2,
                   size = 3,
                   stat = 'count')
f <- f + theme_classic()
f
</code></pre>

<p> Let us now, find the age distribution. Later on let us find the age distribution per sex category. Furthermore, I believe that it is interesting to research further the age distribution for sex category specifically for the suicide incidents. </p>

<pre><code>
f <- ggplot(data = df, mapping = aes(x = Age, fill = Sex))
f <- f + geom_density(alpha = 0.3)
f <- f + labs(title = 'Age Distribution', 
              x = 'Age',
              y = 'Density')
f
</code></pre>

<p> Let us now see what is going on specifically, for the reason Suicide. </p>

<pre><code>
df %>%
  filter(Reason == 'Suicide') %>%
  ggplot(mapping = aes(x = Age, fill = Sex)) +
  geom_density(alpha = 0.3) + 
  labs(title = 'Age Distribution (Reason = Suicide)', 
              x = 'Age',
              y = 'Density') + ggeasy::easy_center_title()
</code></pre>

<p> We can see differences between the general case and the Suicide (Reason) specified for Males. In the general case the gun usage is more frequent in the lower age, whereas when we specify our research to Suicide, we see that it is much more frequent for the age between 50s-60s. On the other hand, female, keeps the same distribution before and after the specification. </p>

<p> Lastly, we are going to check what is going on with the variables that describe the Places where the incidents happen and the police involvement in the gun usage (as described in the dataset). </p>

<pre><code>
f <- ggplot(data = df, mapping = aes(x = fct_infreq(Place.of.incident), fill = Place.of.incident))
f <- f + geom_bar(alpha = 0.5)
f <- f + labs(title = 'Barplot of Place of gun incident',
              x = 'Place of Incident',
              y = 'Number of incidents')
f <- f + geom_text(aes(label = ..count..),
                   vjust = -0.5,
                   size = 3,
                   stat = 'count')
f <- f + theme(axis.text.x = element_text(angle = 45, vjust = 0.6))
f
</code></pre>

<p> As we can see most of the incidents have taken place at Home. One could say that this is expected as the number of gun incidents for the reason of suicide occurred is the major one  and the difference from other reasons combined is immense. Though this logical steps seem to be correct, we can not end up to this conclusion based only on the presented data. As for the end, we will investigate what is the number of police involvement in those gun incidents. </p>

<pre><code>
df$Police.involvement <- factor(df$Police.involvement)

f <- ggplot(data = df, mapping = aes(x = fct_infreq(Police.involvement), 
                                     fill = Police.involvement))
f <- f + geom_bar(alpha = 0.4)
f <- f + labs(title = 'Number of incidents where police involved',
              x = 'Police Involvement (0: No, 1: Yes)',
              y = 'Number of incidents')
f <- f + geom_text(aes(label = ..count..),
                   vjust = -0.5,
                   size = 3,
                   stat = 'count')
f <- f + guides(fill = guide_legend(title = 'Police involvement'))
f
</code></pre>

<p> Well, I believe that this is a result that we expected. If we take a moment and think the big number of Suicides reported in this dataset, we expected that the police involvement would be so small. I believe there is no doubt about this interpretation. I believe that there is no point on saying that guns are dangerous. We have already have seen that the gun incidents have no age limit. There is no supremum nor infimum. We have seen that in those 3 years, there are more suicides reported than any other reasons. Apart from that, we have seen what is going on related to the gender matter as well the age distribution of the reported incidents. </p>

<p> What is really interesting, to investigate later on, is try to establish, if any, relationship across the aforementioned variables. Hence, on a later post we will dig deeper and try to apply different kind of algorithms to model the gun incidents and find all those hidden treasures that are hidden in this dataset.. Stay tuned! </p>

<hr>
<p>Be safe, code safer!</p>
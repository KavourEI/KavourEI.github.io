---
layout: post
current: post
cover:  assets/images/lda_fund/lda_basic_0.jpg
navigation: True
title: TV Show - Friends
date: 2021-9-30
tags: [EDA]
class: post-template
subclass: 'post'
author: Kavour
---

<p>In this notebook I am going to analyse a dataset about the famous TV Series Friends. The dataset has been found and downloaded from Kaggle ~ Friends Series Dataset. </p> 

<p>All copyrights for the display cover image of Friends are owned by the official FRIENDS American Tv Show and its creators. No copyrights for the display cover image presented are reserved by me! </p>

<p>First of all I will import all the libraries that I am going to need for my analysis. </p> 

<pre><code>
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import emoji
import plotly.express as px

import cufflinks as cf
from plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot

%matplotlib inline
sns.set_style('darkgrid')

init_notebook_mode(connected = True)
cf.go_offline()

df = pd.read_csv('.../Datasets/FriendsDataset/friends_episodes_v2.csv')

df.head()

df.tail()
</code></pre>
w
<p>We can see that the two last episodes have the exact same title (*The Last One*). I, for the needs of this analysis and the interpretation of the results to words, will edit the two last titles into the following two: </p> 

<ul>
<li> The Last One (i) </li>
<li> The Last One (ii) </li>
<ul>

<pre><code>
df.at[233 , 'Episode_Title'] = 'The Last One (i)'
df.at[234 , 'Episode_Title'] = 'The Last One (ii)'

df.tail()

df.columns
</code></pre>

<p> In this dataframe we have the following attributes:</p>

<ul>
<li> Year_of_prod : Year of production.</li>
<li> Seasons : Season of the TV Show FRIENDS (1 to 10) </li>
<li> Episode_Title : The title of the episode.</li>
<li> Duration : The duration of an episode. </li>
<li> Summary : A summary of an episode. </li>
<li> Director : Who has directed the episode </li>
<li> Stars : How many starts out of 10 has the episode been awarded with. </li>
<li> Votes : How many people voted. </li>
</ul>

<p>There is no need to change any of the attribute's name. </p> 

<pre><code>
for i in df['Episode_Title']:
    if i[0:7] == 'The One':
        print('Good')
    else:
        print('Not good as:', i[0:7])
</code></pre>

<p>We can see that all the episodes apart from the last two, have a title starting with 'The One". Now let us try and create a list of the words that come after that, what was just reported. </p> 

<pre><code>
Next_title_words = []
for x in df['Episode_Title']:
    if x[8:13] not in Next_title_words:
        Next_title_words.append(x[8:13])
print(Next_title_words)
</code></pre>

<p>We can now see the words that come after the usual title phrase "The One". </p> 

<pre><code>
df[['Season','Episode_Title']].groupby('Season').count()
</code></pre>

<p>So according to the data provided we have the following information: </p> 

<ul>
<li> Season 1 has 23 episodes. </li>
<li> Season 2 has 24 episodes. </li>
<li> Season 3 has 25 episodes. </li>
<li> Season 4 has 24 episodes. </li>
<li> Season 5 has 24 episodes. </li>
<li> Season 6 has 25 episodes. </li>
<li> Season 7 has 24 episodes. </li>
<li> Season 8 has 24 episodes. </li>
<li> Season 9 has 24 episodes. </li>
<li> And finally season 10 has only 18 episodes! </li>
</ul>

<p> In total one has 235 episodes to enjoy from this great TV show called FRIENDS. </p> 

<pre><code>
df.info()

df.describe()
</code></pre>

<p> From the descriptives provided above, we know that there is no point trying to translate the attributes Year_of_prod and Season as those two are some (so called) dummy variables. When it comes to the other attributes we can see that the avg episode lasts 22.3 minutes and an avg episoded is rated with 8.45 stars out of 10 with 3352.28 votes. Pretty good for a TV Show I would say. </p> 

<p> I know!!!

<p> <em>(Hopefully you got the joke..) Moving forward, according to the votings, let us see which season is the best!</em></p>

<pre><code>
df_best_0 = df[['Season','Votes','Stars']]
</code></pre>

df_best_V = df[['Season','Votes']].groupby('Season')['Votes'].sum()
A_data = pd.DataFrame(df_best_V).sort_values('Votes',ascending = False)
A_data

fig = px.pie(A_data, values='Votes', names=A_data.index, title = 'Sum of votes collected per season of the TV Show FRIENDS.')
fig.update_layout(legend_title_text='Season')
fig.show()

<p> From the table and the piechart demonstrated just above we can see that the most voted Season is the 1st one with 95397 votes. </p> 

<pre><code>
df_best_S = df[['Season','Stars']].groupby('Season')['Stars'].sum()
B_data = pd.DataFrame(df_best_S).sort_values('Stars', ascending = False)
B_data
</code></pre>

fig = px.bar(data_frame = B_data, x = B_data.index, y = 'Stars', title = 'Sum of stars collected per Season of the TV Show FRIENDS.')
fig.show()

<p> From the table and the barplot created above, we can see that the 6th Season is the one that collected the highest number of Stars. Given that 2350 is the maximum amount of stars for the whole TV Show and that 235 is per season (divided evenly) we can say that Season 6 managed to collect 212.4/235, quite a good collection. Well, on the other hand the season that collected the least amount of Stars is the last one (nr 10) with a score of 156.2/235 (keep in mind that season 10 haw 18 episodes and the actual maximum is 180, though I decided to divide the full amount of stars evenly). </p> 

<p> Well the next question that pops up my mind and many may disagree with the answer is which episode is the best (according to the voteers of course)? </p> 

<pre><code>
df[df['Stars'] == df['Stars'].max()]
</code></pre>

<p> And so here we are, we have a winner or two 🤷.. Well the two best episodes according to IMDB's votes are Season 5 with episode title "The One Where Everybody Finds Out" and Season 10 with episode title "The Last One (ii)". Now apart from the top episode (since public opinion is divided), I believe there is an immense need to find out the Top-10 episodes of FRIENDS. So here we go... </p> 

<pre><code>
Top_10 = df[['Episode_Title','Stars']].sort_values('Stars',ascending = True).tail(10)
Top_10

plt.figure(figsize=(10,5))
sns.barplot(data = Top_10, y = 'Episode_Title', x = 'Stars', palette='viridis')
plt.title('Top 10 Episodes according to IMDB Rating System', fontsize=15)
plt.xlabel('Stars', fontsize=13)
plt.ylabel("Episode's Title", fontsize=13)
plt.xticks(np.arange(9, 9.8, 0.1), fontsize=12)
plt.yticks(fontsize=12)
plt.xlim(9, 9.8)
</code></pre>

<pre><code>
nr_of_episodes = df[['Director', 'Season']].groupby(by='Director').count()

fig = px.bar(data_frame=nr_of_episodes, x=nr_of_episodes.index, y = 'Season')
fig.update_layout(
    title="Number of Episodes that each Director directed",
    xaxis_title="Directors",
    yaxis_title="Number of Episodes",
    font=dict(
        size=18,
        color="RebeccaPurple"
    ))
fig.show()
</code></pre>

<p> And finally, what we have here.... Those names are the ones that apart fromn David Crane, Marta Kauffman and Kevin S. Bright, that we all see in the end of every episode, directed and created this great TV Show called FRIENDS. </p> 

<p> Well, this has come to an end. I hope that you found out something new through this EDA. One further research that needs to be conducted about this TV Series is whether, Ross Geller and Rachel Green were on a break or not but unfortunately the data provided are insufficient! </p> 

<p> Namely the Friends are: </p> 

<p> 🐣🎩🍕👩‍❤️‍💋‍👨 Joey Tribbiani </p> 

<p> 👛🐱🎤🎸 Phoebe Buffay </p> 

<p> 👠💄💅👗 Rachel Green </p> 

<p> 💍👞🙊📚 Ross Geller </p> 

<p> 🛁👓🎾 Chandler Bing </p> 

<p> 🎂🧽👜👙 Monica Geller </p> 

<p> Hope you've enjoyed my work, stick around for more! </p> 

<p> All copyrights for the display cover image of Friends are owned by the official FRIENDS American Tv Show and its creators. No copyrights for the display cover image presented are reserved by me! </p> 

<hr>
<p>Be safe, code safer!</p>
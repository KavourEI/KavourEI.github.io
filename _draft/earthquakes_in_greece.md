---
layout: post
current: post
cover:  assets/images/lda_fund/lda_basic_0.jpg
navigation: True
title: Earthquakes in Greece for the period 1901 - 2018
date: 2021-9-30
tags: [EDA]
class: post-template
subclass: 'post'
author: Kavour
---

<p> Exploratory Data Analysis of a data dataset found in Kaggle about the earthquakes that have taken place in Greece for the period 1901 - 2018. I have used Jupyter Notebook for the analysis, with Python 3 interpreter.  </p>

<p> Initially, I am going to import all the required libraries that I need to complete this EDA analysis with Python programming language. </p>

<pre><code>
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import emoji
import folium

from Plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot
import cufflinks as cf
import plotly.graph_objects as go
import plotly.express as px

%matplotlib inline
sns.set_style('darkgrid')

data = pd.read_csv('/.../Datasets/Earthquake in Greece (1901- - 2018) Dataset /EarthQuakes in Greece.csv')
</code></pre>

<p> Initially we need to get a glance of the data frame we have just created.... Let's have a look: </p>

<pre><code>
data.head()
</code></pre>

<p> As we can see the dataset does not have many attitudes. With a quick look every one of them seems well established and understandable. Namely we have: </p>

<ul>
<li> Year: the year that the mentioned earthquake occurred </li>
<li> Month: the month that the mentioned earthquake occurred </li>
<li> Date: the day that the mentioned earthquake occurred (will be changed to 'Day') </li>
<li> Hours: the hour that the mentioned earthquake occurred (will be changed to 'Hour') </li>
<li> Minutes: the minutes that the mentioned earthquake occurred (will be changed to 'Minute') </li>
<li> LATATITUDE (N): the latitude that the mentioned earthquake took place (will be changed to 'Latitude') </li>
<li> LONGITUDE (E): the longitude that the mentioned earthquake took place (will be changed to 'Longitude') </li>
<li> MAGNITUDE (Richter): the strength of the mentioned earthquake in Richter Scale (will be changed to 'Magnitude') </li>
</ul>

<p> In order to get some more statistical descriptive information about the data frame, before I apply the changes I mentioned above, I choose to proceed as following: </p>

<pre><code>
data.info()

data.describe()
</code></pre>

<p> We know that the only attitude that there is a point in checking the descriptive statistics is Magnitude (Richter) (By clicking the red box below you can find out more about the Richter scale, if interested). As a result we can understand that the minimum is 0.0 R and the maximum is 8.0 R. First of all I am going to correct the name of the attributes and make them more "user friendly". I am going, later on, to erase, all the earthquakes reported below 1.0R as those are noticed only by machines and do not cause any damage to the buildings.  </p>

<p> As for the rest, I can say the following. For the attribute Year for example, the mean is translated on the following concept. At the year 2008 it is appeared to be 50% of the earthquakes that are noted. If we take a step back we can see that such a 'saying' does not make any sense since a huge amount of seismic activity was not reported due to underdeveloped seismic machinery. This explanation also applies for the attributes Month, Date, Hours, Minutes, LONGITUDE (N) and LONGITUDE (E). </p>

<p> As a result, I now will proceed by applying the changes that I have pointed out about the column names. </p>

<pre><code>
data.columns

columns = ['Year', 'Month','Day','Hour', 'Minute', 'Latitude(N)','Longitude(E)','Magnitude(R)']
data.columns = columns

data.head()
</code></pre>

<p> AAAAAahhh much better now!!! 👌 Now let me erase all the earthquakes that are not needed, as I have mentioned before! </p>

<pre><code>
data_0 = data[data['Magnitude(R)'] >= 1.0]
</code></pre>

<p> Now we need to check how many earthquakes, of those remained, happened in each of the years that passed. I will also compute a graph showing the mean value of the earthquakes that occurred per year. </p>

<pre><code>
annual_nbr = data_0.groupby(by = 'Year').size()
print(annual_nbr)

init_notebook_mode(connected = True)
cf.go_offline()

fig = go.Figure(data=[go.Table(header=dict(values=['Year', 'Number of Earthquakes']),
                 cells=dict(values=[annual_nbr.index, annual_nbr]))
                     ])
fig.update_layout(
    title="Number of Earthquakes, in Greece, per Year (1901 - 2018).")
fig.show()
</code></pre>

<p> Of course there are many many rows til 2018 though due to technical issues it is not possible to be displayed here. If you copy paste all the code cells until this very step, you will be able to see all the rows in your notebook or Python IDE. </p>

<pre><code>
annual_nbr.iplot(kind = 'bar', theme = 'solar', 
                 title = 'Number of Earhtquakes, in Greece, per year (1901 - 2018)', 
                 xTitle = 'Year', yTitle = 'Number of earthquakes')
</code></pre>

<p> As we can see both from the table as well as the graph created above, after the year 1966 (with 190 earthquakes noted) or 1967 (with 322 earthquakes noted) the number of incidents, started increasing rapidly. Before the afforementioned years, we can see that the number of earthquakes in Greece was relatevely low. </p>

<p> As all of you reading this file, I was curious as to why is that happening and decided to conduct some further research, 🤔🧐. Alas! After searching around the web, I found the following: </p>

<p> By the U.S. Geological Survey:  </p>

<p> "The ComCat earthquake catalog contains an increasing number of earthquakes in recent years--not because there are more earthquakes, but because there are more seismic instruments and they are able to record more earthquakes." </p>

<p> By the British Geological Survey: </p>

<p> "There are a number of reasons why it might seem as if we are experiencing more earthquakes. </p>

<p> Earthquakes in populated places are far more noticed than the many that occur in remote regions, so when, by chance, a run of earthquakes hit population centres, it appears that the number of events has increased. Also, there are more people at risk. Population increases mean there are more people than ever in earthquake prone regions. So although the number of earthquakes remains the same the impact increases. </p>

<p> Earthquake clustering. Although long term averages are fairly constant, in any quasi-random process, you get clustering in time. Increases and decreases in seismicity rates are a natural part of this. People notice the clusters; they don't notice the gaps in between. They also forget the previous cluster! </p>

<p> Global communication. Vast improvements in global communications mean we have near instant pictures of devastating earthquakes from all around the world. This means more people are aware of earthquakes and their impact." </p>

<p> By the OpenMind BBVA: </p>

<p> "However, the world population continues to grow, and it also does so in seismically active areas. This is why even though the frequency of earthquakes has not varied, their social, political and economic impact has certainly increased." </p>

<p> As a result of the reasons above, we can accept and the number of incidents and this rapid increase. </p>

<p> Now let us check whether those number of earthquakes are major or minor. Therefore, there is a huge need to move back to the updated data_0 dataframe and conduct a research for the attribute with name Magnitude(R), in order to extract a conclusion. Sit back, relax and (hopefully) enjoy!  </p>

<p> Initially, with the help of a histogram we will find out how many times each level of Magnitude from the list reported earthquakes occured. </p>

<pre><code>
data_0['Magnitude(R)'].iplot(kind = 'histogram', theme = 'solar', 
                             title = 'Frequency per level of reported earthquake', 
                             xTitle = 'Magnitute (R)', 
                             yTitle = "Number of earthquakes reported")
</code></pre>

<p> From the histogram provided above, we can see that there are just a few severe earthquakes that happened to Greece. For starters let us take a look of them, just them! </p>

<pre><code>
severe_earth = data_0[data_0['Magnitude(R)'] >= 7.1

severe_earth_0 = severe_earth.sort_values(by='Magnitude(R)', ascending = False)

severe_earth_0.head()

my_map = folium.Map(location=[severe_earth['Latitude(N)'].mean(), 
                    severe_earth['Longitude(E)'].mean()], zoom_start = 6, 
                    control_scale = True)

folium.Marker(
    location=[36.30, 23.00],
    popup="Monday, 11 August 1903 (04:32) ~ 8.0 R",
    icon=folium.Icon(icon="glyphicon glyphicon-star-empty", color= 'red')
).add_to(my_map)

folium.Marker(
    location=[41.8, 23.1],
    popup="Sunday, 4 April 1904 (10:25) ~ 7.8 R",
    icon=folium.Icon(icon="glyphicon glyphicon-star-empty", color= 'red')
).add_to(my_map)

folium.Marker(
    location=[40.3, 24.4],
    popup="Tuesday, 8 November 1905 (22:06) ~ 7.4 R",
    icon=folium.Icon(icon="glyphicon glyphicon-star-empty", color= 'red')
).add_to(my_map)

folium.Marker(
    location=[40.20, 27.52],
    popup="Wednesday, 18 March 1953 (19:06) ~ 7.4 R",
    icon=folium.Icon(icon="glyphicon glyphicon-star-empty", color= 'red')
).add_to(my_map)

folium.Marker(
    location=[36.64, 25.91],
    popup="Monday, 9 July 1956 (03:11) ~ 7.4 R",
    icon=folium.Icon(icon="glyphicon glyphicon-star-empty", color= 'red')
).add_to(my_map)

my_map
</code></pre>

<p> Acording to Wikipedia (yes, I know, wikipedia...), this 8.0R earthquake was the srongest earthquake that occured during that year. The fatalities of this earthquake were just 2. On the other hand the most fatal earthquake that took place in 1903 was with a Magnitude of 6.3R in Ottoman Empire, Turkey, Mus Province, where there have been counted 3560 deaths. Let us take a quick look where this Mus Province is and how far is it from Greece, the country of our interest in this analysis. </p>

<pre><code>
my_map_2 = folium.Map(location=[39.14, 42.65], zoom_start = 4, 
                    control_scale = True)

folium.Marker(
    location=[39.14, 42.65],
    popup="Monday, 28 April 1903 (01:30) ~ 8.0 R",
    icon=folium.Icon(icon="glyphicon glyphicon-star-empty", color= 'red')
).add_to(my_map_2)

my_map_2
</code></pre>



<pre><code>
df = px.data.iris()

fig.px.scatter(data_0, x = 'Month', y = 'Year', color = 'Magnitude(R)', title = 'Magnitude of the reported earthquakes, by Month and by Year (1901 - 2018)' )

fig.show()
</code></pre>

<p> From the scatterplot presented just above, we can clearly derive the following conclusion. As the years pass by, less powerful earthquakes start to appear more frequent. This is a result of the technological evolution. As years pass by, human try to achieve perfection in everything, as a result, seismographic machines are evoluting along with the idea of perfection. Hence, newer seismographic machines have more capabilities and much higher sensitivity. This is the main resaon that lately are more earthquakes reported than in the older times, and even less powerful ones. </p>

<hr>
<p>Be safe, code safer!</p>
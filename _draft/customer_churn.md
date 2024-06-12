 ---
layout: post
current: post
cover:  assets/images/lda_fund/lda_basic_0.jpg
navigation: True
title: Customer Churn - A classification ml method
date: 2022-9-27
tags: [Machine Learning, Classificaiton]
class: post-template
subclass: 'post'
author: Kavour
---

<p>In this project, our aim is to predict the customers' churn. In a much wider sense to present ML models one can use for classification projects We will try to predict our customers' intention to change their preference when it comes to the brand to cover their needs or just leave us in the future. We will complete this task with the help of R-programming. Of course before the model building, we will try and understand our data by an EDA section. To follow along, you can find the data in the following link:</p>

<p>Without further do, let us begin our adventure. Initially, we will import the libraries that will help us reach the end of this story.</p>

<pre><code>
library(readxl)
library(ggplot2)
library(tidyverse)
library(caret)
library(gmodels) # CrossTable
library(e1071) # Naive Bayes ML Model
library(C50) # Decision Tree ML Model
</code></pre>

<p>There is no statistical/machine learning quest without data, am I right?</p>

<pre><code>
churn <- read_xlsx(path = '.../Customer_Chunk_Data.xlsx',
          col_names = TRUE, 
          skip = 1)
</code></pre>

<p>Before the beginning of our classification journey, we will need to normalise all the numeric features. As a result, we will define the function that will help us complete this goal.</p>

<pre><code>
min_max_norm <- function(x) {
  (x - min(x)) / (max(x) - min(x))
}
</code></pre>

<p>Ok so, we have the libraries, we imported some data, I believe it is time to take a first look at what the data consist of. So,</p>

<pre><code>
churn %>% 
  glimpse()

Rows: 7,043
Columns: 21
$ customerID       <chr> "7590-VHVEG", "5575-GNVDE", "3668-QPYBK", "7795-CFOCW", "9237-HQITU", "9305-CDSKC", "145…
$ gender           <chr> "Female", "Male", "Male", "Male", "Female", "Female", "Male", "Female", "Female", "Male"…
$ SeniorCitizen    <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0…
$ Partner          <chr> "Yes", "No", "No", "No", "No", "No", "No", "No", "Yes", "No", "Yes", "No", "Yes", "No", …
$ Dependents       <chr> "No", "No", "No", "No", "No", "No", "Yes", "No", "No", "Yes", "Yes", "No", "No", "No", "…
$ tenure           <dbl> 1, 34, 2, 45, 2, 8, 22, 10, 28, 62, 13, 16, 58, 49, 25, 69, 52, 71, 10, 21, 1, 12, 1, 58…
$ PhoneService     <chr> "No", "Yes", "Yes", "No", "Yes", "Yes", "Yes", "No", "Yes", "Yes", "Yes", "Yes", "Yes", …
$ MultipleLines    <chr> "No phone service", "No", "No", "No phone service", "No", "Yes", "Yes", "No phone servic…
$ InternetService  <chr> "DSL", "DSL", "DSL", "DSL", "Fiber optic", "Fiber optic", "Fiber optic", "DSL", "Fiber o…
$ OnlineSecurity   <chr> "No", "Yes", "Yes", "Yes", "No", "No", "No", "Yes", "No", "Yes", "Yes", "No internet ser…
$ OnlineBackup     <chr> "Yes", "No", "Yes", "No", "No", "No", "Yes", "No", "No", "Yes", "No", "No internet servi…
$ DeviceProtection <chr> "No", "Yes", "No", "Yes", "No", "Yes", "No", "No", "Yes", "No", "No", "No internet servi…
$ TechSupport      <chr> "No", "No", "No", "Yes", "No", "No", "No", "No", "Yes", "No", "No", "No internet service…
$ StreamingTV      <chr> "No", "No", "No", "No", "No", "Yes", "Yes", "No", "Yes", "No", "No", "No internet servic…
$ StreamingMovies  <chr> "No", "No", "No", "No", "No", "Yes", "No", "No", "Yes", "No", "No", "No internet service…
$ Contract         <chr> "Month-to-month", "One year", "Month-to-month", "One year", "Month-to-month", "Month-to-…
$ PaperlessBilling <chr> "Yes", "No", "Yes", "No", "Yes", "Yes", "Yes", "No", "Yes", "No", "Yes", "No", "No", "Ye…
$ PaymentMethod    <chr> "Electronic check", "Mailed check", "Mailed check", "Bank transfer (automatic)", "Electr…
$ MonthlyCharges   <chr> "29.85", "56.95", "53.85", "42.3", "70.7", "99.65", "89.1", "29.75", "104.8", "56.15", "…
$ TotalCharges     <chr> "29.85", "1889.5", "108.15", "1840.75", "151.65", "820.5", "1949.4", "301.9", "3046.05",…
$ Churn            <chr> "No", "No", "Yes", "No", "Yes", "Yes", "No", "No", "Yes", "No", "No", "No", "No", "Yes",…
</code></pre>


<p> We can initially see some changes that need to be done in the data types, but before getting in that place, let us try and understand what each feature represent. We have 7043 rows full of data waiting us to explore. we have 20 features that will help is build a model that will predict the 21st feature (aka Churn). With no further do, let us take our features one by one and try to understand the meaning.</p>

<ul>
<li> customerID : A customer ID which is unique for each customer (we will check the uniqueness in a while, hopefully I am not wrong about this one).</li>
<li> gender : The gender of the customer </li>
<li> SeniorCitizen : The seniority of each customer (I believe that this refers to the age, meaning if a customer is under or over the age of 18) </li>
<li> Partner : Whether the customer has a partner or not </li>
<li> Dependents : Whether the customer depends on someone else </li>
<li> tenure : I don't really have any clue of what this variable could mean. (If you have some idea, let me know in the comments bellow!) </li>
<li> PhoneService : Whether the customer got a phone service </li>
<li> MultipleLines : Whether the customer is owner of multiple lines. </li>
<li> InternetService : The kind of internet service owned by the customer. </li>
<li> OnlineSecurity : Whether the customer owns some kind of online security. </li>
<li> OnlineBackup : Whether the customer owns some kind of Online Backup. </li>
<li> DeviceProtection : Whether the customer owns some kind of Device Protection service. </li>
<li> TechSupport : Whether the customer owns some kind of Technical Support service. </li>
<li> StreamingTV : Whether the customer owns Streaming TV services. </li>
<li> StreamingMovies : Whether the customer owns Streaming Movies services. </li>
<li> Contract : The kind of  contract made with the customer. </li>
<li> PaperlessBilling : Whether the customer get his/hers bills vial physical mail or not. </li>
<li> PaymentMethod : The desired method of payment. </li>
<li> MonthlyCharges : What are the monthly charges of the customer. </li>
<li> TotalCharges : What are the total charges of the customer. </li>
<li> Churn : Whether the customer will leave us or not. </li>
<ul>

<p>Now let us try to change all the issues that we spotted with a .. glimpse! (You see what I did there? 😉🥲) </p>

<p>Initially we will make sure that the customerID feature is unique for each customer. This will be done by checking if we have any value appearing twice. We know that there exist 7043 rows by the initial glimpse function. There are many ways for one to do certain things in R, as well as finding the number of duplicates. Here I will stick to using the tidy verse functions instead of base ones.</p>

<pre><code>
churn %>% 
  select(customerID) %>% 
  distinct() %>% 
  summarise(n())

# A tibble: 1 × 1
  `n()`
  <int>
1  7043
</code></pre>

<p>As we can see there are still 7043 values. This implies that the values of this feature are indeed unique per customer. Next we will convert the Male-Female or Yes-No features to factor. But before getting to that point, let us check some variables that should be (possibly) part of this conversion.</p>

<pre><code>
churn %>% 
  distinct(MultipleLines)

# A tibble: 3 × 1
  MultipleLines   
  <chr>           
1 No phone service
2 No              
3 Yes  
</code></pre>

<pre><code>
churn %>% 
  distinct(InternetService)

# A tibble: 3 × 1
  InternetService
  <chr>          
1 DSL            
2 Fiber optic    
3 No  
</code></pre>

<pre><code>
churn %>% 
  distinct(Contract

# A tibble: 3 × 1
  Contract      
  <chr>         
1 Month-to-month
2 One year      
3 Two year      
</code></pre>

<pre><code>
churn %>% 
  distinct(PaymentMethod)

# A tibble: 4 × 1
  PaymentMethod            
  <chr>                    
1 Electronic check         
2 Mailed check             
3 Bank transfer (automatic)
4 Credit card (automatic)  
</code></pre>

<p>As you can see those features need indeed to be part of the conversion to factor variables.</p> 

<pre><code>
churn_fct <- churn %>%  
  select(everything()) %>% 
  mutate_at(vars(-c(customerID,tenure,MonthlyCharges, TotalCharges)), factor)
churn_fct %>% 
  select(customerID, gender, SeniorCitizen,Partner,Dependents) %>% 
  glimpse()

Rows: 7,043
Columns: 5
$ customerID    <chr> "7590-VHVEG", "5575-GNVDE", "3668-QPYBK", "7795-CFOCW", "9237-HQITU", "9305-CDSKC", "1452-K…
$ gender        <fct> Female, Male, Male, Male, Female, Female, Male, Female, Female, Male, Male, Male, Male, Mal…
$ SeniorCitizen <fct> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1…
$ Partner       <fct> Yes, No, No, No, No, No, No, No, Yes, No, Yes, No, Yes, No, No, Yes, No, No, Yes, No, No, Y…
$ Dependents    <fct> No, No, No, No, No, No, Yes, No, No, Yes, Yes, No, No, No, No, Yes, No, Yes, Yes, No, No, N…
</code></pre>

<p>Next stop is conversion of Charges to numeric.</p>

<pre><code>
churn_dbl <- churn_fct %>% 
  select(everything()) %>% 
  mutate_at(vars(MonthlyCharges, TotalCharges),as.numeric)
churn_dbl %>% 
  select(customerID, MonthlyCharges, TotalCharges) %>% 
  glimpse()

Rows: 7,043
Columns: 3
$ customerID     <chr> "7590-VHVEG", "5575-GNVDE", "3668-QPYBK", "7795-CFOCW", "9237-HQITU", "9305-CDSKC", "1452-…
$ MonthlyCharges <dbl> 29.85, 56.95, 53.85, 42.30, 70.70, 99.65, 89.10, 29.75, 104.80, 56.15, 49.95, 18.95, 100.3…
$ TotalCharges   <dbl> 29.85, 1889.50, 108.15, 1840.75, 151.65, 820.50, 1949.40, 301.90, 3046.05, 3487.95, 587.45…
</code></pre>

<p>Now it is time to check whether there are any NA values in our dataset. Initially, we will make sure that all the features will be shown.</p>

<pre><code>
options(pillar.print_max = 21)

churn_dbl %>% 
  select(everything()) %>% 
  summarise_all(funs(sum(is.na(.)))) %>% 
  pivot_longer(data = .,cols = 1:21, names_to = "Features") %>% 
  mutate(NA_Values = value) %>% 
  select(Features, NA_Values)

# A tibble: 21 × 2
   Features         NA_Values
   <chr>                <int>
 1 customerID               0
 2 gender                   0
 3 SeniorCitizen            0
 4 Partner                  0
 5 Dependents               0
 6 tenure                   0
 7 PhoneService             0
 8 MultipleLines            0
 9 InternetService          0
10 OnlineSecurity           0
11 OnlineBackup             0
12 DeviceProtection         0
13 TechSupport              0
14 StreamingTV              0
15 StreamingMovies          0
16 Contract                 0
17 PaperlessBilling         0
18 PaymentMethod            0
19 MonthlyCharges           0
20 TotalCharges            11
21 Churn                    0
</code></pre>

<p> As we can see we have 11 values in the feature TotalCharges that are displayed as NA Values. We will replace those NA Values with the average due to the big number of data we have on our hands.</p>

<pre><code>
churn_dbl$TotalCharges <- replace_na(churn_dbl$TotalCharges, mean(churn_dbl$TotalCharges, na.rm = TRUE))

options(pillar.print_max = 21)
churn_dbl %>% 
  select(everything()) %>% 
  summarise_all(funs(sum(is.na(.)))) %>% 
  pivot_longer(data = .,cols = 1:21, names_to = "Features") %>% 
  mutate(NA_Values = value) %>% 
  select(Features, NA_Values)
</code></pre>

# A tibble: 21 × 2
   Features         NA_Values
   <chr>                <int>
 1 customerID               0
 2 gender                   0
 3 SeniorCitizen            0
 4 Partner                  0
 5 Dependents               0
 6 tenure                   0
 7 PhoneService             0
 8 MultipleLines            0
 9 InternetService          0
10 OnlineSecurity           0
11 OnlineBackup             0
12 DeviceProtection         0
13 TechSupport              0
14 StreamingTV              0
15 StreamingMovies          0
16 Contract                 0
17 PaperlessBilling         0
18 PaymentMethod            0
19 MonthlyCharges           0
20 TotalCharges             0
21 Churn                    0
</code></pre>

<p>One is free to explore further this data set and practise his/hers statistical knowledge. Here we will move forward with the model creation. But before that let us take a closer look on the feature we are interested about the most.</p>

<pre><code>
churn_dbl %>% 
  select(Churn) %>% 
  group_by(Churn) %>% 
  summarize(Count = n()) %>% 
  ggplot(aes(x = reorder(Churn, -Count), y = Count , fill = Churn)) + 
  geom_col() + 
  labs(title = "Number of customers' churn status",
       x = "Churn",
       y = "Count") + 
  ggeasy::easy_center_title() + 
  geom_text(aes(label = Count), size = 5 , 
            colour = "black", 
            position = position_dodge(width = 0.75), 
            vjust = 1.5)
</code></pre>

<p>In this point we are going to builder first model. For our first try, are going to use Naive Bayes Classification method but first let us make create the train and test sets.</p>

<pre><code>
churn_num <- churn_dbl %>% 
  select(-customerID) %>% 
  mutate(across(c(tenure, MonthlyCharges, TotalCharges), min_max_norm))

set.seed(1)
trainIndex <- createDataPartition(churn_num$Churn, p = 0.7, list = FALSE, times = 1)
train_data <- churn_num[trainIndex,1:19]
train_label <- churn_num[trainIndex, 20]
test_data <- churn_num[-trainIndex, 1:19]
test_label <- churn_num[-trainIndex, 20]

churn_classifier <- naiveBayes(train_data, train_label$Churn)
churn_pred <- predict(churn_classifier, test_data)

CrossTable(churn_pred, test_label$Churn, 
           prop.chisq = FALSE, prop.c = FALSE, prop.r = FALSE,
           dnn = c('Predicted', 'Actual'))

   Cell Contents
|-------------------------|
|                       N |
|         N / Table Total |
|-------------------------|

 
Total Observations in Table:  2112 

 
             | Actual 
   Predicted |        No |       Yes | Row Total | 
-------------|-----------|-----------|-----------|
          No |      1076 |       108 |      1184 | 
             |     0.509 |     0.051 |           | 
-------------|-----------|-----------|-----------|
         Yes |       476 |       452 |       928 | 
             |     0.225 |     0.214 |           | 
-------------|-----------|-----------|-----------|
Column Total |      1552 |       560 |      2112 | 
-------------|-----------|-----------|-----------|
</code></pre>

<p>Looking at the table above, we can see that a total of 476 + 108 = 584 of  2112 Customer Churns were incorrectly classified (26.65%) a rather high percentage. Let us increase Laplace value and see what is going to be the result.</p>

<pre><code>
churn_classifier2 <- naiveBayes(train_data, train_label$Churn, laplace = 1)
churn_pred2 <- predict(churn_classifier2, test_data)
CrossTable(churn_pred2, test_label$Churn, 
           prop.chisq = FALSE, prop.c = FALSE, prop.r = FALSE,
           dnn = c('Predicted', 'Actual'))

   Cell Contents
|-------------------------|
|                       N |
|         N / Table Total |
|-------------------------|

 
Total Observations in Table:  2112 

 
             | Actual 
   Predicted |        No |       Yes | Row Total | 
-------------|-----------|-----------|-----------|
          No |      1076 |       109 |      1185 | 
             |     0.509 |     0.052 |           | 
-------------|-----------|-----------|-----------|
         Yes |       476 |       451 |       927 | 
             |     0.225 |     0.214 |           | 
-------------|-----------|-----------|-----------|
Column Total |      1552 |       560 |      2112 | 
-------------|-----------|-----------|-----------|
</code></pre>

<p>We can see that our action brought no improvement in the prediction. We can even say that made things worst as there is one extra False Positive prediction. In order for one to improve Naive Bayes he/she needs to follow the next list and try to modify the data in order and rerun the whole process. The list :</p>

<ol>
<li> Remove the correlated features </li>
<li> Use Log Probabilities </li>
<li> Handle Text/Continuous Data </li>
<li> Re-train the model </li>
</ol>

<p>We tried under the hood to complete some of those steps before running the mode, but it seems that if you want to use Naive Bayes in this problem, you should work further with the data. Let us continuous to a different type of model. This is Classification Using Decision Trees. Let us build our starting tree and see how we did.</p>

<pre><code>
set.seed(2)
           churn_tree <- C5.0(train_data, as.factor(train_label$Churn))
tree_predict <- predict(churn_tree, test_data)
CrossTable(tree_predict, test_label$Churn, 
           prop.chisq = FALSE, prop.c = FALSE, prop.r = FALSE,
           dnn = c('Predicted', 'Actual'))

   Cell Contents
|-------------------------|
|                       N |
|         N / Table Total |
|-------------------------|

 
Total Observations in Table:  2112 

 
             | Actual 
   Predicted |        No |       Yes | Row Total | 
-------------|-----------|-----------|-----------|
          No |      1374 |       262 |      1636 | 
             |     0.651 |     0.124 |           | 
-------------|-----------|-----------|-----------|
         Yes |       178 |       298 |       476 | 
             |     0.084 |     0.141 |           | 
-------------|-----------|-----------|-----------|
Column Total |      1552 |       560 |      2112 | 
-------------|-----------|-----------|-----------|
</code></pre>

<p>We can see an improvement as there are 178 + 262 = 440 incorrect classifications with the assistance of Decision Trees ( 20.83%). The percentage is still very high, though seems better than Naive Bayes machine learning model. Let us try and improve this one. </p>


One way the C5.0 algorithm improved upon the C4.5 algorithm was through the addition of adaptive boosting. This is a process in whiny decision trees are built and the trees vote on the best class for each example
Machine Learning with R by Brett Lantz.

<p>So here we are going to use this upgrade and see whether this could assist us predict the Customer Churns more accurate. In case you would like to find out more about the secret paths behind trials, I would advice you to start from here. Anyways, we have the following.</p>

<pre><code>
churn_tree2 <- C5.0(train_data, as.factor(train_label$Churn), trials = 3 )
tree_predict2 <- predict(churn_tree2, test_data)
CrossTable(tree_predict2, test_label$Churn, 
           prop.chisq = FALSE, prop.c = FALSE, prop.r = FALSE,
           dnn = c('Predicted', 'Actual'))

   Cell Contents
|-------------------------|
|                       N |
|         N / Table Total |
|-------------------------|

 
Total Observations in Table:  2112 

 
             | Actual 
   Predicted |        No |       Yes | Row Total | 
-------------|-----------|-----------|-----------|
          No |      1400 |       271 |      1671 | 
             |     0.663 |     0.128 |           | 
-------------|-----------|-----------|-----------|
         Yes |       152 |       289 |       441 | 
             |     0.072 |     0.137 |           | 
-------------|-----------|-----------|-----------|
Column Total |      1552 |       560 |      2112 | 
-------------|-----------|-----------|-----------|
</code></pre>

<p>We can see that the result has further improved. We now have 152+271 = 423 incorrect classified Customer Churns (20.02%). Remember that before the addition of the argument trials we had 440 (20.83%) incorrect predictions. One can take this a step further and search for an even better value of the aforementioned argument. Here I will take this post to a different path.</p>

Everything has a price!
by Anne Bishop

<p>Let me rephrase this. I would rather say that everything has a cost, though the question, in our case, should be what costs more(?). I believe that the cost is higher when the prediction says that people are going to stay in from a business and they don't. Meaning that we predict 'No' and the actual result is 'Yes'. So we have the option to set a different kind of cost values.</p>

<pre><code>
dimensions <- list(c("No","Yes"),c("No","Yes"))
names(dimensions) <- c("Predicted","Actual")
error_costs <- matrix(c(0,1,2,0), nrow = 2, dimnames = dimensions)
error_costs

         Actual
Predicted No Yes
      No   0   2
      Yes  1   0
</code></pre>

<pre><code>
churn_tree3 <- C5.0(train_data, as.factor(train_label$Churn), trials = 3, costs = error_costs)
tree_predict3 <- predict(churn_tree3, test_data)
CrossTable(tree_predict3, test_label$Churn, 
           prop.chisq = FALSE, prop.c = FALSE, prop.r = FALSE,
           dnn = c('Predicted', 'Actual'))

   Cell Contents
|-------------------------|
|                       N |
|         N / Table Total |
|-------------------------|

 
Total Observations in Table:  2112 

 
             | Actual 
   Predicted |        No |       Yes | Row Total | 
-------------|-----------|-----------|-----------|
          No |      1264 |       192 |      1456 | 
             |     0.598 |     0.091 |           | 
-------------|-----------|-----------|-----------|
         Yes |       288 |       368 |       656 | 
             |     0.136 |     0.174 |           | 
-------------|-----------|-----------|-----------|
Column Total |      1552 |       560 |      2112 | 
-------------|-----------|-----------|-----------|
</code></pre>

<p>We can clearly see that this did not worked in our case, but as a practise is nice to keep it in the back of our heads. Next we are going to try Random Forest to see how this will do in our case.</p>

<pre><code>
churn_rf <- randomForest(train_data, train_label$Churn)
churn_rf_p <- predict(churn_rf, test_data, type = "response")
CrossTable(churn_rf_p, test_label$Churn, 
           prop.chisq = FALSE, prop.c = FALSE, prop.r = FALSE,
           dnn = c('Predicted', 'Actual'))

   Cell Contents
|-------------------------|
|                       N |
|         N / Table Total |
|-------------------------|

 
Total Observations in Table:  2112 

 
             | Actual 
   Predicted |        No |       Yes | Row Total | 
-------------|-----------|-----------|-----------|
          No |      1391 |       276 |      1667 | 
             |     0.659 |     0.131 |           | 
-------------|-----------|-----------|-----------|
         Yes |       161 |       284 |       445 | 
             |     0.076 |     0.134 |           | 
-------------|-----------|-----------|-----------|
Column Total |      1552 |       560 |      2112 | 
-------------|-----------|-----------|-----------|
</code></pre>

<p>We can see that this model predicted 161+277=437 incorrect Customer Churn cases (20.7%). If you can recall, we had earlier a better result. Hence we drop the idea of usage of this model. Those are some of the ideas one could approach a problem of Customer Churn, and a classification problem in general. </p>

<p>I would advice you to take a step back and dig deeper into the data. With a better preprocessing, one could achieve a much higher accuracy percentage than an 80% that we got here. Remember this was achieved with a rather high level of preprocessing.</p>

<p>I hope you enjoyed this analysis, as much as I did. Hopefully you have gained some useful information, and will return in the future to copy some part of it and use it for your own analysis.</p>

<hr>
<p>Be safe, code safer!</p>
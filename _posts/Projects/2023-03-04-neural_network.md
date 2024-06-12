---
layout: post
current: post
cover: assets/images/nn_application/0_nn_application.jpg
navigation: True
title: Neural Network ~ Predicting a Numerical Value
date: 2023-03-04
tags: [Deep Learning]
class: post-template
subclass: 'post'
author: Kavour
---


<p>Welcome back! As part of this introductory series on Neural Networks, we will be exploring the process of building NNs and making decisions about their topology. This includes determining the number of layers, the number of neurons per layer, selecting appropriate activation functions, and implementing backpropagation. Throughout this process, we will delve into various factors to consider when building an effective neural network. Though everything is statistics (😉) I will try to keep statistical formulas to the minimum possible level.</p>

<p>Without further ado let's jump right into fun (hopefully!).  In this post we will be building two differenct neural network models to predict numerical values :</p>

<ul>
<li>A model to predict the strength of concrete strength.</li>
<li>A model to predict the prices of houses in Paris (Why Paris? Don't know just cause! We don't need a reason for everything, accept it 😛)</li>
</ul>

<p>Initially, I planned to explain the concepts and decision-making process between the code chunks. However, I understand that some readers may prefer to just jump straight into the code and results. Therefore, I will provide a summary of the topics I plan to cover at the top of the post and keep the code and results at the bottom for those who prefer that approach. No judgement here - feel free to choose what works best for you! Or is there some judgement? Just kiding, choose your way (or am I not? 😛)</p>

<p>When we encounter a neural network, the first thing that typically stands out to us is the layer structure. Before we dive into understanding the movement, input features, activation functions, or weights, we need to have a solid grasp of the layers in a neural network. So let's start from there.</p>

<blockquote>
<p>How to decide the number of the layers?</p>
</blockquote>


<p>To be honest, there is no solid way or any rule of thumb to calculate the number of layers needed for any type of problem you are trying to solve. As a result, deciding on the number of layers can be a challenging task. However, there are some general guidelines that can help:</p>

<ol>
  <li> <strong>Start small</strong>: Beginning with a simple network structure with just a few layers can help to avoid overfitting and to gradually increase the complexity as needed. Remember the goal is to find the simplest model possible not the most complex one. A small network with few layers is called shallow neural network. </li>
  <li> <strong>Research pre-existing architectures</strong>: If possible, consider using pre-existing network architectures that have proven effective in solving similar problems. I know you want to build your own model and you want to be independent, but your mother's cooked food is always better than yours, right? So try searching around for your mom, I mean a built model that is proven to work efficiently and the try adjusting this to your own needs. </li>
  <li> <strong>Get to know your data</strong>: Having a large amount of training data can support deeper and more complex neural networks. </li>
  <li> <strong>Practise, practise, practise..</strong>: The Mose effective way to find out the optimal number of layers your your specific needs and flavours, is through experimentation and testing difference architectures, so after completing the steps described above, play around, change the configurations and check the outcome. The time is your enemy and depending on the pc specs you run your tests on, hopefully, this won't take long per model build. </li>
</ol>

<p>Bottom line, there is no one rule that fits the all to determin the oprimal number of layers in a neural network. Only one mom to cook the perfect dish for every occation. The key is to balance the complexity of the network with the available resources and the data in your environment. Remember though, we aim for simplicity as choosing more that 2 layers, can get computationally expensive really fast.</p>

<blockquote>
<p>Fine with the layers, but how many neurons should we use per layer added in a model?</p>
</blockquote>

<p>If you search around the <a href="https://www.google.com">web</a> for information on determining the optimal number of neurons per layer in a neural network, you will come across several "rules of thumb" that suggest a range of options. Some of those are the following: </p>

<p>If you search for information on determining the optimal number of neurons per layer in a neural network, you may come across several "rules of thumb" that suggest a range of options. While these rules can provide a starting point, it's important to remember that the optimal solution may vary depending on the specific problem you are trying to solve. Therefore, it's important to also consider other factors such as the complexity of the problem, available resources, and experimentation with different architectures.</p>


<ul>
<li> The number of hidden neurons should be between the size of the input layer and the size of the output layer. </li>
<li> The number of the neurons should be 2/3 the size of the input layer, plus the size of the output layer. </li>
<li> The number of the hidden neurons should be less than twice the size of the input layer. </li>
</ul>

<p>While these ruls can provide a starting point, it's important to remember that the optimal solution may vary depending on the problem that you are trying to answer. Once again, I feel the need to remind you that we aim for the simpliest model possible, complexity costs and slow us down. Remember after all the most beutiful mathematical formulas are the simpliest ones. </p>

<p>While keeping that in mind, note that using less neurons than it is required may lead us to underfitting the data imported, while using more neurons than needed may end up to overfitting, high variance and increse the time it takes to train the network. </p>

<p>A way that may give us a good intuition on the number of neurons needed is using cross-validation method with different configurations (starting with the simplest possible) and compare the Mean Square Errors (MSE) in order to stick with the option that minimises MSE. Fill free to try this in the models we are going to build and find out a better model architecture for the models provided below.</p>

<blockquote>
<p>Cool cool cool.. No doubt.. How do we pass through the neurons and layers?</p>
</blockquote>
<iframe src="https://giphy.com/embed/XAdbHJywVjF5K" width="480" height="274" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/someone-gwen-stefani-XAdbHJywVjF5K"></a></p>
<p>For those two or three..</p>

<img src = "https://giphy.com/embed/XAdbHJywVjF5K"/>

<p>I am glad you asked.. (Did you? Hopefully you did, or I am hearing voices 👻). If you recall from the <a href="https://kavourei.github.io/neural_network_intro">introductory post</a> of this series, we mentioned the activation functions which we shall discuss later in this post, but I have not mentioned at all the work backpropagation though you may have come across in some posts. </p>

<p><a href="https://people.idsia.ch/~juergen/who-invented-backpropagation-2014.html">Backpropagation</a> is a fundamental algorithm in the training process. The main purpose that we use back propagation is to adjust the weights (the numbers above the arrows that you will come across later in a NN plot) of the neural network. The weights distinguish level of importance that every feature (through the neurons in the input layer) has. Recall the example of the house pricing. It is more important that it has proper roof than higher number of entrances.</p>

<p>Backpropagation works iteratively. This means that the algorithm is used many times to adjust the weights that the difference between the predicted outcome and the actual outcome through the training process is minimized. This is also known as the error. </p>

<p>The steps at every iteration is the following. After a full process is completed and the model has the first pair of results, the backpropagation (BP) algorithm is set to use. It starts from the end (output) to the beginning (input) of the model, that is why it is called -<strong>back</strong>-propagation. It computes the derivative of the error with respect to each weight in the network. This tells us (don't worry it is done without your contribution) how much each choice of weight has contributed to the final error acquired at the end, hence how much this can be adjusted. Then changes are made and then the model runs from the beginning to the end once again, producing a new error, and going back again calculating new weights. This back and forth is done many many times (hopefully, not that many) until the error is minimised.</p>

<p>With this repeation, the network grafually learns to map input data to output data more accurately. This process is often reffered as learning rate. Overall BP is a powerfull tool and helps us humans solve very complex problems. The formulation of this process to programm by hand can be really complex, but there is no need for that as R (and Python for anyone interested) gives us this as an option to choose amongst others.</p>

<blockquote>
<p>What is learning rate mentioned earlier?</p>
</blockquote>

<p>Well during the process of BP, we said that the weights are adjusted. Learning rate is the steps that we allow the algorithm to take. In other words, is the amount that we allow the algorithm to adjust the weights per iteration. </p>

<p>Now you may think that we can set this high so that the model will converge fast..</p>

<p>Am a sorry to be the party pooper (💩) here but setting learning rate high can lead our model to diverge. This can happen as the optimal choice of weight may be "jumped over" a big step of weight configuration. Image you search for a middle in the floor, you can not search while making huge steps. On the other hand, it is sure that making small steps will lead us to finding the middle though it make take time, so really small steps is not a good option as well. </p>

<p>Guess what?!? There is no method that tells us the learning rate no matter the problem. Some of the best practises are the following : </p>

<ul>
<li> <strong>Loss/Error VS Learning Rate</strong> : With this approach if you are patient, you have to plot the loss function vs the learning rate on a logarithmic scale, which will help us deside on a good range of learning rates to use. On the range that has been prompted, we have to use the largest possible, as we want the model to converge without many iterations.</li>
<li> <strong>Grid Search</strong> : Again, if you are patient enough, by trying out different learning rates over the training values and evaluating the performance of the model on the validation set, can help you identify a good range of learning rates to use. </li>
</ul>

<p>I believe that was all I wanted to discuss about Neural Network configurations and really did not used any mathematical/statistical formulas at all!!! I hope you got the ideas presented above (as simple as possible). </p>

<p>Now it is time for the second part, the implementation. Bellow you will see two examples. The first implementation is from a really good book "<a href="https://www.amazon.com/Machine-Learning-techniques-predictive-modeling/dp/1788295862">Machine Learning with R</a>" providing you with as much information needed to get introduced to the topic and the other one from <a href="https://www.kaggle.com/">Kaggle</a>. All the data can be found <a href="https://github.com/stedy/Machine-Learning-with-R-datasets/blob/master/concrete.csv">here</a>. </p>

<p>As usuall, we are going to start with importing the libraries. We are going to use <em>caret</em> library in order to split the data randomly. The library <em>neuralnet</em> to build neural network models. The last library, <em>sigmoid</em>, is worth noting as it contains all the activation functions mentioned in the previous post. I you feel like it take a moment and search for the document of this last one, in order to check what are the functions included in there, so you dop't have to define them from the ground.</p>

<pre><code>
library(caret)
library(neuralnet)
library(sigmoid)
</code></pre>

<p>Moving forward we are going to load the data for the first example, the concrete one.</p>

<pre><code>
data1_init <- read.csv('/Users/.../concrete.csv')

str(data1_init)
</code></pre>

<p>As we can see we have the 8 input features and the last one that is the output to be predicted feature, the strength of the concrete. All the models perform much better with normalised data. There are many ways to do that, it's one with some unique pros and cons (It is out of this post's scope to dive into that). Some to mention are the normalise with log transformation, with Min-Max values (which we are going to use) or with stars scaling (also called standardisation). In order to perform the normalisation selected, there are two ways to go.</p>

<ul>
<li>Define the process as a custom function </li>
<li>With the usage of the functions <em>preProcess</em> and predict. In the first one you choose the type through the argument <em>mehtod</em> and then by passing through the second function you apply this method to the data you want.</li>
</ul>

<p>Let's define our normalisation function, which will be clearer how the process works and then apply the normalisation function to the data imported:</p>

<pre><code>
custom_norm <- function(x){
  return((x-min(x))/(max(x)-min(x)))
}
data1_norm <- as.data.frame(lapply(data1_init, custom_norm))

str(data1_norm)
</code></pre>

<p>Now we need to split the data to train and test datasets. Though a better practise is to split data in three parts, train, validation and test datasets, we will use the simpler way as the point of the posts is to get solid foundations and build upon that on later steps and further experimentation. In order to split the data we run the following :</p>

<pre><code>
set.seed(1)
trainIndex <- createDataPartition(data1_norm$strength,
                                  p = 0.7,
                                  list = FALSE,
                                  times = 1) 
data1_train <- data1_norm[trainIndex,]
data1_test <- data1_norm[-trainIndex,]
</code></pre>

<p>I use here the <em>set.seed(1)</em> so that if you copy and paste the code chunks you end up with the same results as me. The creatDataPartition help us create index to take the train and test sample according to the vector we will use as outcome. The second argument is used to define the amount of data we will split the data upon, here we use 70%.</p>

<p>Guess what time it is.. To build our first model. We are going to build the simplest model possible to start with and get an idea. We will use the function <em>neuralnet</em>. As the first argument, we define the data that we take the features from and then address the formula. Before the tilde ( '~' ) we define the output variable to be predicted and in the right of it we define the input features. By adding the dot, we indicate to the model to use all the other features available.</p>

<pre><code>
conc_model1 <- neuralnet(data = data1_train, strength ~ .)
plot(conc_model1)
</code></pre>
	
<p>This is our first Neural Network. Here we see the input layer (all the dots to the right), with the weights each feature is measured with the help of BP, the hidden layer (1) in the middle, where the logarithmic activation function is used (by default in neuralnet) and th outcome where layer. Bellow we can see the Error (which is the sum of squared errors (<strong>SSE</strong>)) and the number of training steps required for the model to converge.</p>

<p>In order to evaluate our first NN, we continue as listed below:</p>

<pre><code>
conc_results1 <- compute(conc_model1, data1_test[1:8])
conc_pred1 <- conc_results1$net.result
cor(conc_pred1,data1_test[9])
</code></pre>

<p>Correlation at 0.84, not bad for our first try, right? Let's run some more evaluation metrics though. I will use bellow the following :</p>

<ul>
<li> Mean Squared Error (<strong>MSE</strong>) : It represents the difference between the original and predicted values extracted by squared the average difference over the data set. </li>
<li> Mean Absolute Error (<strong>MAE</strong>) : It represents the difference between the original and predicted values extracted by the averaged absolute difference over the data set. </li>
<li> Root Mean Squared Error (<strong>RMSE</strong>) is the error rate by the square root of MSE </li>
<li> Coefficient of determination (<strong>R-squared</strong>) represents the coefficient of how well the values fit compared to the original values of a vanilla model. The value from 0 to 1 interpreted as percentages. The higher the value is, the better the model is. </li>
</ul>

<pre><code>
d1 = data1_test$strength-conc_pred1
mse = mean((d1)^2)
mae = mean(abs(d1))
rmse = sqrt(mse)
R2 = 1-(sum((d1)^2)/sum((data1_test$strength-mean(data1_test$strength))^2))
cat(" MAE:", mae, "\n", "MSE:", mse, "\n", 
    "RMSE:", rmse, "\n", "R-squared:", R2)
</code></pre>

<p>We can see that overall, the results we obtain are good. But there is always room for improvement. <strong>Perfection is the enemy of a good result</strong> after all!</p>

<pre><code>
conc_model2 <- neuralnet(data = data1_train, strength ~ ., hidden =5)
</code></pre>

<p>Here we have modified the single hidden layer, by adding 4 extra neurons (5 in total) through the argument of <em>hidden</em>.</p>

<pre><code>
plot(conc_model2) 
</code></pre>

<p>By the Error provided through the plot of the new NN model, we have a sign that we have improved the situation, though let us proceed to our model evaluation metrics introduced above.</p>

<pre><code>
conc_results2 <- compute(conc_model2, data1_test[1:8])
conc_pred2 <- conc_results2$net.result
cor(conc_pred2,data1_test[9])

d2 = data1_test$strength-conc_pred2
mse = mean((d2)^2)
mae = mean(abs(d2))
rmse = sqrt(mse)
R2 = 1-(sum((d2)^2)/sum((data1_test$strength-mean(data1_test$strength))^2))
cat(" MAE:", mae, "\n", "MSE:", mse, "\n", 
    "RMSE:", rmse, "\n", "R-squared:", R2)
</code></pre>

<p>We can clearly see that we have obtained from that small change. You can modify the model above by adding one or more layers and change the number of the neurons. Though this is like a sandbox where you can test different things, remember you always need to take care of the number of layers and neurons used as the most common error of the excitement while going closer to perfect prediction is overfitting.. In order to change the number of letters, we should modify the <em>hidden</em> argument in the <em>neuralnet</em> function. For example if we want 4 neurons in the first hidden layer and 5 in the second we should define it as </p>

<pre><code>
example_model <- neuralnet(..., hidden = c(4,5))
</code></pre>

<p>Apart from those there are many more arguments to modify your network like <em>startweights</em> which defines the starting value of each weight, <em>learningrate</em> which indicates the learning rate of your model, <em>algorithm</em> which let's you change the algorithm for weights adjustment (a.k.a. change the default backpropagation usage), <em>act.fct</em> which let's you choose activation function through your model, <em>err.fct</em> which gives you the power to use specific error calculating function and many many more, feel free to type <strong>neuralnet</strong> in your console to find out all of them!</p>

<p>The second example is an implementation of two neural network models. After followin the same normalization preprocessing and splitting steps as above for the data about house prices in Paris we have a 1-3-1 model  where the hidden layers will consist from 4 neurons each and a 1-1-1 model where the hidden layer will consist from 2 neurons, and compare the results. In those models, the ReLU activation function was used. </p>

<pre><code>
house_model0 <- neuralnet(data = house_train, price ~ .,hidden = c(2),act.fct = relu)
house_model1 <- neuralnet(data = house_train, price ~ .,hidden = c(4,4,4), act.fct = relu)

plot(house_model0)
plot(house_model1)
</code></pre>

<p>Now let us run all the evaluation metrics in order to compare the two models.</p>

<pre><code>
data.frame(Model_1 = c(cor21,mae21,mse21,rmse21,R2_21),
           Model_2= c(cor22,mae22,mse22,rmse22,R2_22),
           row.names = c('Correlation',"MAE:","MSE:","RMSE:","R-squared:"))
</code></pre>

<p>From the evaluation metrics, we can say that both our models do great at predicting the house prices. The reason that I have used these examples though is not to build the models, is to show to you that a much deeper model will not always result in a better situation. Apart from the result, the complexity and computational time needed to build the second model is much more than the first one. So keep in mind when playing around that we always aim for the simplest model possible that will give us the best results.</p>

<p>Thank you for reading this post, I hope you have learned something new and more importantly noe you are able to implement yourself neural netowrks to predict numerical values. There will be a new post about image recognition on the topic where we will use some different kind of neural networks. Anyways thank you all!</p>

<p>At this place I would like to especially thank the readers who send me their comments (both good and bad) and general remarks, with their help I become better and keep it going. So thank you guys!</p>

<hr>
<p>Be safe, code safer!</p>


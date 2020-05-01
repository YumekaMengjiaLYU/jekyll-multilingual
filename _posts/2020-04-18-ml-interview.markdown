---
layout: post
title:  "Preparing for Your ML Interview"
ref: welcome
date:   2020-04-18 
categories: career
lang: en
---

I bumped into this great [post][ref-1] on Udacity. So let's go through all these wonderful interview questions!

## Computer Science Fundamentals and Programming
Sample Questions
+ How would you check if a linked list has cycles?

+ Given two elements in a binary search tree, find their lowest common ancestor.

+ Write a function to sort a given stack.
+ What is the time complexity of any comparison-based sorting algorithm? Can you prove it?
+ How will you find the shortest path from one node to another in a weighted graph? What if some weights are negative?
+ Find all palindromic substrings in a given string.


## Probability and Statistics
Sample Questions
+ The mean heights of men and women in a population were calculated to be image00 and image01. What is the mean height of the total population?
+ A recent poll revealed that a third of the cars in Italy are Ferraris, and that half of those cars are red. If you spot a red car approaching from a distance, what is the likelihood that it is a Ferrari?
+ You’re trying to find the best place to put in an advertisement banner on your website. You can make the size (thickness) small, medium or large, and choose vertical position top, middle or bottom. At least how many total page visits (n) and ad clicks (m) do you need to say with 95% confidence that one of the designs performs better than all the other possibilities?


## Data Modeling and Evaluation
Sample Questions
+ A dairy farmer is trying to understand the factors that affect milk production of her cattle. She has been keeping logs of the daily temperature (usually 30-40°C), humidity (60-90%), feed consumption (2000-2500 kgs), and milk produced (500-1000 liters).
+ How would you begin processing the data in order to model it, with the goal of predicting liters of milk produced in a day?
+ What kind of machine learning problem is this?
+ Your company is building a facial expression coding system, which needs to take input images from a standard HD 1920×1080 pixel webcam, and continuously tell whether the user is in one of the following states: neutral, happy, sad, angry or afraid. When the user’s face is not visible in the camera frame, it should indicate a special state: none.
+ What class of machine learning problems does this belong to?
+ If each pixel is made up of 3 values (for red, green, blue channels), what is the raw input data complexity (no. of dimensions) for processing each image? Is there a way to reduce the no. of dimensions?
+ How would you encode the output of the system? Explain why.
+ Climate data collected over the past century reveals a cyclic pattern of rising and falling temperatures. How would you model this data (a sequence of average annual temperature values) to predict the average temperature over the next 5 years?
+ Your job at an online news service is to collect text reports from around the world, and present each story as a single article with content aggregated from different sources. How would you go about designing such a system? What ML techniques would you apply?

## Applying Machine Learning Algorithms and Libraries
Sample Questions
+ I’m trying to fit a single hidden layer neural network to a given dataset, and I find that the weights are oscillating a lot over training iterations (varying wildly, often swinging between positive and negative values). What parameter do I need to tune to address this issue?
+ When training a support vector machine, what value are you optimizing for?
+ Lasso regression uses the L1-norm of coefficients as a penalty term, while ridge regression uses the L2-norm. Which of these regularization methods is more likely to result in sparse solutions, where one or more coefficients are exactly zero?
+ When training a 10-layer neural net using backpropagation, I find that the weights for the top 3 layers are not changing at all! The next few layers (4-6) are changing, but very slowly. What’s going on and how do I fix this?
+ I’ve found some data about wheat-growing regions in Europe that includes annual rainfall (R, in inches), mean altitude (A, in meters) and wheat output (O, in kgs/km2). A rough analysis and some plots make me believe that output is related to the square of rainfall, and log of altitude: O = β0 + β1 × R2 + β2 × loge(A)
+ Can I fit the coefficients (β) in my model to the data using linear regression?

## Software Engineering and System Design
Sample Questions
+ You run an ecommerce website. When a user clicks on an item to open its details page, you would like to suggest 5 more items that the user may be interested in, based on item features as well as the user’s purchase history, and display them at the bottom of the page. What services and database tables would you need to support this behavior? Assuming they’re available, write a query or procedure to fetch the 5 items to suggest.
+ What data would you like to collect from an online video player (like YouTube) to measure user engagement and video popularity?
+ A very simple spam detection system works as follows: It processes one email at a time and counts the number of occurrences of each unique word in it (term frequency), and then it compares those counts with those of previously seen emails which have been marked as spam or not. In order to scale up this system to handle a large volume of email traffic, can you design a map-reduce scheme that can run on a cluster of computers?
+ You want to generate a live visualization of what portion of a webpage users are currently viewing and clicking, sort of like a heat map. What components/services/APIs do you need in place, on the client and server end, to enable this?


I bumped into this great [post][ref-2]. So let's go through all these wonderful interview questions!
### Modeling
+ What type of problem does the model try to solve?
+ Is it prone to over-fitting? If so – what can be done about this?
+ Does the model make any important assumptions about the data? When might these be unrealistic? How do we examine the data to test whether these assumptions are satisfied?
+ Does the model have convergence problems? Does it have a random component or will the same training data always generate the same model? How do we deal with random effects in training?
+ What types of data (numerical, categorical etc…) can the model handle?
+ Can the model handle missing data? What could we do if we find missing fields in our data?
How interpretable is the model?
+ What alternative models might we use for the same type of problem that this one attempts to solve, and how does it compare to those?
+ Can we update the model without retraining it from the beginning?
+ How fast is prediction compared to other models? How fast is training compared to other models?
+ Does the model have any meta-parameters and thus require tuning? How do we do this?
+ In training a neural network, you notice that the loss does not decrease in the few starting epochs. What could be the reason?
  - The learning rate is too low.
  - Regularizaton parameter is high.
  - Stuck at local minima. 

### ML Theory
+ What is deep learning and what are some of the main characteristics that distinguish it from traditional machine learning
  - ML algorthms are not very useful when working with high dimensional data.
  - The second major challenge is to tell the computer what are the features it should look for in predicting the outcome as well as to achieve better accuracy while doing so.
+ What is linear in a generalized linear model?
+ What is a probabilistic graphical model? What is the difference between Markov networks and Bayesian networks?
+ Give an example of an application of non-negative matrix factorization
+ On what type of ensemble technique is a random forest based? What particular limitation does it try to address?
+ What methods for dimensionality reduction do you know and how do they compare with each other?
+ What are some good ways for performing feature selection that do not involve exhaustive search?
+ How would you evaluate the quality of the clusters that are generated by a run of K-means?
+ What is supervised learning and unsupervised learning? 
+ What kind of problems can be solved by supervised learning or unsupervised learning?
+ Give some examples for supervised learning and unsupervised learning.
+ What are the benefits of mini-batch gradient descent?
  - This is more effective compared to stochastic gradient descent.
  - The generalization by finding the minima.
  - Mini-batches allow help to approximate the gradient of the entire training set which helps us to avoid local minima.
+ What are the steps for using a gradient descent algorithm?
  - Initialize random weight and bias.
  - Pass an input through the network and get values from the output layer.
  - Calculate the error between the actual value and the predicted value.
  - Go to each neuron which contributes to the error and then change its respective values to reduce the error.
  - Reiterate until you find the best weights of the network. 
+ What are the drawbacks of single-layer perceptron?
  - Single-layer perceptron cannot classify non-linearly separable data points
  - Complex problems, that involve a lot of parameters cannot be solved by single-layer perceptrons.
+ What is a multi-layer perceptron?
  - A MLP is a deep, artifical neural network. It is composed of more than one perceptron.
  - THey are composed of an input layer to receive the signal, an output layer that makes a decision or prediction about the input, and in between those two, an arbitrary number of hidden layers that are the true computational engine of the MLP. 
+ What is data normalization and why do we need it?
  - Data normalization is very important pre-processing step, used to rescale values to fit in a specific range to assure better convergence during backpropagation.
  - In general, it boils down to subtracting the mean of each data point and dividing by its standard deviation.  
+ Why is weight initialization important in neural networks?
  - Weight initialization is one of the very important steps. A bad weight initialization can prevent a network from learning but good weight initialization helps in giving a quicker convergence and a better overall error.
  - Biases can be generally initialized to zero. The rule for getting the weights is to be close to zero without being to small.

+ What are the hyperparameters?
  - They are the variables which determine the network structure and the variables which determine how the network is trained. Hyperparameters are set before training.
Examples include number of hidden units and the learning rate. 
+ Explain the different hyperparameters related to Networking and Training.
  - Number of Hidden Layers.
  - Network weight initialization.
  - Activation function.
  - Batch size.
  - Number of epochs.
  - Momentum.
  - Learning rate. 
+ What is dropout?
  - Dropout is a regularization technique to avoid overfitting thus increasing the generalizing power.
  - Generally, we should use a small dropout value of 20-50% of neurons. A dropout value too low has minimal effect and a value too high results in underlearning by the network.
+ What is a CNN?
  - CNN is a class of deep neural networks, most commonly applied to analyzing visual imagery.
  - Unlike neural networks, where the input is a vector, here the input is a multi-channeled image. CNNs use a variation of multilayer perceptrons designed to require minimum pre-processing.
+ Explain the different layers of CNN.
  - Convolution: The convolution layer comprises of a set of independent filters.
  - ReLU: This layer is used with the convolutional layer.
  - Pooling: Its function is to progressively reduce the spatial size of the representation to reduce the number of parameters and computation in the network.
  - Full Connectedness: Neurons in a fully connected layer have full connections to all activations in the previous layer.
+ What is an RNN?
  - RNN is a type of artificial neural network designed to recognize patterns in sequences of data, siuch as text, genomes, handwriting, the spoken word, numerical times series data.
  - RNN use backpropagation algorithm for training. Because of their internal memory, RNN's are able to remember important things about the input they received which enables them to be very precise in predicting what's coming next.
+ What is vanishing gradient?

+ What is exploding gradient decsent?
  - Exploding gradients are a problem when large error gradients accumulate and result in very large updates to neural network model weights during training.
  - GD works best when these updates are small and controlled.
  - When the magnitudes of the gradients accumulate, an unstable network is likely to occur, which can cause poor prediction of results or even a model that reports nothing useful what so ever.
+ Explain the importance of LSTM.
  - LSTM is an artificial RNN architecture used in the field of DL.
  - Unlike standard feedforward neural networks, LSTM has feedback connections that make it a "general purpose computer".
  - It can not only process single data points, but also entire sequences of data.
  - They are a special kind of RNN which are capable of learning long term dependencies.
### Tools and Research
+ Do you have any research experience in machine learning or a related field? Do you have any publications?
+ What tools and environments have you used to train and assess models?
+ Do you have experience with Spark ML or another platform for building machine learning models using very large datasets?
+ Name a few deep learning frameworks
  - TensorFlow, PyTorch, Caffe, Chainer, Keras, CNTK 
+ List a few advantages of TensorFlow
  - It has platform flexibility.
  - It is easily trainable on CPU as well as GPU for distributed computing.
  - TensorFlow has auto differentiation capabilities.
  - It has advanced support for threads, asynchronous computation.
  - It is customizable and open source. 


[ref-1]:https://blog.udacity.com/2016/05/prepare-machine-learning-interview.html
[ref-2]:https://resources.workable.com/machine-learning-engineer-interview-questions

Other resources:

[Machine Learning Interview Questions][ref-3]

[40 Interview Questions asked at Startups in Machine Learning/Data Science][ref-4]

[Columbia Data Science Society Interview Prep][ref-5]

[Deep Learning Interview Questions and Answers Edureka][ref-6]

[ref-3]:https://www.springboard.com/blog/machine-learning-interview-questions/
[ref-4]:https://www.analyticsvidhya.com/blog/2016/09/40-interview-questions-asked-at-startups-in-machine-learning-data-science/
[ref-5]:https://cdssatcu.com/interview-prep/
[ref-6]:https://www.youtube.com/watch?v=HGXlFG_Rz4E
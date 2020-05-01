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
+ How would you handle missing/corrupt data?
  - Data imputation: If data is missing, add a value.
  - Categorial: Add a new category "no clue"/"other"
  - Numerical: Impute a 0+ indicator variable to show value is missing
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
  - Deep learning is a form of machine learning that is inspired by the structure of the human brain and is particularly effective in the feature detection.
    - Enables machines to take decisions with the help of artificial neural networks.
    - Needs a large amount of training data.
    - Needs high end systems to work.
    - The machine learns the features from the data it is provided.
    - The problem is solved in an end-to-end manner.
  - Machine learning is about algorithms that parse data, learn from that data, and then apply what they've learned to make informed decisions.
    - Enables machines to take decisions on their own, based on past data.
    - Needs only a small amount of training data.
    - Works well on low-end systems.
    - Most features need to be identified in advance and manually closed.
    - The problem is divided into parts and solved individually and then combined.

+ What is linear in a generalized linear model?
+ What is bagging and boosting in machine learning?
  - Both are ensemble methods

+ What is selection bias?
  - Statistical error that causes a bias in the sampling portion of an experiment.
  - The error causes one  sampling group to be selected more often than other groups included in the experiment.
  - Selection bias may produce an inaccurate conclusion if the selection bias is not identified 
+ What is the difference between generative & discriminative models?
  - Discriminative models learn the decision boundary between classes
  - Generative models model the distribution of individual classes
+ What is a probabilistic graphical model? What is the difference between Markov networks and Bayesian networks?
+ What's one shortcoming of neural networks?  
  - Black Box
  - Duration of development
  - Amount of data
  - Computationally expensive
+ Explain the commonly used ANNs
  - Feedforward Neural Network
    - Simplest form of ANN, where the data or the input travels in one direction
    - The data passes through the input nodes and exit on the output nodes. This NN may or may not have the hidden layers
  - CNN
    - Input features are taken in batch wise. This will help the network to remember the images in parts and can compute the operations
    - signal and image processing
  - RNN
    - Works on the principle of saving the output of a layer and feeding this back to input
  - Autoencoders
    - The output layer has a same number of units
+ What are Bayesian Networks?
  - A Bayesin Network is a statistical model that represents a set of variables and their conditional dependencies in the form of a directed acrylic graph.
+ Explain the assessment that is used to test the intelligence of a machine.
  - In AI, a TT is a method of inquiry for determining whether or not a computer is capable of thinking like a human being.
+ How does RL work? Explain with an example?
  - The RL agent collects state S from the environment
  - Based on the state S, the RL agent takes an action A, initially the action is random.
  - The environment is now in a new state S1.
  - RL agent now gets a reward R from the environment.
  - The RL loop goes on until the RL agent is dead or reaches the destination.
+ What is exploitation and exploration trade off?  
  - Exploitation is about using the already known exploited information to heighten the rewards.
  - Exploration is about exploring and capturing more information about an environment.
+ What is the difference between parametric and non-parametric models?
  - Parametric model
    - It uses a fixed nunmber of parameters to build the model.
    - Considers strong assumptions about the data.
    - Computationally faster.
    - Requires less data.
    - Examples include logistic regression and naive bayes models.
  - Non-parametric model
    - It uses flexible number of parameters to build the model.
    - Considers fewer assumptions about the data.
    - Computationally slower.
    - Require more data.
    - Example KNN and decision tree.
+ Explain the difference algorithms used for hyperparameter optimization.
  - Grid search
    - Grid search trains the network for every combination by using the two set of hyperparameters, learning rate and number of layers. Then evaluates the model by using Cross Validation techniques.
    - Random search
      - It randomly samples the search space and evaluates sets from a particular probability distribution. For example, instead of checking all 10,000 samples, randomly selected 100 parameters can be checked.
    - Bayesian Optimization
      - This includes fine tuning the hyperparameters by enabling automated model tuning. The model used for approximating the objective function is called surrogate model(Gaussian Process). Bayesian optimization uses GP function to get posterior functions to make predictions based on prior functions.   
+ How can overfitting be fixed?
  - CV
  - More training data
  - Remove features
  - Early stopping
  - Regularization
  - Use Ensemble methods 
+ Give an example of an application of non-negative matrix factorization
+ On what type of ensemble technique is a random forest based? What particular limitation does it try to address?
  - Bagging
  - High variance
+ Both being tree-based algorithms, how is random forest different from gradient boosting algorithm?
  - random forest - bagging
  - gradient boosting algorithm - boosting
+ What methods for dimensionality reduction do you know and how do they compare with each other?
  - Linear
    - PCA: Continuous data. PCA rotates and projects data along the direction of increasing variance. The features with maximum variance are the prinicple components.
    - Factor Analysis: The values of observed data are expressed
    - LDA
  - Nonlinear
    - MDS
    - GDA
    - Isomap
  - Autoencoder
+ What are some good ways for performing feature selection that do not involve exhaustive search?
+ How would you evaluate the quality of the clusters that are generated by a run of K-means?
+ What is supervised learning and unsupervised learning? 
  - Supervised learning
    - Machine learning model learns from the past input data and makes future prediction as output
  - Unsupervised learning
    - Machine learning model was unlabeled input data and allows the algorithm to act on that information without guidance
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
+ What are capsules in CNN?
  - Capsules are a vector specifying the features of the object and its likelihood. These features can be any of the instantiatiion parameters like position, size, orientation, deformation, velocity, hue, texture and much more.
  - A capsule can specify its attributes like angle and size so that it can represent the same generic information. Now, just like a neural network has layers of neurons, a capsule network can have layers of capsules.
+ Explain autoencoders and its uses.
  - An autoencoder neural network is an unsupervised machine learning algorithm that applies backpropagation, setting the target values to be equal to the inputs.
  - Autoencoders are used to reduce the size of our inputs into a smaller representation.
  - If anyone needs the original data, they can reconstruct it from the compressed data.
+ In terms of Dimension Reduction, how does autoencoders differ from PCAs?
  - It is more efficient to learn several layers with an autoencoder rather than learn one huge transformation with PCA.
  - An auto encoder provides a representation of each layer as the output.
  - It can make use of pre-trained layers from another model to apply transfer learning to enhanve the encoder/decoder.         
+ Explain the architecture of an autoencoder.
  - Encoder: This part of the network compresses the input into a latent space representation.
  - Code: This part of the network represents the compressed input which is fed to the decoder.
  - Decoder: This layer decodes the encoded image back to the original dimension.

+ What is a bottleneck in autoencoder and why is it used?
  - The layer between the encoder and decoder, i.e. the code is also known as Bottleneck.
  - This is a well-designed approach to decide which aspects of observed data are relevant information and what aspects can be discarded.
+ Is there any variatoin of autoencoders?
  - Convolution
  - Sparse
  - Deep
  - Contractive 
+ What are deep autoencoders?
  - The first layer of the Deep Autoencoder is used for first-order features iin the raw input.

+ What is a restricted Boltzmann machine?
  - RBM is an undirected graphical model that plays a major role in DLF in recent times.
  - It is an algorithm which is useful for dimensionality reduction, classification, regression, collaborative filtering, feature learning, and topic modeling.
+ Advantages of KNN algorithm
  - Easy to understand and implement
  - Non-parametric: no need for assumptions to be made 
  - Almost no training time
  - Continuously self-evolving
  - Works well with both regression and classification problems
+ Disadvantages of KNN
  - Declining speed
  - Not effective with large number of input variables
  - Choose the optimal number of neighbors can be a problem
  - High probability of wrong classification if data inclines toward a class
  - Outlier may impact the performance
  - Model doesn't learn
  - Change k can impact outcome
+ What is Q-learning?
  - Q-learning is a reinforcement learning algorithm in which an agent tries to learn the  optimal policy from its past experiences with the environment. The past experiences of an agent are a sequence of state-action-rewards.

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
+ What are some limitations of deep learning?
  - Deep learning usually requires large amounts of training data.
  - Deep neutral networks are easily fooled.
  - Successes of deep learning are purely empirical, deep learning algorithms have been criticized as uninterpretable "black-boxes".
  - Deep learning thus far has not been well integrated with prior knowledge.


[ref-1]:https://blog.udacity.com/2016/05/prepare-machine-learning-interview.html
[ref-2]:https://resources.workable.com/machine-learning-engineer-interview-questions

Other resources:

[Machine Learning Interview Questions][ref-3]

[40 Interview Questions asked at Startups in Machine Learning/Data Science][ref-4]

[Columbia Data Science Society Interview Prep][ref-5]

[Deep Learning Interview Questions and Answers Edureka][ref-6]

[10 Machine Learning Interview Questions - ANSWERED][ref-7]

[Machine Learning Interview Questions and Answers CareerRide][ref-8]

[Machine Learning Interview Questions and Answers Eureka][ref-9]

[Artificial Intelligence Interview Questions and Answers][ref-10]

[Dimensionality Reduction for Machine Learning][ref-11]

[ref-3]:https://www.springboard.com/blog/machine-learning-interview-questions/
[ref-4]:https://www.analyticsvidhya.com/blog/2016/09/40-interview-questions-asked-at-startups-in-machine-learning-data-science/
[ref-5]:https://cdssatcu.com/interview-prep/
[ref-6]:https://www.youtube.com/watch?v=HGXlFG_Rz4E
[ref-7]:https://www.youtube.com/watch?v=T03Fw1kj3B8
[ref-8]:https://www.youtube.com/watch?v=-jOKqY9L1Z0
[ref-9]:https://www.youtube.com/watch?v=t6gOpFLt-Ks
[ref-10]:https://www.youtube.com/watch?v=D_xZjXoloxc
[ref-11]:https://towardsdatascience.com/dimensionality-reduction-for-machine-learning-80a46c2ebb7e
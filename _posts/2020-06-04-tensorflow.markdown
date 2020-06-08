---
layout: post
title:  "TensorFlow Summary"
ref: welcome
date:   2020-06-04
tags: courses
lang: en
---

Tensors are the building block in Tensorflow and identifies a multi-dimensional array.

## ML Basics

### Basic image classification
tf.keras is a high-level API to build and train models in TensorFlow

The basic building block of a neural network is the layer. Layers extract representations from the data fed into them. Hopefully, these representations are meaningful for the problem at hand.

Most of deep learning consists of chaining together simple layers. Most layers, such as tf.keras.layers.Dense, have parameters that are learned during training.


### Text classification with TF Hub
The neural network is created by stacking layers—this requires two main architectural decisions:
- How to represent the text?
- How many layers to use in the model?
- How many hidden units to use for each layer?
One way to represent the text is to convert sentences into embeddings vectors. We can use a pre-trained text embedding as the first layer, which will have three advantages:

- we don't have to worry about text preprocessing,
- we can benefit from transfer learning,
- the embedding has a fixed size, so it's simpler to process.

A model needs a loss function and an optimizer for training. Since this is a binary classification problem and the model outputs logits (a single-unit layer with a linear activation), we'll use the binary_crossentropy loss function.

This isn't the only choice for a loss function, you could, for instance, choose mean_squared_error. But, generally, binary_crossentropy is better for dealing with probabilities—it measures the "distance" between probability distributions, or in our case, between the ground-truth distribution and the predictions.

### Text classification with preprocessed text
Training loss decreases with each epoch and the training accuracy increases with each epoch. This is expected when using a gradient descent optimization—it should minimize the desired quantity on every iteration.

This isn't the case for the validation loss and accuracy—they seem to peak after about twenty epochs. This is an example of overfitting: the model performs better on the training data than it does on data it has never seen before. After this point, the model over-optimizes and learns representations specific to the training data that do not generalize to test data.

### Regression
- Mean Squared Error (MSE) is a common loss function used for regression problems (different loss functions are used for classification problems).
- Similarly, evaluation metrics used for regression differ from classification. A common regression metric is Mean Absolute Error (MAE).
- When numeric input data features have values with different ranges, each feature should be scaled independently to the same range.
- If there is not much training data, one technique is to prefer a small network with few hidden layers to avoid overfitting.
- Early stopping is a useful technique to prevent overfitting.

### Overfit and underfit
To recap: here are the most common ways to prevent overfitting in neural networks:

- Get more training data.
- Reduce the capacity of the network.
- Add weight regularization.
- Add dropout.
Two important approaches not covered in this guide are:

- data-augmentation
- batch normalization
Remember that each method can help on its own, but often combining them can be even more effective.

### Save and load
You can use a trained model without having to retrain it, or pick-up training where you left off—in case the training process was interrupted. The tf.keras.callbacks.ModelCheckpoint callback allows to continually save the model both during and at the end of training.

Checkpoints contain:

- One or more shards that contain your model's weights.
- An index file that indicates which weights are stored in a which shard.

Call model.save to save a model's architecture, weights, and training configuration in a single file/folder. This allows you to export a model so it can be used without access to the original Python code*. Since the optimizer-state is recovered, you can resume training from exactly where you left off.

Entire model can be saved in two different file formats (SavedModel and HDF5). It is to be noted that TensorFlow SavedModel format is the default file format in TF2.x. However, model can be saved in HDF5 format. More details on saving entire model in the two file formats is described below.

To save custom objects to HDF5, you must do the following:

- Define a get_config method in your object, and optionally a from_config classmethod.
get_config(self) returns a JSON-serializable dictionary of parameters needed to recreate the object.
from_config(cls, config) uses the returned config from get_config to create a new object. By default, this function will use the config as initialization kwargs (return cls(**config)).
- Pass the object to the custom_objects argument when loading the model. The argument must be a dictionary mapping the string class name to the Python class. E.g. tf.keras.models.load_model(path, custom_objects={'CustomLayer': CustomLayer})

### Tune hyperparameters with the Keras Tuner
Hyperparameters are of two types:

- Model hyperparameters which influence model selection such as the number and width of hidden layers
- Algorithm hyperparameters which influence the speed and quality of the learning algorithm such as the learning rate for Stochastic Gradient Descent (SGD) and the number of nearest neighbors for a k Nearest Neighbors (KNN) classifier

## Load and preprocess data
### CSV
We can load csv files using pandas, and pass the NumPy arrays to TensorFlow. If you need to scale up to a large set of files, or need a loader that integrates with TensorFlow and tf.data then use the tf.data.experimental.make_csv_dataset function:

The only column you need to identify explicitly is the one with the value that the model is intended to predict.
Continuous data should always be normalized.
Mean based normalization requires knowing the means of each column ahead of time.
### NumPy
We can load NumPy arrays with tf.data.Dataset.
Assuming we have an array of examples and a corresponding array of labels, pass the two arrays as a tuple into tf.data.Dataset.from_tensor_slices to create a tf.data.Dataset.
### pandas.DataFrame
The easiest way to preserve the column structure of a pd.DataFrame when used with tf.data is to convert the pd.DataFrame to a dict, and slice that dictionary.
### Images
To train a model with this dataset you will want the data:

- To be well shuffled.
- To be batched.
- Batches to be available as soon as possible.
These features can be easily added using the tf.data api.
### Text
Before being passed into the model, the datasets need to be batched. Typically, the examples inside of a batch need to be the same size and shape. But, the examples in these datasets are not all the same size — each line of text had a different number of words. So use tf.data.Dataset.padded_batch (instead of batch) to pad the examples to the same size.


### Unicode
There are two standard ways to represent a Unicode string in TensorFlow:

- string scalar — where the sequence of code points is encoded using a known character encoding.
- int32 vector — where each position contains a single code point.
### TF.Text
TensorFlow Text provides a collection of text related classes and ops ready to use with TensorFlow 2.0. The library can perform the preprocessing regularly required by text-based models, and includes other features useful for sequence modeling not provided by core TensorFlow.

The benefit of using these ops in your text preprocessing is that they are done in the TensorFlow graph. You do not need to worry about tokenization in training being different than the tokenization at inference, or managing preprocessing scripts.
### TFRecord and tf.Example
The TFRecord format is a simple format for storing a sequence of binary records.

Protocol buffers are a cross-platform, cross-language library for efficient serialization of structured data.

Protocol messages are defined by .proto files, these are often the easiest way to understand a message type.

The tf.Example message (or protobuf) is a flexible message type that represents a {"string": value} mapping. It is designed for use with TensorFlow and is used throughout the higher-level APIs such as TFX.
## Estimator 

### Premade estimator
You must create input functions to supply data for training, evaluating, and prediction.

An input function is a function that returns a tf.data.Dataset object which outputs the following two-element tuple:

- features - A Python dictionary in which:
    - Each key is the name of a feature.
    - Each value is an array containing all of that feature's values.
- label - An array containing the values of the label for every example.
### Linear model
The receiver operating characteristic (ROC) of the results will give us a better idea of the tradeoff between the true positive rate and false positive rate.
### Boosted trees
Boosted Trees models are among the most popular and effective machine learning approaches for both regression and classification. It is an ensemble technique that combines the predictions from several (think 10s, 100s or even 1000s) tree models.

Boosted Trees models are popular with many machine learning practitioners as they can achieve impressive performance with minimal hyperparameter tuning.
### Boosted trees model understanding
Local interpretability refers to an understanding of a model’s predictions at the individual example level, while global interpretability refers to an understanding of the model as a whole. Such techniques can help machine learning (ML) practitioners detect bias and bugs during the model development stage.

For local interpretability, you will learn how to create and visualize per-instance contributions. To distinguish this from feature importances, we refer to these values as directional feature contributions (DFCs).

For global interpretability you will retrieve and visualize gain-based feature importances, permutation feature importances and also show aggregated DFCs.
### Keras model to Estimator
In Keras, you assemble layers to build models. A model is (usually) a graph of layers. The most common type of model is a stack of layers: the tf.keras.Sequential model.

## Customization
### Tensors and operations
Many TensorFlow operations are accelerated using the GPU for computation. Without any annotations, TensorFlow automatically decides whether to use the GPU or CPU for an operation—copying the tensor between CPU and GPU memory, if necessary. 
### Custom layers
The best way to implement your own layer is extending the tf.keras.Layer class and implementing:

- __init__ , where you can do all input-independent initialization
- build, where you know the shapes of the input tensors and can do the rest of the initialization
- call, where you do the forward computation
### Custom training
Computations using tf.Variable are automatically traced when computing gradients. For variables that represent embeddings, TensorFlow will do sparse updates by default, which are more computation and memory efficient.
### Custom training: walkthrough

## Distributed training

### Distributed training with Keras
We still train the model in the usual way, calling fit on the model and passing in the dataset created at the beginning of the tutorial. This step is the same whether you are distributing the training or not.
### Custom training loops
Alternate ways of iterating over a dataset
Using iterators
If you want to iterate over a given number of steps and not through the entire dataset you can create an iterator using the iter call and explicity call next on the iterator. You can choose to iterate over the dataset both inside and outside the tf.function. Here is a small snippet demonstrating iteration of the dataset outside the tf.function using an iterator.
### Multi-worker training with Keras
### Multi-worker training with Estimator
###s Save and load

## Images
### Convolutional Neural Network
The output of every Conv2D and MaxPooling2D layer is a 3D tensor of shape (height, width, channels). The width and height dimensions tend to shrink as you go deeper in the network. The number of output channels for each Conv2D layer is controlled by the first argument (e.g., 32 or 64). Typically, as the width and height shrink, you can afford (computationally) to add more output channels in each Conv2D layer.
### Image classification
Overfitting generally occurs when there are a small number of training examples. One way to fix this problem is to augment the dataset so that it has a sufficient number of training examples. Data augmentation takes the approach of generating more training data from existing training samples by augmenting the samples using random transformations that yield believable-looking images. The goal is the model will never see the exact same picture twice during training. This helps expose the model to more aspects of the data and generalize better.

Implement this in tf.keras using the ImageDataGenerator class. Pass different transformations to the dataset and it will take care of applying it during the training process.
### Transfer learning with TF Hub
Using TF Hub it is simple to retrain the top layer of the model to recognize the classes in our dataset.
### Transfer learning with pretrained CNN
Two ways to customize a pretrained model:

- Feature Extraction: Use the representations learned by a previous network to extract meaningful features from new samples. You simply add a new classifier, which will be trained from scratch, on top of the pretrained model so that you can repurpose the feature maps learned previously for the dataset.

You do not need to (re)train the entire model. The base convolutional network already contains features that are generically useful for classifying pictures. However, the final, classification part of the pretrained model is specific to the original classification task, and subsequently specific to the set of classes on which the model was trained.

- Fine-Tuning: Unfreeze a few of the top layers of a frozen model base and jointly train both the newly-added classifier layers and the last layers of the base model. This allows us to "fine-tune" the higher-order feature representations in the base model in order to make them more relevant for the specific task.
### Data Augmentation

### Image Segmentation

## Text
### Word embeddings
Word embeddings give us a way to use an efficient, dense representation in which similar words have a similar encoding. Importantly, we do not have to specify this encoding by hand. An embedding is a dense vector of floating point values (the length of the vector is a parameter you specify). Instead of specifying the values for the embedding manually, they are trainable parameters (weights learned by the model during training, in the same way a model learns weights for a dense layer). It is common to see word embeddings that are 8-dimensional (for small datasets), up to 1024-dimensions when working with large datasets. A higher dimensional embedding can capture fine-grained relationships between words, but takes more data to learn.


### Text classification with an RNN
### Text generation with an RNN
### Neural machine translation with attention
### Image Captioning
### Transformer model for language understanding

## Structured data
### Classify structured data with feature columns
### Classification on imbalanced data
### Time series forcasting

## Generative
### Neural style transfer
NNT is implemented by optimizing the output image to match the content statistics of the content image and the style statistics of the style reference image. These statistics are extracted from the images using a convolutional network.
### DeepDream
### DCGAN
### Pix2Pix
### CycleGAN
### Adversarial FGSM
### Variational Autoencoder 
Unlike a traditional autoencoder, which maps the input onto a latent vector, a VAE maps the input data into the parameters of a probability distribution, such as the mean and variance of a Gaussian. This approach produces a continuous, structured latent space, which is useful for image generation.
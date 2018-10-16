# An Introduction to Convolutional Neural Networks

This is the implementation of [this](https://arxiv.org/pdf/1511.08458.pdf) research paper on Introduction to Convolution Neural Network by Keiron O’Shea and Ryan Nash.



## Artificial Neural Network(ANN)
ANNs are processing units which was inspired from the biological neural system of human brain. ANNs consists of a large number of interconnected computation units which works collectively to learn from the imput data to optimise the output.
![](https://cdn-images-1.medium.com/max/824/1*eBMwpBBboAXgqsawwOKkPw.png)

We load the input, a multidimensional vector to the input layer of the Neural Network, which will be distributed to the hidden layers.The hidden layer will make decision from previous layers and see how a change in characteristic of the node will will improve the output, this is called learning. (adapting itself by getting the input and trying to decide the output with generalization).


## Convolutional Neural Network(CNNs)
CNNs are mostly used in the field of pattern recognition within images.This helps to encode image-specific features, making the network more suited for image focused tasks.<br>

Traditional ANNs can still be used for image base tasks, but one of the problem is the computation complexity requirement in ANNs for images.<br>
A basic MNIST dataset has 28x28 images, so the first imput layer itself should have 28x28x1 = 784 weights.
Just think about a colour image which whose size is 3461 x 2266, that wll be 3661x2266x3 = 24,887,478 parameters in the first input layer.
And for the network to learn the image patters for the specific output , it will need more layers that just a single input layer.
<br><br>
If in ideal case , you have unlimited computation power to use any ANN of any size, there also comes a problem of [overfitting](https://en.wikipedia.org/wiki/Overfitting). More if the layers and nodes, more better will you network work on the training set, but gives poor performance on test set, due to overfitting. 
<br><br>
So, we need a model which is computationaly inexpensive and gives us good accuracy on both training and testing set.

## CNN Archintecture
![](https://s3.amazonaws.com/cdn.ayasdi.com/wp-content/uploads/2018/06/21100605/Fig2GCNN1.png)

CNN comprises of 3 layers. 
1. Convolution Layer
2. Polling Layer
3. Fully-Connected Layer

Convolution layer will determine the output of neurons of which are connected to local regions of the input through the calculation of the scalar product between their weights and the region connected to the input volume. The rectified linear unit (commonly shortened to ReLu) aims to apply an ’elementwise’ activation function such as sigmoid to the output of the
activation produced by the previous layer.

The pooling layer will then simply perform downsampling along the spatial dimensionality of the given input, further reducing the number of parameters within that activation

The fully-connected layers will then perform the same duties found in standard ANNs and attempt to produce class scores from the activations, to be used for classification. It is also suggested that ReLu may be used between these layers, as to improve performance.

![](https://www.researchgate.net/profile/Holger_Roth/publication/264160750/figure/fig3/AS:296012620025856@1447586316051/The-proposed-convolution-neural-network-consists-of-two-convolutional-layers-max-pooling.png)

## Implementation of Convolutional Neural Network

I will implement the convolutional neural network froms cratch using only basic libraries like numpy(for computational functions), matplotlib(for visualization).<br>
Although CNNs can now be implemented very easily and effectively using packahes like Keras, Tensorflow, Pytorch..etc.

### Convolution layer

Convolution is a mathematical operation.
In mathematics (and, in particular, functional analysis) convolution is a mathematical operation on two functions (f and g) to produce a third function that expresses how the shape of one is modified by the other.--WIKI

### Pooling Layer
![](https://cdn-images-1.medium.com/max/1200/1*q0lk6B6gzvsSQSDn-20zJA.png)

### Fully connected layer

Fully connected layer is same as ANNs. we take the pooled box of values and make it into a single layer of NN.

![](http://www.jpathinformatics.org/articles/2017/8/1/images/JPatholInform_2017_8_1_1_201108_f3.jpg)

Then continue adding new layers of fully connected layer is neeeded , else use the activation to predict the output.


### The final Model

The model will look like
<pre>CONV-->POOL-->CONV--->POOL..........-->CONV-->POOL-->FNN-->ACTIVATION-->PREDICTION</pre>
CONV- Convolution layer
POOL - Pooling Layer
FNN - Fully Connected layer


Image source : Google Images

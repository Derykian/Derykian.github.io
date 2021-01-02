[comment]: something

### About this site

This page was created as a concept showcase and design report for AntsNet, a visual ant tracking and identifying AI algorithm. It will outline the general workings of neural networks, with a focus on convolutional neural networks and transfer learning, the areas most relevant to AntsNet. This is an ongoing research project and this site will be updated periodically with new information and insights as development progresses.

### Project summary

AntsNet is a convolutional neural network-based deep learning algorithm designed to detect and 'box' ants from images, and identify them by genus. This project is a culmination of my interests in computer algorithms and ant behavior, and the end product serves to contribute to the ant-keeping community as well as provide an application for my newly developed skills in neural network programming. The network utilizes transfer learning, using pre-trained Inception, ResNet, and VGG-16 models as its base networks during development for performance comparison purposes. The final form of AntsNet will be open-sourced and publicly available, and I will be working to optimize the algorithm for use on hardware like Jetson or Raspberry Pi.

### The General Neural Network

The simplistic description of a standard neural network employs layers of nodes as the data structures. The values of the nodes in the input layer represent distinct independent variables, and are fully connected to the first network layer, meaning each input node makes a connection to every first-layer node. These connections hold weights. The values from one layer are multiplied by weights before storage in the following layer's nodes, and so on until the output layer. The dimensions of the output layer vary by application, from one element in a binary classifier to as many as there are classes that a multiclass network is trained to identify.

*picture here*

The true architecture of neural networks makes heavy use of matrices. Each layer is a column vector variable. Each layer vector is multiplied by a weight matrix and added to a bias vector of the same dimensions such that the matrix operations are legal. In order to increase the network's capacity, the resultant vector is run through an 'activation' function, which delinearizes the network and prevents the layers from collapsing to a linear function.

*picture here*

### How Neural Networks Learn

While training a neural network, each input is fed through the layers of the network. In each layer its values are multiplied by the weights and delinearized by an activation function, until an output is reached at the end of the network. This output, or predicted value, is compared to the input's label, the target value. A loss is calculated using the difference between the predicted value and the target value. Two common loss functions are Mean Squared Error and Cross-Entropy loss. Mean Squared Error is used to calculate the loss in regression models which have continuous, real-valued outputs. Cross-Entropy is used in categorical models. Both of these functions are differentiable, which is important for backpropagation, which relies on calculating the gradient of the loss function. Updates to the values of the network weights in each layer are determined by working backward from the output through the weight matrices and bias vectors, using the chain rule of calculus and the loss function gradient. With this algorithm, weight matrices and bias vectors can be systematically incremented toward the direction minimizing the network's loss, or error.

*picture here*

### Convolutional Neural Networks

Simple fully-connected deep neural networks require the data to be input as a vector. Visual data, such as a digital photograph, must be flattened into a vector for this case. The problem is that this disrupts spatial relationships within the image, so regular deep neural networks used in this application have had mediocre performance. Convolutional neural networks make use of 'convolutional' layers, which convolve a filter with the input image or feature map, which are of two or more dimensions and preserve spatial relationships.

Convolutional neural networks are usually structured as follows:

- Input
- Convolutional layer (small filters)
- Pooling layer
- Convolutional layer (larger filters)
- Pooling layer  
⁝
- Flatten
- Multiple fully connected layers
- Output

*picture here*

Prior to being input to the network the dataset images are preprocessed, which involves downscaling their dimensions to match the input of the network, commonly to 224x224 pixels, and normalizing their pixel values to between 0 and 1. Downscaling heavily reduces the required resources during training, with little impact to training performance. Normalization is required to avoid exploding and vanishing gradients, caused by repeated operations with very large or tiny weights.

For applications such as identifying ants from color images, the network is fed an input with 3 color channels, each a matrix of pixel color values usually of dimensions 224x224.

The input data with a shape of 224x224 is fed into the first convolutional layer. *filters, feature mapping, stride, same and valid, activation,...*

### Transfer Learning

Currently in machine learning, an abundance of training data is key to good results. However, the volume of data required is often not available for every application, or to every machine learning developer. One way to remedy this is to use a different network pre-trained on a different dataset, as the base of the model for your new task, and this is Transfer Learning. Transfer learning is used when high network capacity is needed, but limited training data is available. The base networks are usually chosen such that their training data share a similar featureset to the new application. It is common practice to start by retraining only the classification section of the model, keeping the feature detection portion intact. In image processing this means keeping the convolutional layers and retraining the fully-connected "top" of the network.
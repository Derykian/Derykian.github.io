[comment]: hi

### About this site

This page was created as a concept showcase and design report for AntsNet, a visual ant tracking and identifying AI algorithm. It will outline the general workings of neural networks, with a focus on convolutional neural networks and transfer learning, the areas most relevant to AntsNet. This is an ongoing research project and this site will be updated periodically with new information and insights as development progresses.

### Project summary

AntsNet is a convolutional neural network-based deep learning algorithm designed to detect and 'box' ants from images, and identify them by genus. This project is a culmination of my interests in computer algorithms and ant behavior, and the end product serves to contribute to the ant-keeping community as well as provide an application for my newly developed skills in neural network programming. The network utilizes transfer learning, using pre-trained Inception, ResNet, and VGG-16 models as its base networks during development for performance comparison purposes. The final form of AntsNet will be open-sourced and publicly available, and I will be working to optimize the algorithm for use on hardware like Jetson or Raspberry Pi.

### The General Neural Network

The simplistic description of a standard neural network employs layers of nodes as the data structures. The values of the nodes in the input layer represent distinct independent variables, and are fully connected to the first network layer, meaning each input node makes a connection to every first-layer node. These connections hold weights. The values from one layer are multiplied by weights before storage in the following layer's nodes, and so on until the output layer. The dimensions of the output layer vary by application, from one element in a binary classifier to as many as there are classes the network is trained to identify.

*picture here*

The true architecture of neural networks makes heavy use of matrices. Each layer is a column vector variable. Each layer vector is multiplied by a weight matrix and added to a bias vector of the same dimensions such that the matrix operations are legal. In order to increase the network's capacity, the resultant vector is run through an 'activation' function, which delinearizes the network and prevents the layers from collapsing to a linear function.

*picture here*

### Convolutional Neural Networks

Simple fully-connected deep neural networks require the data to be input as a vector. Visual data, such as a digital photograph, must be flattened into a vector for this case. The issue is that this disrupts spatial relationships within the image, and therefore regular deep neural networks used in this application have had mediocre performance. Convolutional neural networks make use of 'convolutional' layers, which convolve a filter with the input image or feature map, which are of two or more dimensions and preserve spatial relationships.

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

For applications such as identifying ants from colored photos, the network is fed an input with 3 color channels, each a matrix of pixel color values usually of dimensions _.

Prior to being input to the network, the dataset images are preprocessed, which involves downscaling their dimensions and normalizing pixel values. Downscaling heavily reduces required system resources during training, with little impact to training performance. Normalization is required to mitigate exploding and vanishing gradients, caused by repeated operations with very large or tiny weights.


The input data with a shape of _ is fed into the first convolutional layer. *filters, feature mapping, stride, same and valid, activation,...*

*pooling layer*

*convolutional and pooling layers are typically repeated with different dimensions _*

*the parts covered thus far make up the **feature learning** section of the network. next comes the **classification** section—*
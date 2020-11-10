[comment]: hi

### About this site

This page was created as a concept showcase and design report for AntsNet, an visual ant tracking and identifying AI algorithm.

### Project Summary

AntsNet is a culmination of my interests in ants and algorithms. The goal is to create a binary classifier to distinguish ants from other items, then an ant genus classifier. The final model will combine all of this into a video feed-capable YOLO network.

### The General Neural Network

The simplistic description of a standard neural network employs layers of nodes as the data structures. The values of the nodes in the input layer represent distinct independant variables, and are fully connected to the first network layer, meaning each input node makes a connection to every first-layer node. These connections hold weights. The values from one layer are multiplied by weights before storage in the following layer's nodes, and so on.

*picture here*

The exact architecture of neural networks uses matrices. Each layer is a column vector variable. Each layer vector is multiplied by a weight matrix and added to a bias vector of the same dimensions such that the matrix operations are valid. In order to increase the network's capacity, the resultant vector is run through an 'activation' function, which delinearizes the layers and stops them from becoming a collapsible linear combination.

*picture here*

### Convolutional Neural Networks

Simple fully-connected deep neural networks require the data to be input as a vector. Visual data, such as a digital photograph, must be flattened into a vector for this case. The issue is that this disrupts spatial relationships within the image, and therefore regular deep neural networks used in this application have had mediocre performance. Convolutional neural networks make use of 'convolutional' layers, which convolve a filter with the input image or feature-map, which are 2-dimensional (sometimes with additional separate color channels) and preserve spatial relationships.

Convolutional neural networks are usually structured as follows:

- Input
- Convolutional layer (small filters)
- Pooling layer
- Convolutional layer (larger filters)
- Pooling layer
- Flatten
- Multiple fully connected layers
- Output

*picture here*

For applications such as identifying ants from colored photos like in AntsNet, the CNN is fed an input with 3 color channels, each a matrix of values representing how much of the respective color is within a pixel. The image data had undergone preprocessing, which involved augmentation (link to generalization), downscaling to _ x _, and normalizing its pixel values to between 0 and 1 (The reason why is explained further in _).

The input data with a shape of _ is fed into the first convolutional layer. *filters, feature mapping, stride, same and valid, activation,...*

*pooling layer*

*convolutional and pooling layers are typically repeated with different dimensions _*

*the parts covered thus far make up the **feature learning** section of the network. here on comes the **classification** part-*
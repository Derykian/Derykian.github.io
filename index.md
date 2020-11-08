[comment]: <You can use the [editor on GitHub](https://github.com/Derykian/NN-concepts-showcase/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.>

[comment]: <Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.>

### About this site

This page was created as a concept showcase and design report for AntsNet, an visual ant tracking and identifying AI algorithm.

### Project Summary

AntsNet is a culmination of my interests in ants and algorithms. The goal is to create a binary classifier to distinguish ants from other items, then an ant genus classifier. The final model will combine all of this into a video feed-capable YOLO network.

### The General Neural Network

The simplistic description of a standard neural network employs layers of nodes as the data structures. The values of the nodes in the input layer represent distinct independant variables, and are fully connected to the first network layer, meaning each input node makes a connection to every first-layer node. These connections hold weights. The values from one layer are multiplied by weights before storage in the following layer's nodes, and so on.

picture here

The exact architecture of neural networks uses matrices. Each layer is a column vector variable. Each layer vector is multiplied by a weight matrix and added to a bias vector of the same dimensions such that the matrix operations are valid. In order to increase the network's capacity, the resultant vector is run through an 'activation' function, which delinearizes the layers and stops them from becoming a collapsible linear combination.

picture here

### Convolutional Neural Networks

Simple fully-connected deep neural networks require the data to be input as a vector. Visual data, such as a digital photograph, must be flattened into a vector for this case. The issue is that this disrupts spatial relationships within the image, and therefore regular deep neural networks used in this application have had mediocre performance. Convolutional neural networks make use of 'convolutional' layers, which convolve a filter with the input image or feature-map, which are 2-dimensional (sometimes with additional separate color channels) and preserves spacial relationships.

Convolutional neural networks are usually laid out as follows:

- Feature learning
  - an input image of dimensions _ x _ with color depth of 3, that has been augmented, downscaled, and normalized during data preprocessing
  - a convolutional layer with a filter size of 3x3, stride of 1, ReLU activation
  - 2x2 pooling layer
  - convolutional layer
  - pooling layer
- Classification
  - Fully connected layer
  - Fully connected...

-simplify list and move details down here-
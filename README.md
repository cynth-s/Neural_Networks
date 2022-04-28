# ECS659U/P Coursework

# The problem :
1) Fashion-MNIST classification 
2) Classify every image in terms of 1 out of 10 classes 
3) Standard tasks for lectures and labs
4) Build a model on training set and evaluate on test 
<img src='images/fashion_mnist.jpg'>

# Overview of model
1) An architecture to process images based on MLPs.
2) Model architecture consists of Stem, backbone, classifier 

<img src ='images/overview.jpg'>

# The Stem
1) Takes as input an image <i>I</i> of size <i>H x W</i> and divides into N<sub>p</sub> non-overlapping patches.
2) Each patch P<sub>i,j</sub> has <i>K x K</i> dimensions.
3) Each patch is vectorized, then transformed to a feature vector of dimesions <i>d: x<sub>i,j</sub> = f(p<sub>i,j</sub>)</i>
4) <i>f</i> can be a single layer or a single hidden layer MLP.
5) All features are stored in a matrix <i> X belongs R <sup>N<sub>p</sub>Xd</sup></i>

<img src ='images/stem.jpg'>
  
# The Backbone
1) Consists of <i>N</i> blocks. The basic implementation for each block B<sub>i</sub> consists of two MLPs.
2) The first MLP is: O<sub>1</sub> = g(X <sup>T</sup>W<sub>1</sub>)W<sub>2</sub>, where g is a non-linear activation function.
3) Next Step is O<sub>1</sub> <- O<sup>T</sup><sub>1</sub>
4) The second MLP is : O<sub>2</sub> = g(O<sub>1</sub>W<sub>3</sub>)W<sub>4</sub>

<img src ='images/backbone.jpg'>

# The Classifier
1) Takes as input the output O<sub>2</sub> belongs to R <sup>N<sub>p</sub>Xd<sub>0</sub></sup></i> of the last block <i>B<sub>N</sub></i>
2) Then, it computes a mean feature <i>x belongs to R <sup>d<sub>0</sub></sup></i>
3) Finally, it feeds this feature to a classifier, can be softmax regression classifier.

<img src ='images/classifier.jpg'>








### Tuesday Week 3 Responses

https://www.tensorflow.org/tutorials/customization/custom_training_walkthrough

Using the Custom training: walkthrough 
script we developed during today's class, write a 1-1/2 to 2-page 
report that provides a description of the following.

    the data used in the model
    how you created the tf.dataset
    how you specified your model architecture, including the input shape, the layers and other functions
    how you trained the model
    how you optimized the model
    how you estimated loss including a plot that describes that change per epoch
    how you evaluated the model with your test dataset
    how you made some predictions, including three new ones of your own and their results

dataset: 
https://archive.ics.uci.edu/ml/datasets/iris
https://www.tensorflow.org/datasets/catalog/iris

The dataset used in this script is the "iris" dataset from TensorFlow, or rather from the Machine Learning Repository
of UCI.  It is a classification problems, with three classes forming the target variable "species".
There are 120 classes or types of iris flowers in the world, but only three classes are chosen to be included in this dataset
-- setosa, virginica, versicolor.  Each class contains 50 instances.  The 4 input features include: 
sepal length in cm, sepal width in cm, petal length in cm, and petal width in cm.  The target variable is the "label", while the input features
are "features".



more info and sources on tf.data (data input pipelines): 
https://www.tensorflow.org/guide/data
https://www.tensorflow.org/api_docs/python/tf/data/Dataset

tf.data.Dataset is a high-level API for writing descriptive and efficient input pipelines.  
There are three steps to it:

    - 1. create a source dataset from input data
    - 2. preprocess data: apply dataset transformation
    - 3. iterate over the dataset and process the elements
For the "iris" dataset, the first two steps are covered by the method used here ".experimental.make_csv_dataset", 
which reads the CSV-formatted dataset in.  This function returns a tf.data.Dataset of (features, label) pairs.  
The third step of iteration over dataset is covered by the line of code "features, labels = next(iter(train_dataset))".


(check section "Select the type of model")
The model for this iris classification problem seeks to define a relationship between the features (sepal and petal lengths and widths)
and the target (iris class prediction).  A *dense, fully-connected* neural network is used here, meaning each neuron in 
one layer receives input connections from every neuron in the layer before it.  There are three components to this type of 
neural network -- input layer, hidden layers, and output layer.
The neural network used for this dataset has 4 layers, with an input and output layer in addition to 2 hidden layers.  
The 2 hidden layers have 10 nodes each.  The output layer has 3 nodes, because there are only 3 classes of iris.  The first hidden
layer has an argument "input_shape", which represents the number of input features.  The activiation function is another argument
in both hidden layers, representing the output shape of nodes.  ReLU is the activation function here, meaning that if input is zero or less, the output will be zero; 
otherwise, output is equalivalent to value of input.  
Function "softmax()" is used to convert the predictions in logits to probabilities of of each prediction being either one of the three classes of iris.
Method "argmax()" used here gives you the labels of iris with the highest predicted probability.

(check section "Train the Model")
Training model is comprised of 6 steps:
- iteration of epochs
- for each epoch, iterate over each instance/example (features, labels) in train_dataset
- calculate loss and gradients of the model by calculating inaccuracy of predictions
- optimize the model
- track progress
    - loss and accuracy data
- repeat above steps for each epoch

loss and gradient function in addition to optimizer are important components the training process.
Loss represents how inaccurate are the predictions from actual labels using our model.  The goal is to minimize loss, which is 
"optimization".  The loss metrics used is SparseCategoricalCrossentropy, which computes the average of losses of examples from predictions
of iris class probability and corresponding actual label.  The self-defined function 'grad( )' that incorporates "tf.GradientTape" calculate gradients.
To optimize model, we want to minimize loss meaning go in the opposite direction of gradient.
The optimizer metrics used here is Stochastic Gradient Descent (SGD).  "Learning rate" is a hyperparameter of SGD representing
step size for each iteration finding new lower loss values.

[loss v. epoch plot](tue3_images.md)

(check section "Evaluate the model's effectiveness: setup the test dataset)
To evaluate the model using test_dataset, I imported a new dataset from outside that the model has never seen or trained on.
Then, I input this new dataset into the trained model and used the metrics "Accuracy" to calculate the percentage accuracy of the model predicting
on this test data set.

(check section "Evaluate the model's effectiveness: evaluate the model on the test dataset)
To make my own predictions using the model, I first convert the 3 lists/arrays of numbers -- each array representing the input features -- to a tensor
using "tf.convert_to_tensor".  Then I feed this convereted dataset into the model.  
Check here for the results: [predictions results](tue3_images.md)















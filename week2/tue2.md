dataset info: https://archive.ics.uci.edu/ml/datasets/HIGGS

### Informal Responses Tuesday 7/13/2021

#### Higgs Dataset questions

Describe the dataset. What type of variable is the target? 
How many features are being used? How many observations are in the training dataset?
How many are used in the validation set?
- The HIGGS Data Set is a classification problem 
    - to distinguish between a signal process vs. background process
        - signal process: produces Higgs bosons
        - background process: not produce Higgs bosons
- target variable type: categorical 
    - class label (1 for signal, 0 for background)
- 28 features
    - last 7 features are functions of first 21
- number of observations = number of instances = 11000000
- (first) 1000 samples for validation

How did each of the four models perform (tiny, small, medium and large)? 
Which of the four models performed the best? 
Which ones performed the worst? Why in your estimation did certain models perform better? 
Produce a plot that illustrates and compares all four models.
- the large and medium models performed the worst (clearly overfitting), while tiny and small performed better.
- simpler model the better, and complexity leads often not to better generalization to testing data
but to overfitting.  When the model becomes more complex (more layers and more neurons), it learns to predict
  the Training data better than less complex models.  But this could lead to it perform worst at predicting data it has
  never seen before and are different from training data.
 - [comparison of all four models](tue2_images.md) 


Apply regularization, then add a drop out layer and finally combine both regularization with a dropout layer. 
Produce a plot that illustrates and compares all four models. Why in your estimation did certain models perform better?
- [comparison of 4 models](tue2_images.md)
- my models and graph demonstrate conclusion and observation consistent with the TensorFlow
webpage for the most part--with combo and tiny models ranking among the best--except that
  my graph shows a strange spike and a wider divergence towards the end for "Dropout Train" and "Dropout Val"
    - though on the TensorFlow graph, there is also a slight divergence for "dropout train" and "dropout val"

What is an overfit model? Why is it important to address it? 
What are four different ways we have addressed an overfit model thus far?
- overfit model is a model that predicts with high accuracy for training dataset but fails to
generalize for testing data or data it has never seen
  - overfitting occurs when training and validation loss metrics go off in opposite direction
- it is important to address it because the purpose of building model is to generalize it for use on
data that it has never seen before. Thus, overfitting is a problem that needs to be overcome
  
### Monday Week 3
(just training, no testing)

Start with the Load CSV data script that we prepared during today's class. Following the Mixed data types section from the exercise, replace the titanic dataset first with the Metro Interstate Traffic Volume Data Set and then with the Iris Dataset. You can use the read_csv() command from the pandas package to pull these datasets from the following web addresses.

    https://archive.ics.uci.edu/ml/machine-learning-databases/00492/Metro_Interstate_Traffic_Volume.csv.gz
    https://storage.googleapis.com/download.tensorflow.org/data/iris_training.csv

Use the plot_model() command from tf.keras.utils to produce the plot that describes the input preprocessing step. 
Describe the plot of each model for the two dataset preprocessing steps. 
What does each box in the illustration represent? Are there different paths towards the final concatenation step? 
What is occurring at each step and why is it necessary to execute before fitting your model. 
Train each model and produce the output (not necessary to validate or test). 
Describe the model output from both the metro traffic interstate dataset and the iris flowers dataset. 
What is the target for each dataset? How would you assess the accuracy of each model? Are you using a different metric for each one? 
Why is this so? What is each one measuring?
- [plots for both metro and iris datasets](mon3_images.md)
- Metro Dataset:
    - The first layer (left-most side) boxes are all Inputs
    - the second layer are separated into 'concatenate' and 'string_lookup'
        - All the continuous/numeric features are concatenated
        - All the categorical features are passed to "string_lookup"
            - mappingto CategoryEncoding
    - The third layer involves "normalization" and "CategoryEncoding"
        - normalization transforms inputs/features into a distribution centered around 0 with standard deviation 1
        - category encoding is a.k.a one hot encoding
            - creates dummy variables 
            - quantify categorical data
            - represent categorical words as numeric combinations of 0s and 1s
                - so position and order of 0s and 1s matter
            - https://deepai.org/machine-learning-glossary-and-terms/one-hot-encoding
    - the fourth layer is concatenation of both the normalized numeric features plus the category-encoded categorical features
    - the separation of concatenation and string_lookup in layer 2 is because continuous features and categorical features are applied
      two different methods (which are in layer 3: normalization and category encoding)
    - it is necessary to execute concatenation (of both numeric plus categorical) before fitting the model
    because it speeds up the training 
        - due to the vast amount of parameters in the neural network
    
    - target: traffic_volume
    - output of metro model:
        - loss of epoch 10: 0.9665
    
- Iris dataset
    - target: species
        - represents the 3 classes of iris
    - output of iris model: (epoch 10)
        - loss for scenario 1: 0.0140
        - loss for scenario 2: 0.8375
        - loss for scenario 3: 0.1358
        - [loss](mon3_images.md)
    - I run the model with three variations for the iris dataset
        - for each variation, one class is assigned a 1, while the other two classes are assigned a 0
            - making it a binary problem to investigate
    - The iris dataset plot_model() has four layers
        - the first layer is InputLayer
            - comprised of four boxes, each representing an input feature of the iris dataset
                - sepal_length, sepal_width, petal_length, petal_width
        - the second layer is a Concatenate layer
            - because all the input features are of the same data type (continuous/numeric), they 
            are concatenated together
        - the third layer is Normalization
            - because all the input features are continuous/numeric, that's why normalization 
            is applied
        - the fourth layer is Concatenate a second time      
    
    
- with just training and no testing, accuracy of each model can be assessed by
    - looking at loss
        - of the last epoch of training
- metrics used:
    - metro: loss=tf.losses.MeanSquaredLogarithmicError()
        - measures mean squared logarithmic error between actual labels and predicted labels
        - I tried MeanSquaredError, MeanAbsoluteError, and MeanAbsolutePercentageError as well
            - but MeanSquaredLogaritmicError() gives the most reasonable loss value
                - all the other loss metrics produce final loss value that are at least in the thousands
    - iris: loss=tf.losses.BinaryCrossentropy()
        - measures the loss between true labels and predicted labels
- different metrics are used because both datasets imply two very differnt problems to investigate thus require different approaches
    - metro: regression; one-variable target "traffic_volume" of Minneapolis St Paul 
        - features characteristics: multi-variate, sequential, time-series
        - https://archive.ics.uci.edu/ml/datasets/Metro+Interstate+Traffic+Volume#
    - iris: classification; 3-class target:
        - feature characteristics: multivariate
        - https://archive.ics.uci.edu/ml/datasets/iris
- the paths towards the final concatenation step is different for both datasets.  
Although both datasets' plot_model() both have four layers, because metro dataset has a more heterogenous feature mix, 
  while iris dataset has a more homogenous feature mix, metro dataset went through the additional process of 
  StringLookUp and CategoryEncoding for its categorical features.
    


    
    
    
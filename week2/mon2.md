###Week 2 Monday Response
dataset: https://archive.ics.uci.edu/ml/datasets/Automobile 

out of 26 variables, these are the categorical:
- make       
-  fuel-type  
-  aspiration  
-  num-of-doors  
-  body-style   
-  drive-wheels 
-  engine-location 
-  engine-type  
-  num-of-cylinders**
-  fuel-system

Start with the Regression script that we prepared during today's class. Replace the Auto MPG dataset provided in the tensorflow exercise with the Auto Imports dataset provided in the UCI Machine Learning Repository. Specify a model with the following target and features.

    highway-mpg (continuous)
    num-of-cylinders (categorical)
    engine-size (continuous)
    horsepower (continuous)
    curb-weight (continuous)

Specify and train both a multi-class linear regression and a multi-class DNN regression. Which of the two models produces a better loss metric (see this link for an explanation of the loss function). 
Produce a plot that supports your answer. Return to the remainder of the variables from the dataset and add additional continuous and categorical features with the intent of improving your loss metric. 
Produce a plot that demonstrates the value of your model. What is the best model your team was able to produce?
- [loss plots](mon2_images.md)
- between multi-class linear regression and multi-class DNN regression, the DNN model is better
    - Mean Absolute Error
        - DNN: 2.058904
        - linear regression: 2.571499
- next step: add additional variables one by one to "raw_dataset_variables" to see if model improves    
- After running the above listed 5 features (with num-of-cylinders as categorical variable), I run 24 more models (12 for multi-class linear
  regression and 12 for multi-class DNN)
each with a new continuous/numeric feature from the list of 26 features added to the original 5 and with still num-of-cylinders as
  categorical.  I then run 26 x 10 more models (24 models + 1 original linear regression + 1 original DNN), each 'loop' with a different categorical variable [check above list for categorical
  variable].
- for each 'loop' (holding one categorical variable constant for loop), a new continuous feature is added each time to run a model, 
  until all the continuous features have been added
- you can see the dataframes of MAE here [MAE dataframes](mon2_df.md)  
    - I highlighted which model
- because there are so many models ran, a plot visualization would be too complicated for the eyes.  
  Therefore, I chose to present the MAE information with dataframes
- the best model is "lin_city-mpg" with categorical variable "engine type" because it has the lowest MAE
of 0.690061, which is even lower than the original DNN and linear regression.
  - "lin_city-mpg" means linear regression model run with continuous features of 
        - symbolizing, normalized-losses, wheel-base, length, width, height, bore, stroke, compression-ratio, peak-rpm, AND CITY-MPG
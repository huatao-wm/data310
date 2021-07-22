### Thursday Week 3 Response
Using the Classify structured data using Keras Preprocessing Layers you prepared for today's 
class as a model example, train, validate and test a model that has wealth class as the target as follows.

    Import the dataset country_persons.csv to your PyCharm environment
    Initially set the target to the least wealthy class, 1 in this case, and set all other wealth class outcomes to 0 (2,3,4 & 5)
    Train, validate and test your model
    Interpret and analyze your results. Did the model performance exhibit a particular trend?

The dataset is *country_persons.csv*.  There are 14 features and 1 target.  The features are:
hhid, unit, weights, location, size, potable, toilet, electric, car, cook, wealth, pnmbr, gender, age, and education.  
The four features dropped from dataset are: hhid, pnmbr, unit, weights.  The problem under investigation here is whether we can 
find a relation between any of these 14 features to wealth -- that is whether and how do the features or combination of the feature reflect the wealth.

The first step is to convert this problem or dataset rather into a binary one before we
build and train the model.  Five models were built and trained, each with a different 'wealth' assigned to 1 with the other 'wealth' classes
set to 0.

    dataframe['target'] = np.where(dataframe['wealth']==1, 1, 0) 
    dataframe['target'] = np.where(dataframe['wealth']==2, 1, 0) 
    dataframe['target'] = np.where(dataframe['wealth']==3, 1, 0) 
    dataframe['target'] = np.where(dataframe['wealth']==4, 1, 0) 
    dataframe['target'] = np.where(dataframe['wealth']==5, 1, 0)

The numeric features are: size, age.  The categorical features encoded as integers are: gender, education.
The categorical feature encoded as strings are: location, potable, toilet, electric, car, cook.



Here are the TEST accuracy values for each model: 

{"1's test accuracy": 0.789921224117279, "2's test accuracy": 0.7392160892486572, "3's test accuracy": 0.7952094674110413, 
"4's test accuracy": 0.8825176358222961, "5's test accuracy": 0.9594566822052002}

see plot of accuracy for comparison across all five models: [plot of accuracies](thur3_images.md)

Trend: except for the second model, which accuracy decreased from first model's, the accuracies have shown
a pattern of increase as we increase value of "wealth".  
So these features are more accurate at predicting the wealthier demographics of the country.









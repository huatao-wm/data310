Using the Classify structured data with feature columns you prepared for today's class as a model example, train, validate and test a model that has wealth class as the target as follows.

    import the dataset city_persons.csv to your PyCharm environment
    Initially set the target to the least wealthy class, 2 in this case, and set all other wealth class outcomes to 0 (3,4 & 5)
    Train, validate and test your model
    Interpret and analyze your results. Did the model performance exhibit a particular trend?

The dataset had five features: age, gender, education, size, and wealth class. The ages ranged from 0-97 years. 
The size ranged from 1- 22. The gender was split 2458 and 2665, each assigned a value of 1 or 2 respectively. 
Education status was given a value of 0-2 with 1831 0’s. 1259 1’s, 1600 2’s, and 432 3’s. Wealth class, our target data, was categorized into a number 2-5. 
There were 64 2’s, 557 3’s, 1800 4’s, and 2702 5’s. Dropping rows that contained NaN values, gender, size, and wealth class had 5123 values but age and education had 5122.

The first step is to convert the dataset into a binary problem to investigate.  There are four classes of
"wealthC" -- 2, 3, 4, 5 -- ranging from least to most wealthy.  I ran 4 rounds, each round assigning a value of 1 to
one of the four classes, while assigning a "0" to other three classes-- making the problem a binary one to investigate.
For each round, I also run 3 sub-rounds, each testing out a different 'feature columns' combination.  The firt sub-round
is a combination of numeric column and bucketized column; features "size", "gender", "age", "edu" are inputted into numeric column,
while "age" is inputted into bucketized column.  The second sub-group is also a combination of numeric column and bucketized column, only
this time "age" is removed from numeric column.  The third combination is numeric, bucketized, and indicator columns.  "size" and "edu"
is fed into numeric column, "age" fed into bucketized column, and "gender" is inputted into indicator column.
10 epochs are used for each round and sub-round for fitting model.  BinaryCrossentropy is the loss metrics used during compiling.
The model has two hidden Dense layers, each with 128 neurons and one Dropout layer with a parameter of 0.1.  
Check the accuracies here:
[accuracy](wed3_images.md)

Overall, our models performed better on predicting lower wealth.
Both Numeric cols [size, gender, age, edu] + bucketized cols (age)
and Numeric cols [size, gender, edu] + bucketized cols (age)
performed better overall than the Numeric [size, edu] bucket[age] indicator [gender]
model.
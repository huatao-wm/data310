Using the Classify structured data with feature columns you prepared for today's class as a model example, train, validate and test a model that has wealth class as the target as follows.

    import the dataset city_persons.csv to your PyCharm environment
    Initially set the target to the least wealthy class, 2 in this case, and set all other wealth class outcomes to 0 (3,4 & 5)
    Train, validate and test your model
    Interpret and analyze your results. Did the model performance exhibit a particular trend?


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
Check the accuracies here: [accuracy](week3/wed3_images.md)
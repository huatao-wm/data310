### Project 3



- Using either the Classify structured data with feature columns script or the Classify structured data using Keras Preprocessing Layers with the country_persons.csv dataset, specify, train and evaluate models that predict class of wealth versus all other classes as a binary target. Amongst the five possible binary targets (1 versus all others, 2 versus all other etc...), produce your results from the two models with the best and worst accuracy.

- Using the data and two models you produced in step 1, create a confusion matrix. You are welcome to use the following script. With your confusion matrix as a reference, analyze and discuss the two sets of results you produced.

- Again using either the Classify structured data with feature columns script or the Classify structured data using Keras Preprocessing Layers with the country_persons.csv dataset, specify, train and evaluate a model that predicts all class of wealth outcomes as a categorical target. Again create a confusion matrix in order to analyze and discuss your results. Revisit the Classify structured data with feature columns script or the Classify structured data using Keras Preprocessing Layers in order to modify your feature columns, in attempt to improve the accuracy of your model that uses all five categorical wealth classes as the target. Analyze and discuss your progress and results.

Step 1. Define your confusion matrix plot command

    def plot_confusion_matrix(cm, classes,
    normalize=False,
    title='Confusion matrix',
    cmap=plt.cm.Blues):
    """
    This function prints and plots the confusion matrix.
    Normalization can be applied by setting `normalize=True`.
    """
    import itertools
    if normalize:
    cm = cm.astype('float') / cm.sum(axis=1)[:, np.newaxis]
    print("Normalized confusion matrix")
    else:
    print('Confusion matrix, without normalization')
    
    print(cm)
    
    plt.imshow(cm, interpolation='nearest', cmap=cmap)
    plt.title(title)
    plt.colorbar()
    tick_marks = np.arange(len(classes))
    plt.xticks(tick_marks, classes, rotation=45)
    plt.yticks(tick_marks, classes)
    
    fmt = '.2f' if normalize else 'd'
    thresh = cm.max() / 2.
    for i, j in itertools.product(range(cm.shape[0]), range(cm.shape[1])):
    plt.text(j, i, format(cm[i, j], fmt),
    horizontalalignment="center",
    color="white" if cm[i, j] > thresh else "black")
    
    plt.ylabel('True label')
    plt.xlabel('Predicted label')
    plt.tight_layout()

Step 2. Create objects that describe the true and predicted target values

    y_true = assign the true target values to this object
    y_pred = assign the predicted target values to this object

Step 3. Plot your confusion matrix

    cnf_matrix = confusion_matrix(y_true, y_pred,labels=[add labels here])
    np.set_printoptions(precision=2)
    
    plt.figure()
    plot_confusion_matrix(cnf_matrix, classes=[add labels here],
    title='title your plot')
    plt.show()


The dataset used is "country_persons.csv", which contains demographics information about population
in Liberia and the wealth classes there.  Target variable is wealth class.  "Wealth" class is a numeric categorical variable; 
there are 1-5 classes of wealth, with 1 being poorest and 5 richest.
Features are: hhid, unit, weights, location, size, potable, electric, car, cook, pnmbr, gender, age, and education

Out of the two approaches--feature columns or preprocessing layers--I chose to use feature columns in this project.

There are two components to this project.  The first component is create, train, and evaluate binary models, each model with one of the 'wealth' classes
assigned "1", with other 'wealth' classes assigned "0"s (five possible binary targets).  Then, create confusion matrix one for least accurate and one for most accurate models out of
all fives models.  The second component is to create, train, and evaluate a model with all five 'wealth' classes as one single categorical target.

---------------------------------------------------------------------------
Regarding the first component (binary models):

As preprocessing data steps, I dropped columns [hhid, pnmbr, unit, weights].  I also dropped missing values from
columns [potable, toilet, electric, car, cook] (**note: at first step, I have not dropped missing values for "age" and "education", because of a mistake on my part.)

For all the binary models variations: 

        optimizer = 'adam'
        loss metrics = BinaryCrossentropy
        accuracy metrics = ['accuracy']

epochs = 30

At first, I created 3 sets of models (each set is 5 models), with each set having a different "combo" or 
feature columns settings.  At this point, no "sigmoid" nor "softmax" has been applied, when building the model at this point.
All three sets of models demonstrated a consistent observation of accuracy increases as you move from 'wealth' class 
1 to 5, but accuracy dips as you go from 1 to 2 and then picks up after 2.  Therefore 'wealth' class 2 model 
yields the lowest accuracy, while 'wealth' class 5 model yields the highest accuracy--for all three sets of models.
I chose to go with combo 3's settings, therefore from here on I will use combo 3 models for rest of the tasks for this project.

        - combo 1 has 
            - numeric feature column: size, gender, age, education
            - indicator feature column: location, potable, toilet, electric, car, cook
            - ACCURACY
                - {'wealth 1': 0.8059251308441162,
                    'wealth 2': 0.7600831389427185,
                    'wealth 3': 0.8222452998161316,
                    'wealth 4': 0.9132016897201538,
                    'wealth 5': 0.9697505235671997}
        - comb 2 has
            - numeric: size, age
            - categorical: location, potable, toilet, electric, car, cook, gender, education
            - ACCURACY
                {'wealth 1': 0.8032224774360657,
                'wealth 2': 0.7548856735229492,
                'wealth 3': 0.8192307949066162,
                'wealth 4': 0.9188149571418762,
                'wealth 5': 0.9636174440383911}
        - combo 3 has
            - numeric: size
            - bucketized: age
            - categorical: potable, toilet, electric, car, cook, gender, education
            - embedding: location
            - ACCURACY
                {'wealth 1': 0.8030145764350891,
                'wealth 2': 0.7616423964500427, ****
                'wealth 3': 0.8267151713371277,
                'wealth 4': 0.9234927296638489,
                'wealth 5': 0.9664241075515747}***


Then, I went on to add "activation = 'sigmoid' " to the last Dense layer when building model, 
only for combo 3 settings of feature columns.  Here is the result/accuracy I got:

                {'wealth 1': 0.8175675868988037,
                'wealth 2': 0.7579001784324646,
                'wealth 3': 0.8224532008171082,
                'wealth 4': 0.9217255711555481,
                'wealth 5': 0.9675675630569458}


Next, I went on to remove the missing values of "education" and "age", and also made some changes to feature column settings.
Now, feature columns are condensed into only numeric, bucketized, indicator. 
Check here for confusion matrices of 'wealth 2' (least accurate) and 'wealth 5' (most accurate model) [confusion matrix](project3_images.md)
    
        numeric: size, age
        bucketized: age (age is deliberately repeated for numeric and bucketized)
        indicator: 'location', 'potable', 'toilet', 'electric', 'car', 'cook', 'gender', 'education'

        ACCURACY:
            {'wealth 1': 0.8097667694091797,
            'wealth 2': 0.7487505078315735, ***
            'wealth 3': 0.8105997443199158,
            'wealth 4': 0.9177426099777222,
            'wealth 5': 0.9647021889686584} ***



As last step for binary models, keeping same settings of feature columns and removal of missing values like the one set of models
right before this paragraph, I would aggregate "toilet" and "potable" features's entries, respectively.
Check here for details on aggregation of the two features [feature aggregation](project3_images.md)
Check here for confusion matrices [confusion matrix](project3_images.md)

After aggregating the two features respectively and replace those two columns' entries with the newly aggregated entries (numeric labels),
I rerun the model again.  
    
    Here is the result/accuracy:

        {'wealth 1': 0.7994585633277893,
        'wealth 2': 0.7504165172576904,
        'wealth 3': 0.8034152388572693,
        'wealth 4': 0.911078691482544,
        'wealth 5': 0.9662640690803528}

Final words about binary models: 

Overall, the accuracy stays relatively similar no matter what setting tweaks I made.  
The aggregation did make the accuracy values slightly better but not much.  Also, the set of models where 
I first added "sigmoid" outperformed the aggregated set of models by a bit -- difference only visible at the thousandth place forward.

An observation: looking at confusion matrices, there are more correctly labeled '0's than '1's because
every time running the binary model, only one class is assigned '1' while all four other classes 
are assigned '0's making the data sample size of '0's much larger than '1' 



-----------------------------------------------------------------
#### all five wealth classes as one categorical target

Here is link to see all confusion matrices of below models: [confusion matrices of categorical target](project3_images.md)

- first model


For this second component of the project, I also first run a model with all missing values removed for all features except for 'age' and 'education'. 
This first model has the same feature column setting as combo 3 of the first sets of models of binary models: 

            - numeric: size
            - bucketized: age
            - categorical: potable, toilet, electric, car, cook, gender, education
            - embedding: location

Also, this time I did not do "activation = 'sigmoid' " but rather "activation = 'softmax'
when building the model.  The accuracy/result is: 

    {'wealth as categorical target': 0.6370062232017517}



- second model

Then, the second model has missing values of "age" and "education" removed in addition to the 
other missing values removed already in the previous model.  The feature column settings have changed to:

            - numeric: size, age
            - bucketized: age
            - categorical: location, potable, toilet, electric, car, cook, gender, education
Accuracy/result is 
        
    {'wealth as categorical target': 0.6304664611816406}


- third model

For the third model, I did aggregate features the same way as in first component of project binary models,
with "potable" and "toilet".

- fourth model

for the fourth model, I attempted to improve the model by eliminating aggregation of features and added "embedding feature column"
for 'location'.  This one is slightly different from the first categorical target model because
the first model did not include "age" as numeric feature column while only for "bucketized".  This fourth model includes
"age" for both feature columns.

          - numeric: size
          - bucketized: age
          - categorical: potable, toilet, electric, car, cook, gender, education
          - embedding: location

Here is the accuracy/result:

    {'wealth as categorical target': 0.6215118765830994}


I failed to improve the categorical target model.  In fact, every time I made an attempt, whether it's 
aggregation of features or adding embedding feature column, the accuracy decreases further.  The first model
without aggregation and even w/o removing missing values for two features came out to have highest accuracy.
The second most accurate model is the model where I first tried to remove the missing values for the two features.
Also, even the most accurate model of categorical target has a much lower accuracy compared to even the least accurate
binary models.  However, do note that there are many more features to train and account for in the categorical model compared
to only two features in binary models making the former more difficult.
    

















                



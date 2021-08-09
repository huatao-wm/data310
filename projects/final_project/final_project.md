### Final Project - Credit Analysis & Binary Classification


#### Abstract

In this project, the problem to investigate is how accurately can I train a model to predict a person’s credit worthiness.  In other words, I will build models to predict and identify those who are more likely to default on payments before the default actually takes place.  This is important for banks when they make lending decisions—to whom to lend to and what interest rate to charge.  The goal is, first, to see how accurate a credit worthiness predictive model can I build, and second, whether I can identify certain features that significantly contribute to determine a person’s credit worthiness.  

Two datasets are used in this project.  The simplified version and full version datasets differ only in the number of features included and data types of each feature.  Both datasets investigate and classify a sample of people in Germany by a set of attributes as good or bad credit risks.  There are 1000 observations.  The target is a binary variable named ‘Risk’, and the entries of ‘Risk’ are ‘good’ and ‘bad’.  ‘Good’ is credit worthy, and ‘bad’ is not worthy.  There are 700 ‘good’ observations, and 300 ‘bad’ observations.  The full dataset contains 20 features, while the simplified version has 9 features.  Both datasets’ data types are numeric and categorical.  The difference is that one feature could be numeric in one dataset but categorical in another, or vice versa.  Details regarding the datasets can be found in the links below.

The binary classification predictive models that I build are based on the script “Classify structured data with feature columns” under the section “Structured Data” from Tensorflow.  I try different feature columns and different combinations of features to assign to each selected feature columns.  I also try normalization within numeric feature column by the parameter ‘normalizer_fn = ‘.  I also try to one-hot-encode features.   Out of the seven working models that I built, the first six uses simplified dataset, while only the last model uses the full dataset.  The metrics that I use to assess the models include testing accuracy, precision, and false positive percentage versus false negative percentage.


https://www.kaggle.com/uciml/german-credit (simplified dataset)

https://www.kaggle.com/sid321axn/south-german-credit-updated (full dataset)

#### link to view presentation recording: 
https://drive.google.com/file/d/1ThXXlD1ja-hJywh6zlNYS2AMVKF_nNia/view?usp=sharing

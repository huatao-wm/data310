Overview:
- dataset: LA with 500 results
    - 428 datapoints after removing Nan rows
- no train/test split

graphs with inverse transformed/unscaled data
- [plots](project1_images.md)


How did your model fare?
- The MSE is 131769005358912.25, with scaled data
    - scale: x 1/1000 for 'price' and 'LivingArea' and 'predicted price'
- estimator of error (y-y_pred): the lowest one is 2985.374634  
  - y and y_pred used are scaled
- Although I do not have any other model to make comparison with,
just looking at the estimator of error, there is still a long way to go
  before reaching the ideal error = or near 0.
 - this model has limitations and hence yielded such unoptimal result
    - because it is a neural network with only 1 layer
    - and 500 results/datapoints are not enough to build a good model
 - therefore, ideally, we would need more than 500 and at least thousands if not
tens of thousands of datapoints in addition to adding a couople more
   layers to make the model better.  Also, splitting dataset into train, test groups
   may help as well, but that would be if we have more datapoints.  500 datapoints
   render splitting not so effective.


In your estimation is there a particular variable that may improve model performance?
- [histogram](project1_images.md)
- what (spatial) variables are yielding the highest error (y-y_pred):
  I see these following address/city + address/zipcode have multiple occurrence in the top highest errors
    - address/city
        - Los Angeles, Beverly Hills
    - address/zipcode
        - 90077, 90210
- [dataframe sorted by descending y-y_pred](project1_images.md)    
  
- REVISION:
- the variables that may improve model performance include variables like address/city,
address/zipcode, longitude, and latitude. 




Which of the predictions were the most accurate? In which percentile do these most accurate predictions reside? Did your model trend towards over or under predicting home values?
- row 23: 
    - actual price 2800, bedrooms: 2; bathrooms: 2, LivingArea: 1200
- row 252: 
    - actual price 89888, bedrooms: 1; bathrooms: 1; living area: 520
- row 23 and row 252 of the dataframe are the most accurate predictions
    - because their y-y_pred is the top 2 smallest (2985 and 91160)
    - from third smallest on, the % change in difference is not as large as the first two
        - for example the top 4 smallest are: 
            - 2985, 91160, 150650, 169850
        - [sorted df based on ascending y-y_pred](project1_images.md)
- the percentile these two most accurate predictions reside is top 0.467%
    - 2/428
    - because there are 428 total datapoints or rows
- model trends toward overestimating because when I count the number of 
positive vs. negative y-y_pred values, all of them are positive

Which feature appears to be the most significant predictor?
- I ran models 6 times, each time only with one of the following features and with the target 'price'
    - features: bathrooms, bedrooms, latitude, longitude, livingArea, yearBuilt
- then I run MSE 6 times
- 'bedrooms' came out to have the lowest MSE (3497)
    - thus, it would be the most significant predictor compared to the other 5
        - because MSe tells how close predicted values are to actual values
        - and the lower the better (or more accurate)

- REVISION:
- 'bathroom' is the most significant predictor of 'price' because
    - looking along the column/row of 'price' on heatmap, 'bathroom' has the highest
    correlation coefficient of 0.83, compared to other variables
- [heatmap](project1_images.md)      


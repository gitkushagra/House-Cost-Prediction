# House-Cost-Prediction

# MyFirstMLmodel


The model is trained for predicting the house prices based on given features dataset. The dataset is provided with certain features and a label. The dataset is taken from "housing data boston uci repository". 
This project is done with the help from YouTube "codeWithHarry". Respect Mr. Harry sir guided in this project, in which we have solved the prediction problem of Dragon Real EState.
I have followed his video step by step to put my first practical approach in training the dataset.

The project follows:
* Supervised learning
* Has Regression task
* It is a batch learning i.e. input data is not continuous.
* The model uses Root Mean Squared Error for identifying the better algorithm.

In this project, data needs to be trained to give the pricing of the houses as accurate as possible.

1. First converted the raw data from Internet into csv (comma-separated values) file.
2. Integrating each column in housing data with housing names.
3. Analyzing the dataset using Pandas and matplotlib libraries.
4. Then Training data & testing data splitting is done. It is done to saparate training data with test data. As doing all activities and performing algorithms directly to data can harm our predictions in real life scenarios. Test data is preserved and never touched until model is prepared.
5. We used scikit learn for startified sampling. Stratified sampling is necessary as it covers all kind of data in our population. In aboove method, stratified sampling is not guranteed. For ex. CHAS has 471 "0" values and 35 "1" values. It is important to make sure training data shows both 0 and 1 values to the algorithm.
6. Then we observed the correlation of label to each feature. Pearson correlation value lies between -1 and 1. Where -1 means "strong negative correlation" which means inversely propotional, 1 means "strong postive correlation" which means directly proptional.
7. Choosen the best column based on linear growth from graphs i.e. RM (Number of rooms). Then, drawing plot between RM and label i.e. MEDV. We can elimate the outlier points to get more accurate results in our predictions. This is the benifit of finding correlation matrix.
8. Then, Trying out new attribute combinations to get better coorelations, like divided TAX with RM to get a new column TAXRM, which has better negstive correlation.
9. Handling missing Values
To take care of missing values, we have three options:
-- Get rid of missing data points.
-- Get rid of whole attribute.
-- To replace missing values with 0, Mean or Median, whichever suites the most.
Choosen the third approach.
10. Used Scikit learn built-in imputer to deal with missing values.
11. Feature Scaling to scale small and large values for better predictions.
 -- Min-Max (Normalization) (value - min)/(max - min) sklearn provides a class called MinMaxScaler
 -- Standardization (value-mean)/std std means standard deviation sklearn provides a class called Standard Scaler
12. In this project, Standardization is used while creating the pipeline. Pipeline is used for a series of atomation.
13. Selecting a desired model for our project based on above observations. Tedsted for:
 -- LinearRegression (Rejected based on Mean:  4.972693947923473 Standard Deviation:  1.0635397337561052)
 -- DecisionTreeRegressor (Rejected based on Mean:  4.451684086300771 Standard Deviation:  0.9134544540801773)
 -- RandomForestRegressor (Choosen based on Mean:  3.3613984223751876 Standard Deviation:  0.6871641160560278)
 All these predictions are recorded in a "Results.txt" file.
14. Evaluation of the model, to get rid of overfitting or underfitting. This is done for each algorithm to observe rmse (root mean squared error). The lesser the value the better is the algorithm. But it should not be the zero, as we are getting in DecisionTreeRegressor algorithm in which it got overfitted.
15. Once overfitting was occured, we prepared for better evaluation with cross validation. In this, We will do stepwise testing for errors. Like, in first round, we will eliminate 1, and test rest of the cases, than eliminate 1,2 and test rest of the cases and so on... for 1,2,3,4,5,6,7,8..
16. scikit learn has cross_val_score function to perform the operation. By using different "rmse_scores" (root mean squared errors) of different algorithms and observing Mean and std, helped in selection of better algorithm.
17. Finally, after choosing the algorithm, the model needs to be saved for future purposes. 
18. It is saved using "dump" function under joblib.
19. Finally, testing the model for test data. In my case, it got 3.0763381131264658 as rmse value. Which is different from YouTube Video.

Result: Model is trained as expected with rmse= 3.0763381131264658 on test dataset. Which is acceptable.

# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Gleb

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
No changes were needed, apart from making sure that data is in a tabular format with datetimes in the first column and predicted values in the second column. No changes were needed, since all the predictions were positive. This was checked using the `.describe()` on the output dataframe and checking that the minimum value is above zero.For all further runs the same check was performed and where necessary negative predictions were converted to zero.

### What was the top ranked model that performed?
The top ranked model during the inital training scored `1.42564` on kaggle without any additional tunning or data manipulation. The model was `WeightedEnsemble_L3`.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
During the EDA I have found out the distributions of the features using histogram plots. This helped me realise that some data such as weather appears to be numeric, however actually represents different categories. Changing the data type of those columns could have an effect on the performance of the models since AutoGluon would treat them as non-continuous categories instead of numerical data.

I added new features based on the date column using the `pandas` methods for date objects. The columns extracted data avaliable from a datetime object which would open up more possibilities for model training as it explicitly exposes properties like day of the week and hour of the day, which would have an effect on the data. 

### How much better did your model preform after adding additional features and why do you think that is?
The model is able to extract insight from the data as some information is now explicitly states (ie day of the week).
Overall this had a positive effect on the performance of the model by changing the kaggle score from 1.42564 to 0.47215.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The model has showed a slightly worse performance after tunning the hyperparameters as the kaggle score increased from 0.47215 to 0.61785

### If you were given more time with this dataset, where do you think you would spend more time?
I would spend more time tunning hyperparameters, trying to reconstruct the best estimator using sklearn and do hyperparameter tunning using the random search cross validation grid. I would also look into bringing more data, ie more information about the weather.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
Not sure how to present hyperparameter data, as in the last run the model was tunned across a range of hyperparameters at the same time.

### Create a line plot showing the top model score for the three (or more) training runs during the project.
![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.
![model_test_score.png](img/model_test_score.png)

## Summary
This project focused on predicting bike-sharing demand using AutoGluon. Initial submission was trained on raw data with minimal preprocessing. The best performing model was `WeightedEnsemble_L3` achieving a Kaggle score of 1.42564 without tuning. Exploratory data analysis revealed that some numerically encoded features, such as weather, were actually categorical, and converting them accordingly improved model interpretation. Significant performance gains came from feature engineering, particularly extracting datetime components like hour and day of the week, which reduced the Kaggle score dramatically to 0.47215. Hyperparameter tuning was later applied but slightly worsened performance to 0.61785. With more time, further systematic hyperparameter tuning and incorporating additional external data, such as more detailed weather information, could potentially improve results further.

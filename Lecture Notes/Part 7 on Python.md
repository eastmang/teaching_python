# Part 7: SKlearn

## --- SKlearn ---
This package is used for running models and analysis in python

Pros:
1. It tends to be fast and has a wide array of useful functions for managing and analyzing data.
2. There are a lot of models with easily useable and well documented functionality and hyperparameters.

Cons:
1. It is not very verbose. It usually just gives the final output but no other helpful metrics. 
2. The reverse of the pros and cons of this package is the statsmodels package.


## --- Common functions ---
One of the most commonly used functions you may see is used to split the data for analysis. Often times
we want to validate the model we are building. Therefore we split the data into training and testing sets.

from sklearn.model_selection import train_test_split
<br /> 
x_train, x_test, y_train, y_test = train_test_split(predictor, predicted, test_size = .33, random_state = 1)

We have the 4 data sets we are making. It will randomly select observations from the predictor and predicted columns.
The testing dataset will be 1/3rd the size of the original. The random state ensure we get consistent randomization each time.


Lets just look quickly at how to implement a simple linear regression. The main commands used are uniform across
sklearn models, like .fit or .predict, etc.

from sklearn.linear_model import LinearRegression

1. Make the model and name it something. (There are a lot of optional hyperparameters)
<br /> 
model = LinearRegression(fit_intercept = True)

2. Fit the model on the training datasets 
<br />
model.fit(X_train,y_train)

3. Get predictions
<br /> 
y_pred = model.predict(x_test)

4. Get metrics and other pertinent information
<br /> 
from sklearn.metrics import r2_score
<br /> 
r2_score(y_test, y_pred)
<br /> 
mse = sklearn.metrics.mean_squared_error(y_test, y_pred)
<br /> 
import math
<br /> 
rmse = math.sqrt(mse)
<br /> 
print(rmse)

5. Model Coefficient
<br /> 
model.coef_

6. Model intercept
<br /> 
model.intercet_

Other regression notes:
sklearn needs special preperation for categorical variables
 
We can use pandas to do this
<br /> 
pd.get_dummies(data = predictors_with_categoricals, drop_first = True)

We need to drop the first otherwise regression will not work. The reason why is more stats oriented and we can go into 
that if it is helpful, otherwise take my word for it for now. 
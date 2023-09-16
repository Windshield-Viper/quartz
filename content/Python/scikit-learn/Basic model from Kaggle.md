- Basics - X is the data and y is what is being predicted
- Data needs to be split into training data and test data (to prevent overfitting)
- [Mean absolute error](https://en.wikipedia.org/wiki/Mean_absolute_error)
- Data here is being saved as a [[DataFrame]], and being viewed using other Pandas features

```python
# Import helpful libraries
import pandas as pd
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error
from sklearn.model_selection import train_test_split

# Load the data, and separate the target
iowa_file_path = '../input/train.csv'
# turn csv data into a DataFrame
home_data = pd.read_csv(iowa_file_path)
# y is what we want to predict
y = home_data.SalePrice

# Create X (After completing the exercise, you can return to modify this line!)
# what this means is that these are the data points that the model will use to predict the sale price
features = ['LotArea', 'YearBuilt', '1stFlrSF', '2ndFlrSF', 'FullBath', 'BedroomAbvGr', 'TotRmsAbvGrd']

# Select columns corresponding to features, and preview the data (this is just to make sure that the data looks good)
X = home_data[features]
X.head()

# Split into validation and training data
train_X, val_X, train_y, val_y = train_test_split(X, y, random_state=1)

# Define a random forest model
# a less nuanced model would be a DecisionTreeRegressor, which could also be used, albeit for worse results. 
rf_model = RandomForestRegressor(random_state=1)
rf_model.fit(train_X, train_y)
rf_val_predictions = rf_model.predict(val_X)
#test how good the model is on the test data
rf_val_mae = mean_absolute_error(rf_val_predictions, val_y)

print("Validation MAE for Random Forest Model: {:,.0f}".format(rf_val_mae))


# To improve accuracy, create a new Random Forest model which you will train on all training data. We call random_state 1 for repreducible results.
rf_model_on_full_data = RandomForestRegressor(random_state=1)

# fit rf_model_on_full_data on all data from the training data
rf_model_on_full_data.fit(X, y)


# path to output file
test_data_path = '../input/test.csv'

# read test data file using pandas
test_data = pd.read_csv(test_data_path)

# create test_X which comes from test_data but includes only the columns used for prediction.
# The list of columns is stored in a variable called features
test_X = test_data[features]

# make predictions which we will submit. 
test_preds = rf_model_on_full_data.predict(test_X)

# Run the code to save predictions in the format used for competition scoring on Kaggle

output = pd.DataFrame({'Id': test_data.Id,
                       'SalePrice': test_preds})
output.to_csv('submission.csv', index=False)
```
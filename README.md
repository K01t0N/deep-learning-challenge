# deep-learning-challenge

## Analysis Overview

This analysis was conducted to evaluate neural network models created for Alphabet soup. The data countains different charities, funding amounts, and theri success. Neural network models were trained on this data to predict the outcome of a given charity.

**Data Preprocessing**

`IS_SUCCESSFUL` was the target variable for the model, indicating a 0 or 1 whether the outcome was successful. The `EIN` and `NAME` columns were not used in the models, making them neither target varaibles nor features. The rest of the data columns were used as features for the models, consisting as several inputs for the model.

**Compiling, Training, and Evaluating Models**

The following models were developed to test the predictiveness of the data:

**Model 1**

Model 1 ran on 2 hidden layers, each with 5 neurons and relu activations. The input dim was the length of the features (48). The output layer was one neuron with a sigmoid function.

Both `APPLICATION_TYPE` and `CLASSIFICATION` were simplified before using `pd.get_dummies`:

- For `APPLICATION_TYPE`, values under a count of 10 were put in a value called 'other'.
- For `CLASSIFICATION`, values with counts at least 50 but less than 1,000 were 'Other', and values with counts less than 50 were 'Other_2'.

This in turn created 48 features after using `pd.get_dummies`.

The model was trained for 150 epochs, and had a loss of 0.5540777444839478, and an accuracy of 0.7269970774650574.

**Model 2**

Model 2's neural network had the same neurons, layers, and activations as Model 1. The main difference is that `APPLICATION TYPE` and `CLASSIFICATION` were put into `pd.get_dummies` as-is, without reducing the number of features. I wanted to see if increasing the number of features would have a difference in model accuracy. The number of features ended being 116, compared to 48 from model 1.

Being trained on 150 epochs, the model had a loss of 0.551231861114502, and an accuracy of 0.7364431619644165. This is around 1% higher than the previous model.

**Model 3**

Model 3 is a variation on Model 2, in which all aspects are the same except that both hidden layers have 10 neurons each.


## Conclusion

Overall, none of these models really performed exceptionally well with trying to capture the nuances of the data. Underfitting was a major issue when training the models. I would recommend training this data on a random forest algorithm. The advantage to a random forest is that feature importances can be viewed, allowing further analysis of what inputs are helping or hurting the model.
# Neural_Network_Charity_Analysis
## Overview of the analysis: 
Alphabet Soup’s business team provided a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. This dataset includes a number of columns that capture metadata about each organization.
Machine learning and neural networks techniques were used to create a binary classifier that is capable of predicting whether applications will be successful if funded by Alphabet Soup.

## Results
### Data Preprocessing
#### Target Variable: The target variable was selected the “IS_SUCCESSFUL” column. This target indicates if the money was used effectively 

#### Feature variables: The feature variable includes the following columns:
* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special consideration for application
* ASK_AMT—Funding am

#### Deleted Features
Two columns were deleted from features including EIN and NAME—columns as they won’t have any affect on chance of success for an applicant. Also, later the “Status” column was deleted in optimization phase because only it affects 5 applications. 

### Compiling, Training, and Evaluating the Model
The process of model -> fit -> predict/transform follows the following steps:
* Decide on a model, and create a model instance.
* Split into training and testing sets, and preprocess the data.
* Train/fit the training data to the model. (Note that "train" and "fit" are used interchangeably in Python libraries as well as the data field.)
* Use the model for predictions and transformations.

A screenshot of model parameters is shown below:
![image](https://user-images.githubusercontent.com/58461542/184471367-729f3fc9-9bfe-4da6-a886-202aa76f183d.png)

In first phase the model included 43 columns or features and one target. 
In first phase, two hidden layer and one output layer was selected. The first and second layer, have 80 and 30 neurons, respectively. The output layer expectedly only has one neuron.
A good rule of thumb for a basic neural network is to have two to three times the amount of neurons for first hidden layer as the number of features. Selection of 80 neurons roughly follows this rule (Number for features = 43). Additional layers, typically need fewer neurons.
This resulted in 3520 parameters for layer 1 (43 features x 80 +80), 2430 parameters for layer 2 (380x30+30) and 31 parameters for output layer (30+1). 

The Rectified Linear Unit (ReLU) activation function was used for hidden layers and sigmoid function was used for output layer.

The target model performance was set to be accuracy of 75%, which was not achieved in first phase.

Number of tries (epochs was selected 100 times.


### Optimization Model
In optimization model, the following changes in the approach were tried:
* The status column was removed from features as it only affects 5 applications. 
* The  Leaky ReLU function was used for the second hidden layer instead of ReLU function.
* Number of neurons increased to 100 and 60 neurons for the first and second layer.
* One additional hidden layer (layer 3 with 4 neurons) was tried but removed after the results showed no improvement.
A screenshot of optimized model is shown below:
![image](https://user-images.githubusercontent.com/58461542/184471391-9ab331f2-b465-40f3-890b-8ab863d853ab.png)


## Summary
A screenshot of the results  for original model  is provided below:
![image](https://user-images.githubusercontent.com/58461542/184471397-3d05a605-44fa-48c0-8b85-dcb87932536d.png)


A screenshot of the results for optimized model  is provided below:

![image](https://user-images.githubusercontent.com/58461542/184471407-e1b25269-8dcb-4f9e-a05f-5eaef58b7461.png)

These results indicate the accuracy of both models is about 73% which is less than the acceptable limit of 75%. Unfortunately, the optimization measures used did not improve the model and slightly reduced the accuracy to 72%.


### Recommendation

A different machine learning technique can be used such as logistic regression, support vector machine, decision tree or random forest. In addition, I recommend plotting every single column versus the target column and remove the features that show nay correlation with target.




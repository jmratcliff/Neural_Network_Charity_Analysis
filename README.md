# Neural Network Charity Analysis
 *Charity funding analysis using neural network model*
 

## Overview

Create a deep learning model for AlphabetSoup to help predict whether applicants will be successful if funded.  Data file with 34,298 organizations that applied for funding over the past few years.  Use meta data and success flag to create a binary classifier model to predict what organizations will succeed if funded.


## Results

### Data Preprocessing

Data file contains 34,299 records/organizations with 12 columns of data:

![file](/images/file.png)

***Target variable*** = *IS_SUCCESSFUL*

Fields with count of unique values:

![fields](/images/fields.png)

#### Drop non-benefical columns

The ID fields of 'EIN' and 'NAME' were dropped from the DataFrame as they are not needed as features of the model.

The remaining fields will be the features of the model with some additional preprocessing:
* Categorical fields with more than 10 unique values will be binned by assigning low frequency values to an 'Other' category
* Categorical fields will then be encoded so that all features are numerical

#### Binning

APPLICATION_TYPE - 
Application type value counts were fairly wide-spread with a number of application types only having a few records:

![app](/images/app_values.png)

Application types with less than 150 values were put into an 'Other' category:

![app_bin](/images/app_binned.png)

CLASSIFICATION - 
Classification unique value counts were fairly wide-spread with a number of application types only having a few records:

![class](/images/class_values.png)

Classifications with less than 1,500 companies were put into an 'Other' category:

![class_bin](/images/class_binned.png)

#### Encoding

Categorical fields were then identified and encoded utilizing OneHotEncoder

![cat_enc](/images/cat_encoded.png)


### Compiling, Training and Evaluating Models

Model was initially set up with two hidden layers (8 and 5 neurons) with Relu activation function and an output layer with a Sigmoid activation function.

![model1](/images/model1.png)

The model target performance goal was an *Accuracy = 80%* which the intial model did NOT meet.

![model1r](/images/model1_result.png)

#### Model Optimization

***Model 2***
* STATUS field dropped
* Application_type and Classification fields binned slightly differently
* Neurons increased to 10 with an additional hidden layer

![model2](/images/model2.png)

Results were similar to original model:

![model2r](/images/model2_result.png)

***Model 3***
* hidden layer activation functions changed to Tanh

![model3](/images/model3.png)

Results were similar to original model:

![model3r](/images/model3_result.png)

***Model 4***
* Hidden layer activation functions changed to Sigmoid
* Output layer activation function changed to Relu

![model4](/images/model4.png)

Results were similar to original model:

![model4r](/images/model4_result.png)

***Model 5***
* STATUS and ASK_AMT fields dropped from input features
* Output layer activation function changed to Relu

![model5](/images/model5.png)

Results were similar to original model:

![model5r](/images/model5_result.png)


## Summary

The neural network model is fairly successful in predicting the success of an organization with an average ***73% accuracy.***
This model framework does not meet the target goal of ***80% accuracy.***
The neural network model had a high number of categorical values and was unable to identify pertinent variables in order to meet the accuracy goal.

#### Recommendation:

Due to the high number of categorical values and input fields - utilize an ***EasyEnsembleClassifier supervised machine learning model***

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

Categorical fields were then encoded utilizing OneHotEncoder

![cat_enc](/images/cat_encoded.png)


### Compiling, Training and Evaluating Models

Model was initially set up with two hidden layers (8 and 5 neurons) with Relu activation function and an output layer with a Sigmoid activation function.

![model1](/images/model1.png)

The model target performance goal was an *Accuracy = 80%* which the intial model did NOT meet.

![model1](/images/model1_results.png)




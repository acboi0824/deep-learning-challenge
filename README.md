# deep-learning-challenge
module 21 deep learning

Background
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special considerations for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

# Steps Taken:
## 1: Data Preprocessing
- Dataset was checked for null and duplicated values
insert image

- EIN and NAME—Identification columns removed from the input data because they are neither targets nor features
insert image

- Created cutoff point to bin "rare" categorical variables together in a new value, Other for both CLASSIFICATION and APPLICATION_TYPE
insert image
insert image

- Converted categorical data to numeric with pd.get_dummies, split the preprocessed data into features and target arrays, then lastly split into training and tesing datasets

## 2: Compiling, Training, and Evaluating the Model
I build the first model with the following parameters with low computation time in mind:

- 2 hidden layers with 5, 10 neurons split. With a hidden layer activation function of relu as this our go to for first model.
Output node is 1 as it was binary classifier model with only one output: was the funding application succesful yes or no. And an output layer activation of sigmoid as the model output is binary classification between 0 and 1.

image of 1st results

- I then increased the hidden layers to 3 and set the third hidden layer at 40 as the model prediction accuracy was below 75%:
 image of second results
 
## 3: Optimize the Model
I decided to use an automated model optimizer to get the most accurate model possible by creating method that creates a keras Sequential model using the keras-tuner library with hyperparametes options.

hyper tuner code here

The best model from the keras tuner method achieved 73% prediction accuracy using a relu activation function with input node of 76, 5 hidden layers at a 26, 1, 16, 1, 26 neurons split and 34 training epochs.
![hyper tuner](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")
 
 

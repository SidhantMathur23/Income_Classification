# Income Classification

<img src="https://github.com/SidhantMathur23/Income-Classification/blob/main/Other/Money%20gif.gif" width="650" height="400">
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" align="left">
<img src="https://img.shields.io/badge/conda-342B029.svg?&style=for-the-badge&logo=anaconda&logoColor=white" align="left">
<img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" align="left">
<img src="https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white" align="left">
<img src="https://img.shields.io/badge/Numpy-777BB4?style=for-the-badge&logo=numpy&logoColor=white" align="left">
<img src="https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" align="left">
<img src="https://img.shields.io/badge/SciPy-654FF0?style=for-the-badge&logo=SciPy&logoColor=white" align="left">
<img src="https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white" align="left"><br><br><br>

## Problem Statement 
In this project, we will be implementing a use case of machine learning in the field of Personal Finances and Banking. With this data, we are tasked with predicting whether a person makes more than $50K/year.

## Project Description
#### About the Data
The dataset was taken from the UCI Machine Learning Repository, which extracted the data from the 1994 census database, consisting of 32561 entries with 16 columns. The data stores various kinds of variables, 8 categorical(including the target variable) and 8 numeric variables. The target variable, labelled as "income" consists of 2 class labels, ">50K" and "<=50K". The dataset contains a class imbalance, so performance metrics like F1 score will be profoundly used as a basis to evaluate the estimator models.

<img src="https://github.com/SidhantMathur23/Income-Classification/blob/main/Other/target.PNG" width="450" height="250" align="center">


#### Exploratory Data Analysis
Exploratory data analysis was performed on the dataset, which revealed some patterns in the data. Some of them being:
* The ratio of people having an income "<=50k" to ">50k" gradually decreases as we progress towards the mean, after which the ratio increases again. This means that people in lower age groups (17-35) are more likely to have incomes less than 50k than more. Similarly, people belonging to the age groups (35-60) are more likely to have incomes higher than 50k. 
<img src="https://user-images.githubusercontent.com/79369289/135263343-a99e9985-cbee-4cb6-abe9-feef1f9167ec.png" width="350" height="350" align="center">

* Dataset has a higher concentration of males than females, having a ratio of nearly 2:1. From these genders, nearly 30% of the males earn greater than 50K whereas only about 13% females enjoy an income greater than 50K. 
<img src="https://github.com/SidhantMathur23/Income-Classification/blob/main/Other/gender.PNG" width="300" height="220" align="left">
<img src="https://github.com/SidhantMathur23/Income-Classification/blob/main/Other/gender_dist.PNG" width="300" height="225" align="center">

* It was also uncovered that various categorical features of the dataset stored inconsistent data, specifically, the presence of "?" amongst other values. These values were replaced with np.nan values and treated using DataWig library.


#### Feature Encoding 
After missing value imputation, categorical variables were converted into numerical variables using Catboost. A heatmap of the correlation matrix for the features is shown below to measure the multi-collinearity in the data. Squares having dark purple denote the strength of correlation between the 2 columns.  
<img src="https://github.com/SidhantMathur23/Income-Classification/blob/main/Other/corr.PNG" width="500" height="430" align="center">

#### Feature Transformation 
To measure which transformation works best for our data(standardization or normalization), I have performed the respective transformation and fitted some estimators on the data. The technique yielding higher performance metrics was selected and performed on the data. 

#### Feature Selection
To reduce the dimentionality, I applied Recursive Feature Elimination with Cross Validation(RFECV) and Principal Componenet Analysis on my data.

#### Modelling and Hyperparameter Tuning 
After data preprocessing, I fitted various kinds of estimators on the preprocessed data using scikit-learn and pandas. The algorithms which yielded the best results were passed on to the hyperparameter tuning stage, rest were filtered out. Estimators were evaluated based on Precision, Recall and F1 Score.
<br>
<img src="https://github.com/SidhantMathur23/Income-Classification/blob/main/Other/ROC.PNG" width="400" height="250" align="center">
<img src="https://github.com/SidhantMathur23/Income-Classification/blob/main/Other/PR_ROC.PNG" width="400" height="250" align="center">

* In the paramter tuning stage, I used techniques like RandomizedSearchCV and GridSearchCV to find optimal hyperparamters for the estimator models.

#### Conclusion
From the above stages, I have found Logistic Regression to be most suitable for the dataset, having `Precision` of 0.643, `Recall` of 0.725 and `F1 Score` of 0.682.

## Environment Setup
The project contains several external libraries which are not availible with the stndard anaconda download, these libraries are going to have be downloaded by the user. Navigate to the anaconda prompt and enter the following commands 
```python
pip install datawig
pip install category_encoders
pip install warnings
```

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.python.org" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://scikit-learn.org/" target="_blank"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> </a> </p>

### Credits And Resources
* Dataset was borrowed from https://archive.ics.uci.edu/ml/datasets/Adult?ref=datanews.io
* Kaggle: https://www.kaggle.com/uciml/adult-census-income
* http://jmcauley.ucsd.edu/cse190/projects/sp15/024.pdf
* https://towardsdatascience.com/logistic-regression-classifier-on-census-income-data-e1dbef0b5738

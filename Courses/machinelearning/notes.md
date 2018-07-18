---
layout: page
title: Understanding Machine Learning
permalink: /Courses/machinelearning/
---

# This course is a Pluralsight course taught by David Chappell.

## What is Machine Learning?

- Machine learning is used to find patterns in data and then use those patters to predict future trends.
- Learning requires:
  - Identifying patterns
  - Recognizing those patterns when seen again
- Machine learning in a nutshell
  - Start with a sufficient amount of data with some patterns
  - Then feed that data into a machine learning algorithm to find the patterns in the data
  - This algorithm creates a model which is a piece of code that is able to find patterns when given new data
- What does machine learning require:
  - Lots of data
  - Lots of computation power
  - Effective machine learning algorithms
- R is an open source programming language and environment
  - It supports machine learning, statistical analysis and more

## The Machine Learning Process

- The first problem in the machine learning process is asking the right question.
  - Choose what question to ask.
  - Then make sure you have the right data to answer the question.
  - Do you know how to measure success?

- First choose data to train the machine learning algorithm with.
  - Typically the raw data received is not clean. They may have duplicates or missing pieces.
- To clean up the data, we must first run it through some pre-processing steps.
  - This then provides prepared or clean data.
  - This process is typically repeated more than once until the data is ready.
- Once the prepared data is ready, we can then apply learning algorithms to the data.
  - The result of this step is a candidate model or initial model.
  - This process is repeated several times, so the model is improved over time to a model that provides a sufficient deployable model.
  - This is then the chose model.
- Once the final model is chosen, applications, such as predictors, can make use of the model with new sets of data.

## Machine Learning Concepts

- Terminology
  - Training data - The prepared data that is used to create, or train, a model.
  - Supervised learning - The value you want to predict is in the training data. The data involved is *labelled*.
  - Unsupervised learning - The value you want to predict is not in the training data. The data involved is *unlabeled*.

- Data preprocessing with Supervised Learning
  - The process begins with several data sources with various types of data.
  - This data is then preprocessed and used to create training data.
  - The training data contains features, or columns in the training data. These features are key categories in the data that are used for prediction.
  - Since this is supervised learning, the *target value*, or the data we want to predict, is in the training data.

- Categorizing machine learning problems:
  - Regression
    - Finding a line or curve that best fits a set of data. Essentially just finding a trend in the data.
  - Classification
    - Grouping the data in the dataset in to different classes.
  - Clustering
    - Finding clusters in the dataset which are groups of similar data points.

- Styles of Machine Learning algorithms
  - Decision trees
  - Neural networks
  - Bayesian
  - K-means

- Training a model with supervised learning
  - We being is prepared and cleansed data.
  - The first problem is deciding features to look at through the machine learning algorithm.
  - We then pass 75% of the chosen data for the selected features into the learning algorithm.
  - The learning algorithm then prepares a candidate model.
  - The next problem is to verify if the model is good enough.
  - To check if the model is good enough, we input test data, the remaining 25% of the data points, to the candidate model. Then we compare the target values produced from the candidate model to the actual values from the dataset.
- Improving a model
  - Choosing different features
  - Getting new data
  - Getting more data
  - Modifying some parameters in the algorithm
  - Choosing a completely different algorithm

- Using a model
  - An application can call a model and provide values for the features that the model uses. The model then returns a value that it predicts from the given features.

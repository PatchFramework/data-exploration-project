# Data exploration project: Anime Recommendation Engine
<a href="https://colab.research.google.com/github/PatchFramework/data-exploration-project/blob/main/data_exploration_anime_recommendation.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

## Introduction
This repository is part of the data exploration lecture in our fourth semester. The focus of this project is exploring a anime dataset and using methods learned in the machine learning lecture to develop a recommendation engine.

This project was developed by [Can Berkil](https://github.com/ihatecan), [Canberk Alkan](https://github.com/alkancanberk) and [Dominic Viola](https://github.com/PatchFramework). We used Google Colaboratory as our colaboration tool and as an IDE. This Repository is a backup of our developments on Colab, thats the reason, that all pushs in this repository are from Dominic, even though we developed everything together.

## Motivation
The Motivation to do a recommendation system is rooted in our lecture "[Applied Machine Learning Fundamentals](https://github.com/DaWe1992/Applied_ML_Fundamentals)" from 3. semester. In that lecture concepts and the mathematics behind different ML models were introduced. Especially recommendations were interesting for us, as we come in contact with recommendations on different video and streaming plattforms in our everyday lifes. We combined this passion for recommendations with our passion for animes and decided to do an Anime Recommendation Engine.

## Running the Code
The recommended way to execute the code is via [Google Colab](https://colab.research.google.com/github/PatchFramework/data-exploration-project/blob/main/data_exploration_anime_recommendation.ipynb). You can execute all code cells in the Jupyter Notebook on Google Colab via "Runtime" -> "Run all" in the top left menu. Colab is the recommended way, as it provides a unified environment for every one, so the "it works on my machine" problem can be avoided.

Alternatively:
The code can be downloaded and run locally on a linux based system. The Linux environment is necessary, because bash commands are used to download the dataset and unzip it.

## Structure
The central component of this Repository is [data_exploration_anime_recommendation.ipynb](data_exploration_anime_recommendation.ipynb). In this Jupyter Notebook the main steps of data manipulation and machine learning are explained, but here is a short rundown:

<ol> <!--begin ordered list-->
<li>
Downloading Dataset

In this section the [this](https://www.kaggle.com/CooperUnion/anime-recommendations-database?select=rating.csv) data recommendation dataset is downloaded. As Kaggle doesn't support the download of the dataset without credentials we decided to upload the dataset to our own Google Drive. from there it can be downloaded with the gdown program, which is preinstalled on google colab. Afterwards the dataset is unzipped in an idempotent way, so that it can be re-run without disruptions.
</li>

<li>
Fundamental Dataset Exploration

Basic information about the dataset is gathered, such as the seperator in the two csv files. Also attributes and assumptions about the dataset are expressed here.
</li>
  
<li> 
Data Cleaning

In this step numpy and pandas are used to load the CSV-files into dataframes. The data is then cleaned by removing unwanted features and replacing values such as NaN that make the dataframe prone to errors
</li>

<li>
Data Transformation

The information from the two different CSV-files are combined in a merged dataframe.
</li>
  
<li>  
Advanced Data Exploration

Visualization modules such as seaborn and matplotlib are used. We visualize inherent characteristics of the dataset, such as popularity, frequency of certain features and point out some findings through the visualizations. This should give a understanding of biases as well as problems that may occur when recommending animes.
</li>
  
<li>  
Model selection

The basic principles of recommendation engines are examined in this section. Also it is argued why Matrix Factorization is a good fit for our use-case
</li>
  
<li>
Model Implementation
  
3 different models were implemented: 
  <ol>
    <li>Model 1 with vanilla tensorflow without helper functions for the matrix factorization step</li>
    <li>Model 2 with the tensorflow submodule tensorflow-recommenders, that provides build in helper functions</li>
    <li>Algorithm that uses cosine similarity implemented with scikit-learn</li>
  </ol>

Model 1 uses the tf.gradient_tape() function that can estimate gradients unfortunately this returned gradients of zero in our case. Therefore the model cannot be trained with gradient descent and doesn't work properly.
  
Model 2 uses tensorflow-recommenders classes that are spefically developed with recommendation systems in mind. They provide helper functions that can split a matrix into its factors. After tweaking hyperparameters like learning rate and changing the loss function the model didn't improve its accuracy.
  
The Algorithm uses the cosine similarity metric to determine how similar animes are, based on their name, type and genres. This code is an algorithm rather than a model, as it cannot be trained.
</li>

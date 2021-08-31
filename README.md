##### General Assembly Data Science Immersive Capstone Project

##### Jimmy Radford - August 2021

# Predicting the Prices of London Airbnb Properties

A five-week long personal project on building a machine learning model to predict prices of Airbnb properties in London. The majority of the project was completed as part of a General Assembly London Data Science Immersive course in June 2021, with refinements made in August 2021.

Although the data used for this project is not available in this repository, it can be obtained from its original source at [Inside Airbnb](http://insideairbnb.com/). All code used in the project can be found within the links below.

## Files in This Repository

[Data Cleaning and Feature Engineering](https://github.com/jradford5/GA_capstone_Airbnb_project/blob/main/capstone_airbnb_1_data_cleaning_feature_engineering.ipynb)

[Exploratory Data Analysis](https://github.com/jradford5/GA_capstone_Airbnb_project/blob/main/capstone_airbnb_2_EDA.ipynb)

[Pre-processing, Modelling and Summary](https://github.com/jradford5/GA_capstone_Airbnb_project/blob/main/capstone_airbnb_3_pp_and_modelling.ipynb)

## Objectives

##### Can we predict the prices of Airbnb properties in London using listings data?

 - The goal of this project was to build a regression model that could predict the prices of Airbnb properties in London using the data available on the listings page of the Airbnb website.

- If successful, it could be used to help new hosts in determining a suitable rental price for new properties.

- As a by-product of this objective, I'm also hoping to analyse the attributes that determine the prices of Airbnb properties.

## Data Acquisition

The data was downloaded in csv format from [Inside Airbnb](http://insideairbnb.com/), an organisation that scrapes data from Airbnb's website for properties all over the world. They provide data for property listings, calendars (the future dates that a property is available for), reviews and geographical data for the neighbourhoods that the properties are based in. For this project, I only required the listings and geographical data.

The listings data contains all information related to each property that can be viewed on the Airbnb website, from the text description the host has written about the it to whether the property has Wifi or laundry facilities.

Overall, there were 74 different columns in the dataset that corresponded to 73,364 rows for each Airbnb property in London.

## Data Cleaning

 - To begin with, there were 770,731 null values in the dataset. Some columns were removed completely as they contained too many null values, whereas others had their null values filled in with the column median.

- Columns that would not have been useful for modelling (host_picture_url, last_scraped) or were virtual duplicates of other columns (bathrooms, neighbourhood_group_cleansed) were also dropped from the dataset.

## Feature Engineering

Using the GeoPy library and the latitude and longitude columns within the dataset, I added the following geographical features:

- nearest train or tube station
- the TFL fare zone of the nearest station
- distance from the property in km to the nearest station
- based on the postcode of the property, the average monthly rental price for a one-bedroom flat

Length features were also created for all of the text variables to show how many letters each piece of text value.

## EDA

I performed an extensive exploratory data analysis to attempt to understand the data, its distributions and to look for any correlations within the data. All of the code used and plots created can be found in the [EDA notebook](http://localhost:8888/notebooks/capstone_airbnb_2_EDA.ipynb).

## Modelling

#### Feature Selection

Before preparing the dataset, I selected only features that could be extracted from a new property. This meant removing all columns related to reviews, as a new property obviously wouldn't have any.

#### Train-Test Split

The data was separated 80:20 in to training and test sets to ensure that the model performed well on unseen data.

#### Pre-processing

The following pre-processing steps were applied to the dataset before I began modelling:

- log transformation (linear regression with regularisation models only)
- one-hot encoding
- standardisation

#### Fitting and Scoring Models

The table below details the regression models that were fitted to the dataset, along with the r2 scores for the training and test sets and the mean 5-fold cross-validation score.

![](images/r2_score_comparison.png)


## Evaluation

The best performing model was a bagging regressor, which achieved a cross-validated r2 score of 0.6187.

Below is a comparison of the predicted prices against the true prices in the test set. As the graph shows, the shape of the fit is slightly cloudy, rather than being tight to the red line, which would indicate accurate predictions. Also, the model had a slight tendency to under-predict the prices of the more expensive properties.

![](images/test_set_score_comparison.png)

## Limitations

- Aesthetics aren't taken in to account

One of the biggest limitations of this model, is that it's not able to determine the luxury quality of a property. If a property has expensive furniture or stylish architecture, then the model wouldn't be able to factor that into its predictions.

- Dataset contains a lot of prices that don't match the quality of the apartment

One of the biggest dilemmas I faced was how to deal with properties that had disproportionately low and high prices. In the end, I decided that the most appropriate solution was to a

## Conclusions

I've found this to be a really interesting project and a fun dataset to work with, especially when plotting and feature engineering the geographical variables, but there are a lot of improvements that could improve the model's accuracy.

- include natural language processing for the text variables - they might be able to help the model work out whether a property is expensive or not
- simplify the project by attempting a classification model to predict price categories rather than actual prices
- use neural network models to predict prices
- acquire better Airbnb data, either by paying for it or scraping it directly from their website
- incorporate image recognition in to the project to identify important characteristics in properties' photos

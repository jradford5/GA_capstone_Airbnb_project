##### General Assembly Data Science Immersive Capstone Project

##### Jimmy Radford - June 2021

# Predicting the Prices of London Airbnb Properties

A five-week long personal project on building a machine learning model to predict prices of Airbnb properties in London. This was completed as part of a General Assembly London Data Science Immersive course.

Although the data used for this project is not available in this repository, it can be obtained from its original source at [Inside Airbnb](http://insideairbnb.com/). All code used in the project can be found within the links below.

## Files in This Repository

[insert notebook links here]

## Objectives

##### Can we predict the prices of Airbnb properties in London using listings data?

 - The goal of this project was to build a regression model that could predict the prices of Airbnb properties in London using the data available on the listings page of the Airbnb website.

- If successful, it could be used to help new hosts in determining a suitable rental price for new properties.

- As a by-product of this project, I was also hoping to analyse the attributes that determine the prices of Airbnb properties.

## Data Acquisition

The data was downloaded in csv format from [Inside Airbnb](http://insideairbnb.com/), an organisation that scrapes data from Airbnb's website for properties all over the world. They provide data for property listings, calendars (the future dates that a property is available for), reviews and geographical data for the neighbourhoods that the properties are based in. For this project, I only required the listings and geographical data.

The listings data contains all information related to each property that can be viewed on the Airbnb website, from the text description the host has written about the it to whether the property has Wifi or laundry facilities.

Overall, there were 74 different columns in the dataset that corresponded to 74,840 rows for each Airbnb property in London.

## Data Cleaning

 - There were 798,870 null values across 22 different columns in the dataset. Some columns were removed completely as they contained too many null values, whereas others had their null values filled in with the variable mean.

- Columns that would not have been useful for modelling (host_picture_url, last_scraped) or were virtual duplicates of other columns (bathrooms, neighbourhood_group_cleansed) were also dropped from the dataset.

- Given that there were a lot of columns, I used a separate data dictionary in a csv file to keep track of what actions I needed to take for each of them.

## Feature Engineering

Using the GeoPy library and the latitude and longitude columns within the dataset, I added the following geographical features:

- nearest train or tube station
- the TFL fare zone of the nearest station
- distance from the property in km to the nearest station
- based on the postcode of the property, the average monthly rental price for a one-bedroom flat

Length features were also created for all of the text variables to show how many letters each piece of text value.

## EDA

I performed an extensive exploratory data analysis to attempt to understand the data, its distributions and to look for any correlations within the data. All of the code used and plots created can be found here: [insert link for EDA].

## Modelling

#### Feature Selection

Before preparing the dataset, I selected only features that could be extracted from a new property. This meant removing all columns related to reviews, as a new property obviously wouldn't have any.

#### Train-Test Split

The data was separated 80:20 in to training and test sets.

#### Pre-processing

The following Scikit-learn pre-processing steps were applied to the dataset before I began modelling:

- OneHotEncoder
- StandardScaler
- CountVectorizer

#### Fitting and Scoring Models

The table below details the regression models that were fitted to the dataset, along with the R2 scores for the training and test sets and the mean 5-fold cross-validation score.

[insert table]

## Evaluation

Although the model performed reasonably well for properties priced at under £1000 per night, it struggled to accurately predict the prices of properties that were more expensive.

The graph below shows how the random forests model performed when predicting prices in the test set.

[insert graph]

As you can see, there were several huge residual values, where the model had either under or over predicted the price.

## Limitations

- Aesthetics aren't taken in to account

One of the biggest limitations of this model, is that it's not able to determine the luxury quality of a property. If a property has expensive furniture or stylish architecture, then the model wouldn't be able to factor that into its predictions.

- Computationally expensive

The final dataset contained over 10,000 columns, which meant that it took a very long time to fit a model on. As a result, I wasn't able to run a very extensive grid search.

- Dataset contains a lot of prices that don't match the quality of the apartment

The biggest dilemma I faced was how to deal with properties that had disproportionately high prices. Although the number of such properties was relatively small, they had a big effect of the performance of my model.

## Conclusions

I've found this to be a really interesting project and a fun dataset to work with, especially with plotting and feature engineering the geographical variables, but I feel that I need to make some changes to my approach before I can be happy that this project has reached its potential.

My next steps are the following:

-  revisit the data wrangling part of the project to see if I can come up with a better solution to dealing with the disproportionately high price values
- tweak the parameters for natural language processing - currently the model is giving importance to insignificant words
- look in to applying principal component analysis to the model to reduce the amount of features

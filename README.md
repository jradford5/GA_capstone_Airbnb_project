##### General Assembly Data Science Immersive Capstone Project

##### Jimmy Radford - June 2021

# Predicting the Prices of London Airbnb Properties

A five-week long personal project on building a machine learning model to predict prices of Airbnb properties in London. This was completed as part of a General Assembly London Data Science Immersive course.

Although the data used for this project is not available in this repository, it can be obtained from its original source at [Inside Airbnb](http://insideairbnb.com/). All code used in the project can be found within the links below.

## Files in This Repository

[insert links here]

## Background

[high-level facts about Airbnb London]

## Objectives

1. To build a regression model that can predict the prices of Airbnb properties in London using listings data.
2. Identify the attributes that determine the prices of Airbnb properties.
3. Perform high-level data analysis of Airbnb properties in London.

[needs an extra para either before or after the above points]

## Data Acquisition

The data was downloaded in csv format from [Inside Airbnb](http://insideairbnb.com/), an organisation that scrapes data from Airbnb's website for properties all over the world. They provide data for property listings, calendars (the future dates that a property is available for), reviews and geographical data for the neighbourhoods that the properties are based in. For this project, I only required the listings and geographical data.

The listings data contains all information related to each property that can be viewed on the Airbnb website, from the text description the host has written about the it to whether the property has Wifi or laundry facilities.

Overall, there were 74 different columns in the dataset that corresponded to 74,840 rows for each Airbnb property in London.

## Data Cleaning

There were 798,870 null values across 22 different columns in the dataset. Some columns were removed completely as they contained too many null values, whereas others had their null values filled in with mean values so that the columns could be used as feature variables in my model.

There were also columns that would not have been useful for modelling (host_picture_url, last_scraped) or were virtual duplicates of other columns (bathrooms, nieghbourhood_group_cleansed). These were also dropped from the dataset.

Given that there were a lot of columns, I used a separate data dictionary in a csv file to keep track of what actions I needed to take for each of them.

## Feature Engineering

Here are some of the 

## EDA

[include important EDA plots with explanations of their relevance]

## Models

#### Preparing the Data

[preprocessing steps]

#### Fitting and Scoring Models

[different models used and their results]

## Evaluation

[discuss feature importances and plot of residuals]

## Limitations

## Conclusions

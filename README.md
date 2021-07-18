# Predicting unemployment rates with Twitter sentiment
A recurrent LSTM neural network takes as input weekly US unemployment rates, twitter sentiment scores and covid-19 cases to predict one-week-ahead unemployment rates.

### Objective
With the goal of predicting weekly, state-level unemployment rates in the US, the LSTM takes in as input the past week's rates, state-level Twitter sentiment variable along with new weekly covid-19 cases and covid-19 related deaths:

<img src="https://render.githubusercontent.com/render/math?math=X_{t} =\bigg[y_{t-1}, S_{t-1}, C_{t-1}, D_{t-1}\bigg]">

### Check out the .ipynb notebook file for a full walk-through!

### Twitter data
State-level Twitter data from various major and local news companies were extracted on a weekly basis. News tweets containing the handle of the governor in each state were stored. 

As an example, consider the news tweets in three different weeks of 2020 for New York containing the twitter handle of Governor Andrew Cuomo ([@NYGovCuomo](https://twitter.com/NYGovCuomo)):
![Wordclouds](wordclouds.PNG)

The TextBlot sentiment analysis lexicon was used to compute sentiment scores representing the general sentiment towards the governor in each state. 

### All time-series data
The weekly US unemployment rates and covid-19 data was scraped from [Worldometer](https://www.worldometers.info/coronavirus/usa/) and the [United States Department of Labor](https://oui.doleta.gov/unemploy/claims.asp). The heatmap below represents the data from the first week of **April, 2020**:
![heatmap](heatmap.PNG)

Ultimately, the following four time-series were fed as input data to the LSTM network. The plots below show these time-series data from a few US states.   
![inputTimeseries](inputTimeseries.PNG)

### LSTM predictions
For each state, the LSTM network tries to predict the weekly unemployment rate in that state, <img src="https://render.githubusercontent.com/render/math?math=y_{t}">, the network shows good predictive ability in some states, and completely overshot predictions in other states:
![results](results.PNG)
![moreresults](moreResults.PNG)


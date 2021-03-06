# Predicting unemployment rates with Twitter sentiment
A recurrent LSTM neural network takes as input weekly US unemployment rates, twitter sentiment scores and covid-19 cases to predict one-week-ahead unemployment rates.

### Objective
With the goal of predicting weekly, state-level unemployment rates in the US, the LSTM takes in as input the past week's rates, state-level Twitter sentiment variable along with new weekly covid-19 cases and covid-19 related deaths:

<img src="https://render.githubusercontent.com/render/math?math=X_{t} =\bigg[y_{t-1}, S_{t-1}, C_{t-1}, D_{t-1}\bigg]">

### Check out the [projectNotebook.ipynb](projectNotebook.ipynb) file for a full walk-through!

### Twitter data
State-level Twitter data from various major and local news companies were extracted on a weekly basis. News tweets containing the handle of the governor in each state were stored. 

As an example, consider the news tweets in three different weeks of 2020 for New York containing the twitter handle of Governor Andrew Cuomo ([@NYGovCuomo](https://twitter.com/NYGovCuomo)):
![Wordclouds](wordclouds.PNG)

The TextBlob sentiment analysis lexicon was used to compute sentiment scores representing the general sentiment towards the governor in each state. 

### All time-series data
The weekly US unemployment rates and covid-19 data was scraped from [Worldometer](https://www.worldometers.info/coronavirus/usa/) and the [United States Department of Labor](https://oui.doleta.gov/unemploy/claims.asp). The heatmap below represents the data from the first week of **April, 2020**:
![heatmap](heatmap.PNG)

Ultimately, the following four time-series were fed as input data to the LSTM network. The plots below show these time-series data from a few US states.   
![inputTimeseries](inputTimeseries.PNG)

### LSTM out-of-sample predictions
The LSTM network was trained on data of all but the two latest months. The latest data were treated as test data to provide out-of-sample predictions. 

![results](results.PNG)

For each state, the LSTM network tries to predict the weekly unemployment rate in that state, <img src="https://render.githubusercontent.com/render/math?math=y_{t}">.

The network shows good predictive ability in some states, however it make very poor predictions in states that kept unemployment rates relatively low despite high numbers of covid-19 cases, such as Texas and Florida. 

![moreresults](moreResults.PNG)

### Main take-aways
The recurrent neural network of the LSTM is a powerful tool for predictive time-series modeling, but it has some serious short-comings. 

Lagged variables of weekly unemployment rates, twitter sentiment and covid-19 cases may be used to predict one-week-ahead unemployment rates in US states, however it may prove difficult to explain the variability in predictive performance within some states. I would NOT recommend the LSTM for this task, however feel free to replicate this project for fun or educational purposes.

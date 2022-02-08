<img src="https://user-images.githubusercontent.com/42075039/152980331-b1636072-27b8-4311-9064-3cc0b380b1d8.jpg" width="600" height="300">

# Predict rental duration time for ‘Ddareungi’ Seoul's bikes shearing system
The goal of this project is to predict the rental duration time for bikes shearing system, using machine learning regression models: Linear regression, Decision tree and KNN.

### Background:

- Started at 2015 and today has more than 20,000 bikes at 1,500 locations in city.
- The service usage is doubling each year, with 52,000 daily rentals and more then 3M users as of this year (2021).
- Bikes rental options and policy: 1 hour, 2 hours or Daily use, with a penalty surcharge for every 5 min delay returning the bike.

### Objective:
Trip duration is the most fundamental measure in all modes of transportation. Predicting the trip-time precisely is crucial for advanced Intelligent Transport Systems (ITS) and traveler information systems.



## Data source:
Kaggle - Original data from the bike sharing system + local weather information: 

 - https://www.kaggle.com/saurabhshahane/seoul-bike-trip-duration-prediction


## EDA process:
1.3GB csv file with 9,601,139 records and 24 columns
- Used ‘datatable’ library to speed up data loading.
- Dropped columns: with same data, ones highly correlated and others which did not seam to be of value predicting the rental duration.
- Worked with a sample of data (5%) for time process consideration.
- Searched for outliers using histograms and pairplot correlations and removed them by setting proper thresholds.

## Feature engineering:
- Created a new column ‘speed’ using ‘duration’ and ‘distance’ columns. This helped identify outliers with unreasonable speed values.
- Created bins for 3 weather related columns and categorized them (OrdinalEnc)
Final dataset: 9,510,763 records (1% drop) and 12 columns

## Data analysis:
1. Duration is higher on weekends days.
<img src="https://user-images.githubusercontent.com/42075039/152979055-0b74bfc2-b519-455c-800a-7a5d74f55c3c.png" width="600">
2. Duration drops during traffic rush hours,  picks up during the day and again in the evening hours.
<img src="https://user-images.githubusercontent.com/42075039/152979135-226f1c50-ad66-4fce-be02-536762dd75dc.png" width="600">
3. There is a relation between duration and weather element such as temperature.
<img src="https://user-images.githubusercontent.com/42075039/152979208-aaea1af3-4a40-4082-917e-1115fb41216e.png" width="600">
4. We notice a behavior pattern for renters corresponding with rental periods policy for first and second hours (returning bikes).
<img src="https://user-images.githubusercontent.com/42075039/152979263-00465e6b-24c7-4b5c-8cf4-8ddc6cc96825.png" width="600">

## Models' performance:
Many ‘runs’ were made for each model changing parameters and hyper-parms:
- Using default model’s parameters.
- Changing bins sizes and removing them.
- Using deferent scalars for features.
- Setting user defined metric function for KNN.

## Results and conclusions:
- Adding bins helped improving model results.
- Changing original scalar from MinMax to MaxAbs helped the model.
- User defined function for KNN metrics didn’t improve the model.
- The data potentially has more “outliers” which affects the model accuracy.

** Scoring criteria: RMSE

<img src="https://user-images.githubusercontent.com/42075039/152979951-7c94b386-7130-44b6-9318-444d86ff5f6c.png" width="500">

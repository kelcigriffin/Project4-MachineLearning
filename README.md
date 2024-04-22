# Project4-MachineLearning
Project 4: Using Machine Learning to predict housing trends in the city of Chicago

## Background:
We decided that it would be interesting to apply machine learning techniques to uncover hidden trends in the housing market. Specifically, we were interested in using location socioeconomic factors in housing price predictions, and trying to discover which factors had the greatest impact on price. 

## Data:
The main source of data used for this project was the Cook County Assessors office, more specifically the home sale and parcel datasets that can be found at https://datacatalog.cookcountyil.gov/Property-Taxation/Assessor-Archived-05-11-2022-Residen[…]%20%2275%22%2C%20%2276%22%2C%20%2277%22%29/page/filter and https://datacatalog.cookcountyil.gov/Property-Taxation/Assessor-Archived-05-31-2023-Parcel-Universe/tx2p-k2g9/explore

First, using the tools provided on the website, the data was filtered by town code to narrow the dataset to the chicagoland area (town codes 70-77). Some unnessesary columns were then dropped before the downloaded. Then, the data was downloaded as a CSV. The sale data was small enough to be downloaded in one piece, but eight separate downloads had to be done for the parcel data based on town code because the files were so large. The large file also presented issues in the cleaning stage.

Data Preparation:
The sale data and the first of the parcel data was imported. An inner join was conducted between the sale data and the parcel data on pin number, and the result was saved to a new dataframe. This process was repeated for the remaining 7 portions of parcel data. The resulting eight dataframes were then concatanated into a single much smaller dataframe that was ready for additional cleaning steps.

This dataframe was then exported and imported into a different Python file, where more unneeded columns were dropped. It was decided to narrow the datset further by only focusing on housing sales in 2018 and 2019. This produced a dataframe that was much smaller and more managable to use in subsequent steps. The datatypes for each of the rows were then casted, and the clean dataset was exported as a CSV and can be found in this repo (data_cleaned.csv)

## Kyle Random Forest Model

The data was imported into the Kyle Random Forest Jupyter notebook. Rows with NaN values were then dropped, and some additional columns were removed. I decided to drop rows with sale price < 100000 since there were a lot of homes sold for $1, which is not realistic. Dummy variables were obtained for any columns with catagorical data, sale price column was made the y value, and the x dataset was the remaining dataframe. The data was then split into testing and training sets,scaled, and a Random Forest Regressor was run with 200 estimators. The model had a mean absolute error of 93028, and a root mean absolute error of 183898. This is less then ideal, as $90,000 is a significant difference in price. However, on closer inspection, there are a lot of houses that the model predicted very well, but a few where the model was extremely off.

## Kelci Random Forest

## Connor Random Forest

## Javascript Visualization

## Kyle Classification Model

The data was imported into the Kyle Random Forest Jupyter notebook. Rows with NaN values were then dropped, and some additional columns were removed. I decided to drop rows with sale price < 100000 since there were a lot of homes sold for $1, which is not realistic. Dummy variables were obtained for any columns with catagorical data. A new calculated column was created to find the difference between the sale price and the estimated total price. From this, a boolean column "Sale Outcome" was created where any houses whose sale price exceeded the estimated price recieved a 1, and any sale price that didn't recieved a 0. The Sale Outcome column was made the y column, with the x value being all other chosen columns. A logistic regression model was run with 20000 iterations, and the predicted values for the testing dataset were compared to the true testing dataset. The model had an accuracy of 72%, but this is misleading because the model was okay at predicting cases where the predicted price exceeded the sales price, with a precision of 72% and a recall of 99%. However, for predicting cases where the sales price exceeded the predicted price, the model performed abysmally with a precison of 26% and a recall of .01. Thus, it can be concluded that this model is completely ineffective in predicting differences between estimated price and sale price.

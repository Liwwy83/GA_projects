# Project 2 - Ames Housing Data and Kaggle Challenge

## Problem Statement
In this project, we will understand the features that affect the Sale Price of housing in Ames, Iowa. We aim to find a production model that we can use to get a good score on Kaggle, as well as find business insights on what helps to increase Sale Price.

## Features Selected
Using correlation coefficient above 0.4 as the main guideline and transforming the ordinal and nominal features appropriately, the following features were selected.

|Type|Number|Features|
|---|---|---|
|Values|8|Total_Bsmt_SF, Gr_Liv_Area, Garage_Area, Year_Built, Year_Remod/Add, Mas_Vnr_Area, Full_Bath, BsmtFin_SF_1|
|Ordinal|8|Overall_Qual, Exter_Qual, Bsmt_Qual, Kitchen_Qual, Fireplace_Qu, Garage_Finish, Bsmt_Exposure, Heating_QC|
|Nominal|4|MS_SubClass, Foundation, Garage_Type, Neighborhood (split into High and Low)|

## Model Selected
Using Linear Regression, LassoCV and RidgeCV, we fit the above features with no scaling, using Standard Scaler and using Power Transform.

We found that the Linear Regression with Power Transform gave the best R2 and RMSE scores.
### Kaggle Scores
|Scaling Method|None|Standard Scaler|Power Transform|
|---|---|---|---|
|Private|24813.43949|25191.36174|23599.10771|
|Public|31111.93853|31358.58896|29682.66232|

### Top Features with Largest Effect on Sale Price
|Scaling Method|None|Standard Scaler|Power Transform|
|---|---|---|---|
|Top|Neighborhood_High|Gr_Liv_Area|Gr_Liv_Area|
|Second|Kitchen_Qual|Overall_Qual|Overall_Qual|
|Third|Overall_Qual|BsmtFin_SF_1|Total_Bsmt_SF|

We ignore the results from no scaling as it is inappropriate for our dataset with large variation in magnitudes of the raw values of different features. The top 2 features are Gr_Liv_Area and Overall_Qual.

- For every 1 square foot increase in Gr_Liv_Area, SalePrice is expected to increase by around $13.65.
- For every 1 point increase in Overall_Qual, SalePrice is expected to increase by around $1925.19

## Conclusion
To improve the chances of commanding a higher sale price, a house owner may wish to 
- increase to living area above ground 
- get a higher score in overall quality by using better material and having better finishing
- work on the basement to increase the area and exposure
- increase the garage area

For a house-hunter looking for a better deal, he might wish to avoid the 3 neighborhoods of Brookside, Northridge and Northridge Heights which command higher sale prices than the other neighborhoods in Ames. 
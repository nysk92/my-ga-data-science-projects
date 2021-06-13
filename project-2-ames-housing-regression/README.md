# Project 2 - Ames Housing Data and Kaggle Challenge


## Problem Statement

The problem to be solved is to accurately predict housing prices given data about property attributes of previous property transactions. Specific to this challenge, the data is of house sale transactions of Ames, Iowa. 

Success will entail being able to select and appropriately transform the most important features in the dataset, and to train and tune a regression model to make accurate predictions on sale prices. In doing so, interpreting the models will allow us to see how different features of a house may affect the sale price. 

The learnings could be useful for home purchasers or investors to udnerstand how to fairly valuate a house. Such a study could also be a good way to understand a particular city's property market. Although certain attributes in the Ames property data might not be applicable to any city or town in the world, especially the particularities of the neighborhoods, many of this attributes would be relevant in valuating property anywhere, such as the amount of space, quality of finishing and amount of rooms.

More details about the challenge can be found [on this Kaggle page](https://www.kaggle.com/c/dsi-us-6-project-2-regression-challenge/overview).



## Notebooks

This is the notebook structure of the project. 

1. [Notebook 1](../project-2-ames-housing-regression/code/01_EDA_and_Cleaning.ipynb): Data Cleaning and EDA
2. [Notebook 2](../project-2-ames-housing-regression/code/02_Preprocessing_and_Feature_Engineering.ipynb): Preprocessing and Feature Engineering
3. [Notebook 2a](../project-2-ames-housing-regression/code/02a_Preprocessing_Test_Set.ipynb): Preprocessing Test Set
4. [Notebook 3](../project-2-ames-housing-regression/code/03_Models_and_Conclusions.ipynb): Models and Conclusions
5. [Notebook 3a](../project-2-ames-housing-regression/code/03a_Model_Baselines.ipynb): Baseline and QUick Lightweight Models

EDA and data cleaning will be done in Notebook 1. Thereafter, a first cut of cleaned data will be saved and used in Notebook 2 for feature engineering. 

The finalised features will be saved in the Notebook 2 code and loaded for use to train and evaluate models in Notebook 3 and 3a. Notebook 2a does the transformations from Notebook 2 on the test data, preparing it for Kaggle evaluation. 

Main modelling work and conclusions are found in Notebook 3. Notebook 3a is just used to quickly compute lightweight models.



## Data

The original train and test data files and the prediction submissions are located in the [kaggledata folder](../project-2-ames-housing-regression/kaggledata).

The original <code>train.csv</code> and <code>test.csv</code> are cleaned and processed, with features being dropped or new features being created/transformed. Interim data files are saved in the [datasets folder](../project-2-ames-housing-regression/kaggledata), which also contains the fully processed training and test sets, <code>f_train.csv</code>  and <code>f_test.csv</code> respectively.




## Feature Selection


The feature sets used for different models are called <code>features_max</code>, <code>features_max_powerless</code>, <code>features_drop_weak</code>, <code>features_lite</code> and <code>features_min</code>.
The [features folder](../project-2-ames-housing-regression/features) contains organised information on the features, refer to <code>features.csv</code> to specifically see which features belong to each feature set.

### Data Dictionary

This is a data dictionary of the features eventually used for the models. The data dictionary of features from the raw data can be found [here](https://www.kaggle.com/c/dsi-us-6-project-2-regression-challenge/data) and with more details [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).
The variable types are continuous (cont), discrete (dis), binary meaning 1 or 0 (bin), and ordinal (ord).

| feature                    | data type   | var type   | description                                                                                     | raw feature                                          | features max   | features max powerless   | features drop weak   | features lite   | features min   |
|:---------------------------|:------------|:-----------|:------------------------------------------------------------------------------------------------|:-----------------------------------------------------|:---------------|:-------------------------|:---------------------|:----------------|:---------------|
| Lot Frontage               | float64     | cont       | Linear feet of street connected to property                                                     | Lot Frontage                                         | Y              | Y                        | Y                    | N               | N              |
| Lot Area                   | int64       | cont       | Property lot size in square feet.                                                               | Lot Area                                             | Y              | Y                        | Y                    | N               | N              |
| Overall Cond               | int64       | ord        | Overall condition rating of house.                                                              | Overall Cond                                         | Y              | Y                        | N                    | N               | N              |
| Year Built                 | int64       | dis        | Original construction date.                                                                     | Year Built                                           | Y              | Y                        | Y                    | Y               | N              |
| Year Remod/Add             | int64       | dis        | Remodel or construction date.                                                                   | Year Remod/Add                                       | Y              | Y                        | Y                    | Y               | N              |
| Mas Vnr Area               | float64     | cont       | Masonry veneer area in square feet.                                                             | Mas Vnr Area                                         | Y              | Y                        | Y                    | Y               | N              |
| Total Bsmt SF              | float64     | cont       | Total basement area in square feet.                                                             | Total Bsmt SF                                        | Y              | Y                        | Y                    | N               | N              |
| 1st Flr SF                 | int64       | cont       | First floor area in square feet.                                                                | 1st Flr SF                                           | Y              | Y                        | Y                    | Y               | N              |
| 2nd Flr SF                 | int64       | cont       | Second floor area in square feet.                                                               | 2nd Flr SF                                           | Y              | Y                        | Y                    | N               | N              |
| Low Qual Fin SF            | int64       | cont       | Low quality finished area on all floors in square feet.                                         | Low Qual Fin SF                                      | Y              | Y                        | N                    | N               | N              |
| Bedroom AbvGr              | int64       | dis        | Bedrooms above grade.                                                                           | Bedroom AbvGr                                        | Y              | Y                        | Y                    | N               | N              |
| Kitchen AbvGr              | int64       | dis        | Kitchens above grade.                                                                           | Kitchen AbvGr                                        | Y              | Y                        | Y                    | N               | N              |
| TotRms AbvGrd              | int64       | dis        | Total rooms above grade.                                                                        | TotRms AbvGrd                                        | Y              | Y                        | Y                    | Y               | N              |
| Fireplaces                 | int64       | dis        | Number of fireplaces.                                                                           | Fireplaces                                           | Y              | Y                        | Y                    | Y               | N              |
| Garage Area                | float64     | cont       | Garage size in square feet.                                                                     | Garage Area                                          | Y              | Y                        | Y                    | Y               | N              |
| Wood Deck SF               | int64       | cont       | Wood deck area in square feet.                                                                  | Wood Deck SF                                         | Y              | Y                        | Y                    | N               | N              |
| Open Porch SF              | int64       | cont       | Open porch are in square feet.                                                                  | Open Porch SF                                        | Y              | Y                        | Y                    | N               | N              |
| Enclosed Porch             | int64       | cont       | Enclosed porch area in square feet.                                                             | Enclosed Porch                                       | Y              | Y                        | Y                    | N               | N              |
| 3Ssn Porch                 | int64       | cont       | Three season porch area in square feet.                                                         | 3Ssn Porch                                           | Y              | Y                        | N                    | N               | N              |
| Screen Porch               | int64       | cont       | Screen porch area in square feet.                                                               | Screen Porch                                         | Y              | Y                        | Y                    | N               | N              |
| Pool Area                  | int64       | cont       | Area of pool in square feet.                                                                    | Pool Area                                            | Y              | Y                        | N                    | N               | N              |
| Misc Val                   | int64       | cont       | Value of misc features.                                                                         | Misc Val                                             | Y              | Y                        | N                    | N               | N              |
| Mo Sold                    | int64       | dis        | Month sold.                                                                                     | Mo Sold                                              | Y              | Y                        | N                    | N               | N              |
| Yr Sold                    | int64       | dis        | Year sold.                                                                                      | Yr Sold                                              | Y              | Y                        | N                    | N               | N              |
| After 1999                 | int64       | bin        | Whether the house was built from 2000 onwards.                                                  | Yr Sold                                              | Y              | Y                        | Y                    | Y               | N              |
| PID 9                      | int64       | bin        | Whether Parcel ID begins with '9'.                                                              | PID                                                  | Y              | Y                        | Y                    | N               | N              |
| Bath Log                   | float64     | cont       | The logged value of the weighted sum of bathrooms, with basement bathrooms getting less weight. | Full Bath, Half Bath, Bsmt Full Bath, Bsmt Half Bath | Y              | Y                        | Y                    | Y               | N              |
| Floating Village           | int64       | bin        | Whether the zoning classification is floating village.                                          | MS Zoning                                            | Y              | Y                        | Y                    | N               | N              |
| Regular Lot Shape          | int64       | bin        | Whether the lot shape is regular.                                                               | Lot Shape                                            | Y              | Y                        | Y                    | N               | N              |
| Hillside                   | int64       | bin        | Whether land contour is hill sloped.                                                            | Land Contour                                         | Y              | Y                        | Y                    | N               | N              |
| CulDSac                    | int64       | bin        | Whether the lot is at a cul de sac.                                                             | Lot Config                                           | Y              | Y                        | Y                    | N               | N              |
| NH1                        | int64       | bin        | Whether the house is in NH 'IDOTRR' or 'MeadowV'.                                               | Neighborhood                                         | Y              | Y                        | Y                    | N               | N              |
| NH2                        | int64       | bin        | Houses in neither NH1, NH3, N4 nor 'GrnHill'.                                                   | Neighborhood                                         | Y              | Y                        | Y                    | Y               | N              |
| NH3                        | int64       | bin        | Whether the house is in 'Blmngtn', 'Somerst', 'Timber' or 'Veenker'.                            | Neighborhood                                         | Y              | Y                        | Y                    | N               | N              |
| NH4                        | int64       | bin        | Whether the house is in 'Greens', 'NoRidge', 'NridgHt', or 'StoneBr'.                           | Neighborhood                                         | Y              | Y                        | Y                    | Y               | N              |
| 1 Story                    | int64       | bin        | Whether the house is single story or not.                                                       | House Style                                          | Y              | Y                        | N                    | N               | N              |
| Hip Roof                   | int64       | bin        | Whether the roof style is hip roof or not.                                                      | Roof Style                                           | Y              | Y                        | Y                    | N               | N              |
| Stone Vnr                  | int64       | bin        | Whether the veneer is stone or not.                                                             | Mas Vnr Type                                         | Y              | Y                        | Y                    | N               | N              |
| Has Vnr                    | int64       | bin        | Whether there is a masonry veneer or not.                                                       | Mas Vnr Type                                         | Y              | Y                        | Y                    | Y               | N              |
| Exter Qual Num             | int64       | ord        | Quality level of exterior materials, 2 for Gd/Ex, 1 for average, 0 for the rest.                | Exter Qual                                           | Y              | Y                        | Y                    | Y               | N              |
| PConc Foundation           | int64       | bin        | Whether house foundation is of poured concrete.                                                 | Foundation                                           | Y              | Y                        | Y                    | Y               | N              |
| Has Central Air            | int64       | bin        | Whether house has central air conditioning.                                                     | Central Air                                          | Y              | Y                        | Y                    | N               | N              |
| Excellent Heating          | int64       | bin        | Whether house has excellent quality heating.                                                    | Heating QC                                           | Y              | Y                        | Y                    | Y               | N              |
| Kitchen Qual Num           | int64       | ord        | Quality level of kitchen, 2 for Ex, 1 for Gd, 0 for the rest.                                   | Kitchen Qual                                         | Y              | Y                        | Y                    | Y               | N              |
| Fireplace Qu Num           | int64       | ord        | Quality level of fireplace, 2 for Ex, 1 for Gd, 0 for the rest.                                 | Fireplace Qu                                         | Y              | Y                        | Y                    | Y               | N              |
| Attached or BuiltIn Garage | int64       | bin        | 1 if the house has an attached or built-in garage, else 0.                                      | Garage Type                                          | Y              | Y                        | Y                    | Y               | N              |
| Finished Garage            | int64       | bin        | Whether the garage is finished (including roughly finished).                                    | Garage Finish                                        | Y              | Y                        | Y                    | Y               | N              |
| Fully Paved Drive          | int64       | bin        | Whether drive is fully paved.                                                                   | Paved Drive                                          | Y              | Y                        | Y                    | N               | N              |
| New Sale                   | int64       | bin        | Whether the sale type of the house was of a new house.                                          | Sale Type                                            | Y              | Y                        | Y                    | N               | N              |
| Has Alley Access           | int64       | bin        | Whether the property has alley access.                                                          | Alley                                                | Y              | Y                        | Y                    | N               | N              |
| 1.5P Gr Liv Area           | float64     | cont       | Above grade square feet living area value to the power of 1.5.                                  | Gr Liv Area                                          | Y              | N                        | Y                    | Y               | N              |
| 1.5P Total SF              | float64     | cont       | Above and below grade living area value in square feet to the power of 1.5.                     | Gr Liv Area, Total Bsmt SF                           | Y              | N                        | Y                    | Y               | Y              |
| P3 Overall Qual            | int64       | dis        | Overall material and finish quality rating raised to power of 3.                                | Overall Qual                                         | Y              | N                        | Y                    | Y               | Y              |




## Model Evaluation

The processed train set went through a split into train and validation sets.
Each different feature set was fit and transformed with the train set on Linear Regression, Lasso Regression (with LassoCV) and Ridge Regression (with RidgeCV). The non-binary numeric features went through standard scaling for Ridge and Lasso models.

Models were evaluated with R-Squared and Root Mean Square Error (RMSE) metrics. The scores for predicting on the train set, with a mean cross-validation score for RMSE on the train set, and scores for prediction on the validation set were compared to assess for  bias and overfitting.

The first feature set, <code>features_max</code>, showed the most promising performance. A logarithmic transformation of target variable was tried out for the models of that feature set to see if that would further improve performance, but it did not.



### Table of Evaluated Models

|    |   model_group | model_type        | model_params   |   train_R2 |   train_RMSE |   val_R2 |   val_RMSE | comments                                       |   features | feature_set            |
|---:|--------------:|:------------------|:---------------|-----------:|-------------:|---------:|-----------:|:-----------------------------------------------|-----------:|:-----------------------|
|  0 |             1 | Linear Regression |                |       0.92 |      24482   |     0.91 |    23708   |                                                |         53 | features_max           |
|  1 |             1 | Lasso             | alpha=67.09    |       0.91 |      23275.3 |     0.9  |    24193.3 |                                                |         53 | features_max           |
|  2 |             1 | Ridge             | alpha=1.0      |       0.92 |      23078   |     0.9  |    23869.4 |                                                |         53 | features_max           |
|  3 |             2 | Linear Regression |                |       0.89 |      26621.2 |     0.88 |    26424.2 | Non-CV R2 on train set is 0.9.                 |         53 | features_max_powerless |
|  4 |             2 | Lasso             | alpha=65.87    |       0.9  |      25427.7 |     0.88 |    26713.2 | max_iter = 10000                               |         53 | features_max_powerless |
|  5 |             2 | Ridge             | alpha=10.0     |       0.9  |      25405.1 |     0.88 |    26575.5 |                                                |         53 | features_max_powerless |
|  6 |             3 | Linear Regression |                |       0.9  |      25433   |     0.9  |    24795.5 | Non-CV R2 on train set is 0.91.                |         45 | features_drop_weak     |
|  7 |             3 | Lasso             | alpha=117.24   |       0.91 |      24342.2 |     0.89 |    25283   | max_iter = 1000                                |         45 | features_drop_weak     |
|  8 |             3 | Ridge             | alpha=1.0      |       0.91 |      24068.2 |     0.9  |    24910   |                                                |         45 | features_drop_weak     |
|  9 |             4 | Linear Regression |                |       0.88 |      27353.2 |     0.89 |    25224.9 | Non-CV R2 on train set is 0.89.                |         24 | features_lite          |
| 10 |             4 | Lasso             | alpha=67.09    |       0.89 |      26751.6 |     0.89 |    25425   | max_iter = 1000                                |         24 | features_lite          |
| 11 |             4 | Ridge             | alpha=1.0      |       0.89 |      26714.6 |     0.89 |    25297.3 |                                                |         24 | features_lite          |
| 12 |             5 | Linear Regression |                |       0.83 |      32166.2 |     0.84 |    30618.2 | Non-CV R2 on train set is 0.84.                |          2 | features_min           |
| 13 |             5 | Lasso             | alpha=71.94    |       0.84 |      31964.5 |     0.84 |    30622.3 | max_iter = 1000                                |          2 | features_min           |
| 14 |             5 | Ridge             | alpha=1.0      |       0.84 |      31964.4 |     0.84 |    30619.6 |                                                |          2 | features_min           |
| 15 |             1 | Linear Regression |                |       0.93 |      22813.1 |     0.9  |    24442.4 | Logarithmic transformation of target variable. |         53 | features_max           |
| 16 |             1 | Ridge             |                |       0.93 |      21208.7 |     0.9  |    24779.1 | Logarithmic transformation of target variable. |         53 | features_max           |


The baseline performance is a RMSE of 77233.34, which is calculated based on making all prediction as the mean sale price. All the models evaluated beat the baseline.

Overall, the two most promising models were the Linear Regression and Ridge Regression with <code>features_max</code>. These two models were trained on the full training set (including the validation). These two models had their mean five-fold-cross-validated RMSE scores evaluated. The Linear Regression model had a slightly better cross-validated score of 24126.51 and better non-cross-validated score of 22883.38 compared to 24264.45 (cv) and 22995.80 respectively of the Ridge model. However, this indicates that the Ridge model would generalise better to unseen data given that its cross-validated score was more consistent with the non-cross-validated score, and performed only slight worse that the Linear Regression model's cv score.

For this reason, the Ridge model was selected to be the model for the Kaggle test set prediction and submission.

### Kaggle Submitted Model

The RMSE for the Ridge model with <code>features_max</code> was 24727.75. This score is close to the cross-validated score of the Ridge model on the training data, which indicates that this model generalises decently to unseen data in predicting prices.


## Conclusion and Recommendations

1. The key features that, based on the Ames housing data, add most value to a home are its total area, high finishing quality, and year last renovated or built. This makes sense as larger, better finished, and newer homes would garner higher prices. 


2. Having a lot of poorly finished areas can hurt the pricing of the house a lot. This can either be an opportunity for buyers to get bargains (they can simply spend some money to renovate after getting a bargain). 


3. Likewise, it would be helpful to sellers that they make sure their hosues are touched up before going on the market if they wish to fetch a good price. Renovating to get a higher quality house finishing might be worth the capital for the potential increase in sale price.


4. In Ames, Neighborhood Class 3 (NH3) of Bloomington, Somerset, Timberland, and Veenker could prove to be good investments. For their average relatively high finishing quality, they are negatively related to sale price compared to the most expensive tier of neighborhoods. The data is about a decade outdated, so this might not be the case today.


5. Although pool size featured as strongly positively predictive for the Ames properties, this might not always hold true. For example, in hot areas such as in Calfornia and Nevada where a pool in the house is a necessity instead of a luxury, the correlation might not be so strong. The reverse could be true of cities where pools are an expensive luxury due to scarcity of land such as in New York City or Singapore, and pool size could be highly indicative of a high property price. 


6. Other attritubes of the Ames data that might not generalise to other cities, apart from the obvious neighborhood and parcel IDs, are location attributes such as being on a hill. In some cities, being situated on a gradient could be associated with being in an expensive neighbourhood (e.g. The Peak in Hong Kong or Mulholland Drive in Los Angeles). If this prediction task were to be on other cities, some additional work would be needed to segment the neighborhoods. We could use a similar approach of this project by trying to segment based on quality of house finishings and price per square foot. However, location attributes such as land contours could still be relevant, but would be interpreted differently.


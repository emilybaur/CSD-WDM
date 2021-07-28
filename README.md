# CSD-WDM 

**Version 1.0**

Python-based (v3.8.5) Water Demand Model

## Description

The Climate-Supply-Development Water Demand Model takes in monthly features to identify the key per-capita water demand 'drivers'. During model calibration, the training process evaluates feature correlation with observed gallons per-capita water use (gpcd), checks for feature collinearity and removes the lesser demand correlated co-linear feature, and performs recursive feature elimination to identify key demand drivers and optimize model accuracy in predicting water demand.

## Getting Started

Access the module here:

** link to .py file and template **

### Prerequisites

The following are modules used in the model that are not downloaded automatically with python.

* Progressbar

## Usage

### Loading Data

The user will provide two sets of data: training data and testing data.

Testing data will include data from three years: one drought year, one average year, and one surplus year.

Training data will include data from all years besides those selected as the testing data. Training data should not be less than 30 years.

Training data and testing data files should each contain an excel file for each month. Excel files should have features listed along the top as column titles and years listed along the left side as row titles. These excel files will be loaded into a python dictionary format with the help of the provided template.

Features may include:

| Feature | Suggested Units | Label |
| --- | --- | --- |
| Mean daily temperature | °C |
| Monthly precipitation | mm | 
| Monthly snowfall | mm |  Apr_snow_in &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Mar_snow_in &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; etc |
| Yearly snowfall | mm | Total_snow_in |
| Snow shortage | mm | Snow_shortage |  
| Housing | units | Housing |
| Population density | people / sq mile |  HousingDensity |
| Streamflow of major streams | acre-feet |
| Conservation goal | gpcd | cons_goal |
| Mean monthly per capita water demand | gpcd | Target_gpcd |

**  Target_gpcd is a required feature ** 

The user will also load a folder with files containing all the data together (including population data and Target_gpcd values) for calculating average demand by month.

### Model Input

The following are inputs used within in the model:

* Scoring is used to assess the fit of the model to the testing data. As of now, either the R squared method or Root Mean Square Error method can be used in the model.

* Snow data and set conservation goals may be used in the data files if relevant for the area of interest, but must be set to False if not provided in the excel data.

* Correlation threshold is the limit (number between 0 and 1) to be used when examining the relationship between a feature and the target. A range of values to test exists in the model template, but may be edited if desired.

* Collinearity threshold is the limit (number between 0 and 1) to be used when examining the relationship between two features. This threshold is used to remove a feature with the weaker correlation. A range of values to test exists in the model template, but may also be edited if desired.

**Possible Inputs**

| Name of Input | Choices | Enter in template |
| --- | --- | --- |
| **Scoring** | R squared | 'R2' |
| | Root Mean Square Error | 'RMSE' |
| **Snowfeatures** | Use snowfall data | [True, False] |
| | Don't use snowfall data | [False] |
| **Conservation** | Use conservation goal | [True, False] |
| | Don't use conservation goal | [False] |

## Contributers


# Selecting a Location for Oil Well

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![Python](https://img.shields.io/badge/python-3.8%2B-blue)

A project for selecting the most suitable region for developing oil wells using machine learning models to predict oil volumes, analyze potential profits, and assess risks.

## Table of Contents
- [Objective](#objective)
- [Research Plan](#research-plan)
- [Steps to Select a Location](#steps-to-select-a-location)
- [Task Conditions](#task-conditions)
- [Data Description](#data-description)
- [Overall Conclusion](#overall-conclusion)
- [Authors](#authors)
- [License](#license)

## Objective
The objective of this research is to select the most suitable region for developing oil wells. It is necessary to build a machine learning model that can predict the volume of oil in each well and analyze the potential profit and risks associated with the development of each region. The main goal is to choose the region that will bring maximum profit with minimal risk.

## Research Plan

1. **Loading and Preparing Data**:
   - Load data for three regions.
   - Split data into training and validation sets in a 75:25 ratio.

2. **Training the Model for Each Region**:
   - Train a linear regression model on each region.
   - Make predictions on the validation set and save the results.
   - Evaluate the model's quality using the mean of predictions and RMSE metric.

3. **Preparing for Profit Calculation**:
   - Calculate the minimum oil volume for break-even development.
   - Compare the average oil volume in each region to the break-even level.

4. **Profit Calculation**:
   - Select 200 wells with the highest predicted oil volumes for each region.
   - Calculate the total oil volume and profit for each group of wells.

5. **Risk Analysis**:
   - Apply the Bootstrap technique to estimate the profit distribution and risks.
   - Determine the average profit, confidence interval, and probability of losses.

6. **Conclusion**:
   - Draw conclusions about choosing the region with the highest average profit and minimal risks.

## Steps to Select a Location

1. Collect data on well characteristics in each region (oil quality and reserve volume).
2. Build a model to predict the volume of oil reserves.
3. Select 200 wells with the highest predicted volumes.
4. Calculate the total profit from the selected wells.
5. Analyze the risks and determine the region with the highest potential profit.

## Task Conditions

1. Only linear regression is used to train the model.
2. Each region has 500 wells, of which 200 are selected for development.
3. The budget for development is 10 billion rubles.
4. The profit per barrel of oil is 450 thousand rubles.
5. It is necessary to select a region where the probability of losses is less than 2.5%.

## Data Description

- **id** — unique well identifier.
- **f0, f1, f2** — three features characterizing the well (e.g., physical or chemical parameters).
- **product** — volume of oil in the well (in thousands of barrels).

The data is presented for three regions, and it is necessary to determine in which region development will be most profitable.

## Overall Conclusion

In the course of the research, a machine learning model was developed to determine the most profitable region for oil extraction. The analysis conducted using the Bootstrap method allowed for the following conclusions:

### Recommended Region for Development — Region 2:

- **Low risk of losses**: only 0.2% (compared to 2.6% in the first region and 2.8% in the third region).
- **Expected average profit**: approximately 632 million (versus 615 million in the first region and 572 million in the third region).

### Research Stages

1. **Loading and Preparing Data**:
   - Imported necessary libraries and loaded three datasets: `first_geo`, `second_geo`, `third_geo`.
   - Created the function `get_info` to check data: verified data types, identified and removed implicit duplicates, and confirmed the absence of missing values and explicit duplicates.
   - Removed implicit duplicates from the `id` column: 10 rows from `first_geo`, 4 rows from `second_geo`, and 4 rows from `third_geo`.

2. **Preparing Data for Model Training**:
   - Selected features and target variable, and performed data indexing.

3. **Model Training and Validation**:
   - Created a pipeline for training the `LinearRegression` model, which:
     - Excludes unnecessary columns, splits data into training and validation sets (75:25), and applies standardization to quantitative features.
     - Trains the model and predicts the average oil volume for each region, outputs the average reserve and RMSE.
   - The model for the second region showed the best accuracy (RMSE: 0.89).
   - The highest average oil reserve was observed in the third region: 94.93 thousand barrels.

4. **Preparing for Profit Calculation**:
   - Set the key constants of the study and calculated the break-even threshold: 111.11 thousand barrels.
   - The average reserves for all regions were below the break-even threshold, indicating potential risks.
   - Created the function `revenue_all_region_bootstrap` to calculate profits from the best wells.

5. **Profit Calculation and Risk Analysis**:
   - Conducted Bootstrap analysis: created 1000 samples of 500 wells to estimate metrics.
   - **Recommendation — Second Region**:
     - Average profit: 632 million rubles.
     - Confidence interval: from 168 to 1140 million rubles.
     - Risk of loss: 0.2%.

## Authors

- Alexey Borodulin - [GitHub](https://github.com/AlexeyBoroda)

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for more details.

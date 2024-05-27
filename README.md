# Supply-Demand Gap Prediction for Uber-like Ride-hailing Service
## Overview
This project aims to predict the supply-demand gap in a ride-hailing service similar to Uber. The prediction is based on historical data of rides, which includes information about the order, driver, passenger, region, and time. The objective is to use regression algorithms to predict the gap between demand and supply for given regions and time slots.

## Table of Contents
- Project Description
- Data Description
- Data Preparation
- Model Training and Evaluation
- Results
- Usage
- Dependencies

## Project Description
The goal of this project is to predict the supply-demand gap **(gap_ij = demand_ij - supply_ij)** for specific regions and time slots. The data consists of three weeks of order information and region mappings. The prediction targets a period in the fourth and fifth weeks.

The approach involves:

- Loading and preprocessing the data.
- Calculating the demand, supply, and gap.
- Training regression models to predict the gap.
- Evaluating model performance.
- Predicting gaps for new time slots and regions.

## Data Description

### Order Information Table

This table contains information about each ride order:

- order_id: Unique identifier for the order.
- driver_id: Unique identifier for the driver (NULL if no driver accepted the order).
- passenger_id: Unique identifier for the passenger.
- start_region_hash: Hash of the region where the ride started.
- dest_region_hash: Hash of the region where the ride ended.
- price: Price of the ride.
- time: Timestamp of the order.

### Region Information Table
This table maps region hashes to region IDs:

- region_hash: Hash of the region.
- region_id: Unique identifier for the region.

## Data Preparation
### Steps
- Load Data: Load order data from Excel files and region data from a mapping file.
- Merge Data: Combine order data with region data to get region IDs.
- Calculate Time Slots: Divide each day into 144 time slots of 10 minutes each.
- Compute Demand and Supply: 
- Demand: Count of orders per region and time slot.
- Supply: Count of orders with a driver per region and time slot.
- Calculate Gap: gap = demand - supply.

## Model Training and Evaluation
Several regression models were used to predict the supply-demand gap:

- Linear Regression
- K-Nearest Neighbors (KNN)
- Ridge Regression
- Lasso Regression
- Decision Tree Classifier (used as a regression model)

### Steps
- Prepare Features and Target: Use region ID, day, and time slot as features and the gap as the target variable.
- Split Data: Split the data into training and testing sets.
- Train Models: Train each model on the training set.
- Evaluate Models: Evaluate model performance using Mean Squared Error (MSE) and accuracy.

## Results
The models were evaluated on the test set, and their performance was compared. The following metrics were calculated:

- Mean Squared Error (MSE)
- Accuracy Score

The KNN model was used to predict gaps for new time slots and regions based on scaled features.

## Usage
To use the code in this repository:

### Clone the repository:

- git clone https://github.com/aleedurrani/SupplyDemandGapPrediction.git
- cd SupplyDemandGapPrediction

Run the Jupyter notebook in Google Collab or Jupyter to see the data processing, model training, and prediction steps.

## Dependencies
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- openpyxl

## Data files
- Link to the datafiles: 

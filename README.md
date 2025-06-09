# Amazon Sales Report Analysis

## Project Description

This project performs an exploratory data analysis and statistical testing on an Amazon sales report dataset. The aim is to understand sales patterns across various dimensions such as location (states and cities), product characteristics (category and size), and order parameters (status, fulfilment, and business-to-business vs. business-to-consumer).

## Data

The analysis is based on the dataset located at `C:\Users\dkdes\OneDrive\Desktop\kaggle_datasets\Amazon Sale Report.csv`.

The raw dataset initially contains 128,975 entries and 24 columns . After cleaning and preparation, the dataset used for analysis comprises 118,837 entries and 15 columns .

## Libraries Used

The analysis was performed using the following Python libraries:
*   `pandas` for data manipulation and analysis
*   `seaborn` for data visualization
*   `matplotlib.pyplot` for plotting
*   `scipy.stats` for statistical testing (ANOVA and t-tests)

## Analysis Steps and Highlights

The analysis involved several key steps:

1.  **Data Loading and Initial Inspection:**
    *   The dataset was loaded using pandas. A `DtypeWarning` was noted for column 23 due to mixed types.
    *   Initial inspection included viewing the first few rows (`df.head()`), checking data types and non-null counts (`df.info()`), and generating descriptive statistics (`df.describe()`, `df.isnull().sum()`).

2.  **Data Cleaning and Preparation:**
    *   Several columns deemed irrelevant for the analysis were dropped. The final columns retained include: 'Date', 'Status', 'Fulfilment', 'ship-service-level', 'Category', 'Size', 'Courier Status', 'Qty', 'Amount', 'ship-city', 'ship-state', 'B2B'. New columns 'Day', 'Month', and 'Year' were extracted from the 'Date' column after converting it to datetime objects.
    *   Rows with missing 'Amount' values were removed.
    *   Rows where the 'Amount' was 0 were removed.
    *   Missing values in the 'ship-state' column were filled with "Unknown". State names were converted to lowercase.
    *   Missing values in the 'Courier Status' column were filled with "Unknown".
    *   The 'ship-state' value 'nl' was replaced with 'nagaland'.

3.  **Exploratory Data Analysis (EDA):**
    *   Visualizations were created to understand the distribution of `Amount` (histogram and boxplot).
    *   Value counts were analysed for key categorical columns like 'Courier Status', 'Status', 'Size', and 'Category'.
    *   Sales amount was analysed by 'Size' and 'Category' by calculating the mean amount for each group and visualising with bar plots.
    *   Total quantity sold was summed by 'Category'.
    *   Total sales amount was aggregated and sorted by 'ship-state' and 'ship-city'.
        *   **Maharashtra** recorded the highest total sales amount by state.
        *   **Bengaluru** recorded the highest total sales amount by city.
    *   Shipment counts by state were analysed for specific categories like "Top", "Set", "Western Dress", etc., using bar plots.
    *   Categories of cancelled orders were specifically counted. **Set** and **kurta** were the categories with the highest number of cancelled orders.

4.  **Statistical Analysis:**
    *   An ANOVA test was performed on the 'Amount' for the top 5 states by data count. The F-Statistic and P-Value variables were printed, although the output interpretation specific to the ANOVA is not shown.
    *   An independent two-sample t-test (Welch’s t-test) was conducted to compare the average sales amounts between 'Shipped' and 'Unshipped' orders based on 'Courier Status' [6-8]. The T-Statistic was -0.563 and the P-Value was 0.573. Based on this P-Value, the analysis concluded there is **no significant difference** in sales amount between shipped and unshipped orders.
    *   An independent two-sample t-test (Welch’s t-test) was conducted to compare the average sales amounts between B2B and B2C orders. The analysis printed a T-Statistic of -0.563 and a P-Value of 0.573. However, the source separately stated that there is a **significant difference** in sales amount between B2B and B2C orders .

## Getting Started

To run this analysis, you will need:
*   Python installed.
*   The required libraries: `pandas`, `seaborn`, `matplotlib`, and `scipy`. These can typically be installed via pip:
    ```bash
    pip install pandas seaborn matplotlib scipy
    ```
*   The dataset file `Amazon Sale Report.csv` in the specified path or updated path in the script.

The analysis steps are presented sequentially in th

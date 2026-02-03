#  Bitcoin Historical Data

This directory contains the metadata and instructions for the Bitcoin price dataset used in this project's predictive models (LightGBM).

## Data Source
The data is sourced from Kaggle: [Bitcoin Historical Data](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data).
This dataset provides 1-minute interval OHLC (Open, High, Low, Close) data, along with Volume in BTC and USD, and the Volume Weighted Average Price (VWAP) from the **Bitstamp** exchange.

##  Data Dictionary

| Column | Description |
| :--- | :--- |
| **Timestamp** | Unix timestamp (interval of 1 minute). |
| **Open** | Price at the start of the minute interval. |
| **High** | Highest price reached during the minute. |
| **Low** | Lowest price reached during the minute. |
| **Close** | Price at the end of the minute interval. |
| **Volume_(BTC)** | Total quantity of Bitcoin traded during the minute. |
| **Volume_(Currency)** | Total value of trades in USD during the minute. |
| **Weighted_Price** | Volume Weighted Average Price (VWAP) for the minute. |

##  How to Obtain the Data
Due to GitHub's file size limits and the significant volume of this dataset (2012–2021), the raw CSV file is not included in this repository. To reproduce the results:

1. Download the file `bitstampUSD_1-min_data_2012-01-01_to_2021-03-31.csv` from the Kaggle link above.
2. Place the downloaded file into this `/data` folder.
3. Ensure the file is ignored by Git to avoid accidental uploads (check the `.gitignore` file).

##  Data Handling Notes
* **Missing Values:** The dataset contains `NaN` values during periods of no trading activity. The preprocessing pipeline (see `notebooks/`) addresses this using forward-filling techniques to maintain time-series continuity.
* **Sampling:** For the LightGBM model, 1-minute data may be resampled (e.g., to hourly or daily intervals) to reduce noise and optimize computational performance for feature engineering.

# NYC TLC Yellow Taxi Trip Record Data

This project analyzes NYC TLC Yellow Taxi trips from January through November 2025. It uses EDA, graph mining, clustering, anomaly detection, and forecasting to study taxi-zone flows, unusual trip records, and hourly demand.

Start here: `main_notebook.ipynb`

Project video: https://www.youtube.com/watch?v=Cpct6VFGzf0

Note: the video was recorded before the final repo cleanup, so it does not match the current repo exactly.

## Research Questions

1. Do taxi zones form distinct communities in the origin-destination flow graph, and does that community structure change throughout the day?
2. Can clustering identify distinct anomaly types among outlier trips?
3. Can zone-hour taxi demand be forecast more accurately than a simple seasonal baseline?

## Data

Dataset: NYC TLC Yellow Taxi Trip Record Data.

Source: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

The notebook downloads monthly Yellow Taxi parquet files and the taxi zone lookup file. The raw data is large, so it should be downloaded by running the notebook instead of committed to GitHub.

## How To Reproduce

This project was built for Google Colab.
Use a Google Colab High-RAM runtime. The full notebook can use roughly 30-50 GB of RAM because it loads and analyzes January through November 2025 Yellow Taxi trip records.

1. Upload `main_notebook.ipynb` to Google Colab.
2. Open `main_notebook.ipynb`.
3. Run the setup and download cells.
4. Run the cleaning and EDA cells.
5. Run the RQ1, RQ2, and RQ3 analysis sections in order.

## Key Dependencies

- Python 3.11
- pandas
- numpy
- matplotlib
- scikit-learn
- networkx
- xgboost
- prophet
- statsmodels
- geopandas
- scipy
- pyarrow

See `requirements.txt` for the full Colab export. See `requirements-minimal.txt` for the short package list.

## Repo Structure

```text
.
├── main_notebook.ipynb
├── checkpoint_1.ipynb
├── checkpoint_2.ipynb
├── requirements.txt
├── requirements-minimal.txt
├── .gitignore
└── README.md
```

## Results Summary

The OD graph analysis shows that taxi-zone communities can change by time of day. The anomaly analysis separates the outlier tail into different candidate irregularity types instead of treating all outliers as one group. The forecasting section compares naive, Prophet, SARIMA, and XGBoost models, with rolling-origin and recursive checks used to judge forecasting performance more fairly.
The strongest result is that XGBoost with lag features beat the weekly naive baseline across all 20 high-demand zones tested.
The main shortcoming is that the anomaly labels are exploratory and should not be treated as confirmed fraud or confirmed bad records without outside validation.

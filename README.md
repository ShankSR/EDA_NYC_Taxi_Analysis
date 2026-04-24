# Exploratory Data Analysis (EDA) on NYC Yellow Taxi Trip Data (2023)

## Table of Contents
- [Objective](#objective)
- [Problem Statement](#problem-statement)
- [Tasks](#tasks)
- [Data Understanding](#data-understanding)
- [Dataset Source](#dataset-source)
- [Data Dictionary](#data-dictionary)
- [Data Description](#data-description)
  - [Trip Records](#trip-records)
  - [Taxi Zones](#taxi-zones)
- [Exploratory Data Analysis Approach](#exploratory-data-analysis-approach)
  - [Data Loading](#data-loading)
  - [Data Cleaning](#data-cleaning)
  - [Univariate Analysis](#univariate-analysis)
  - [Bivariate Analysis](#bivariate-analysis)
  - [Multivariate Analysis](#multivariate-analysis)
- [Visualizations](#visualizations)
- [Insights and Conclusions](#insights-and-conclusions)
- [References](#references)

---

# Objective

This case study focuses on learning **Exploratory Data Analysis (EDA)** using **NYC Yellow Taxi Trip data** and understanding how EDA helps uncover patterns useful for data science and machine learning.

Goals:
- Improve service efficiency  
- Maximize revenue  
- Enhance passenger experience  
- Support data-driven operational decisions

---

# Problem Statement

As an analyst at an upcoming taxi operation in NYC, use **2023 taxi trip data** to uncover insights that can optimize operations and improve business performance.

---

# Tasks

Perform the following:

- Data Loading  
- Data Cleaning  
- Exploratory Analysis  
- Bivariate and Multivariate Analysis  
- Visualization Creation  
- Deriving Insights  
- Stating Conclusions

---

# Data Understanding

The yellow taxi trip records include:

- Pickup and dropoff timestamps  
- Pickup and dropoff locations  
- Trip distances  
- Itemized fares  
- Rate types  
- Payment methods  
- Passenger counts  

## Data Format
- Format: `.parquet`
- Coverage: 2009–2024
- Scope for assignment: **2023 only**
- 12 monthly parquet files

Data is collected and provided by the **NYC Taxi and Limousine Commission (TLC)**.

---

# Dataset Source

## TLC Trip Records
https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

---

# Data Dictionary

Official PDF:

[NYC Yellow Taxi Data Dictionary (PDF)](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf)

---

# Data Description

## Trip Records

| Field Name | Description |
|-----------|-------------|
| **VendorID** | A code indicating the TPEP provider that provided the record.<br><br>1 = Creative Mobile Technologies, LLC<br>2 = VeriFone Inc. |
| **tpep_pickup_datetime** | The date and time when the meter was engaged. |
| **tpep_dropoff_datetime** | The date and time when the meter was disengaged. |
| **Passenger_count** | The number of passengers in the vehicle.<br>This is a driver-entered value. |
| **Trip_distance** | The elapsed trip distance in miles reported by the taximeter. |
| **PULocationID** | TLC Taxi Zone in which the taximeter was engaged |
| **DOLocationID** | TLC Taxi Zone in which the taximeter was disengaged |
| **RateCodeID** | The final rate code in effect at the end of the trip.<br><br>1 = Standard rate<br>2 = JFK<br>3 = Newark<br>4 = Nassau or Westchester<br>5 = Negotiated fare<br>6 = Group ride |
| **Store_and_fwd_flag** | This flag indicates whether the trip record was held in vehicle memory before sending to vendor ("store and forward").<br><br>Y = Store and forward trip<br>N = Not store and forward trip |
| **Payment_type** | Numeric code signifying how passenger paid.<br><br>1 = Credit card<br>2 = Cash<br>3 = No charge<br>4 = Dispute<br>5 = Unknown<br>6 = Voided trip |
| **Fare_amount** | Time-and-distance fare calculated by meter. |
| **Extra** | Miscellaneous extras and surcharges. |
| **MTA_tax** | 0.50 USD MTA tax. |
| **Improvement_surcharge** | 0.30 USD surcharge assessed at flag drop. |
| **Tip_amount** | Tip amount populated for credit card tips. Cash tips excluded. |
| **Tolls_amount** | Total amount of tolls paid. |
| **total_amount** | Total amount charged to passengers. |
| **Congestion_Surcharge** | NYS congestion surcharge collected. |
| **Airport_fee** | 1.25 USD pickup fee at LaGuardia and JFK Airports. |

> **Note:** Although extra charges and taxes are defined in the data dictionary, actual data may contain different values in some cases.

---

## Taxi Zones

Each trip record contains pickup and dropoff location IDs ranging from:

**1–263**

These map to NYC taxi zones and can be joined to zone lookup tables or shapefiles for geographic analysis.

Possible use cases:
- Demand heatmaps  
- Route analysis  
- Zone-level revenue analysis  
- Spatial clustering

---

# Exploratory Data Analysis Approach

## Data Loading

Example:

```python
import pandas as pd

df = pd.read_parquet('yellow_tripdata_2023-01.parquet')
df.head()
```

Tasks:
- Load all monthly files  
- Merge datasets  
- Inspect schema  
- Check dimensions

---

## Data Cleaning

Possible cleaning steps:

- Null handling  
- Duplicate removal  
- Outlier treatment  
- Invalid trip filtering  
- Fare anomaly detection  
- Datetime conversions

Feature Engineering:
- Hour of day  
- Weekday  
- Month  
- Trip duration

---

## Univariate Analysis

Analyze:
- Passenger count distribution  
- Trip distance distribution  
- Fare distribution  
- Tip patterns  
- Payment types  
- Demand by hour

Visuals:
- Histograms  
- Boxplots  
- Countplots

---

## Bivariate Analysis

Study relationships:

- Distance vs Fare  
- Distance vs Tip  
- Payment type vs Tip  
- Pickup hour vs Demand  
- Passenger count vs Revenue

Methods:
- Scatterplots  
- Group analysis  
- Correlation

---

## Multivariate Analysis

Possible analysis:

- Revenue by location and time  
- Demand by hour and zone  
- Tips by payment and zone  
- Multi-factor trip behavior analysis

Methods:
- Heatmaps  
- Pivot tables  
- Pairplots  
- Cluster analysis

---

# Visualizations

Recommended charts:

- Trip Volume by Hour  
- Revenue Trends  
- Top Pickup Zones  
- Top Dropoff Zones  
- Payment Type Distribution  
- Fare vs Distance Scatter Plot  
- Correlation Heatmap  
- Monthly Trends  
- Geographic Demand Maps

(Add visuals here)

---

# Insights and Conclusions

Potential insights:

## Operational
- Peak demand hours  
- High-demand zones  
- Low utilization windows

## Revenue
- Most profitable routes  
- Fare behavior patterns  
- Tip behavior

## Passenger Experience
- Preferred payment methods  
- Pickup hotspots  
- Service improvement opportunities

### Recommendations
1. Optimize driver allocation during peaks  
2. Increase coverage in profitable zones  
3. Improve demand forecasting  
4. Use insights for pricing and operational strategy

---

# References

- TLC Trip Records  
https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

- Data Dictionary  
https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf

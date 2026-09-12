# 📊 Exploratory Data Analysis on Shopify Stock Data

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on historical Shopify stock market data. The analysis focuses on understanding stock price movements, trading volume, daily returns, and price ranges using Python.

The dataset contains **2,469 trading records** with information such as opening price, highest price, lowest price, closing price, adjusted closing price, and trading volume.

---

## 🎯 Objective

The main objective of this project is to:

* Load and understand the Shopify stock dataset
* Inspect the structure and quality of the data
* Check and handle missing and duplicate values
* Convert and organize the date column
* Create useful features for stock analysis
* Perform descriptive statistical analysis
* Visualize stock trading patterns and returns
* Identify important trends and characteristics in the dataset

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **Matplotlib**
* **Google Colab**

---

## 📂 Dataset

The dataset used in this project is:

`SHOP.csv`

### Original Columns

| Column      | Description                    |
| ----------- | ------------------------------ |
| `date`      | Trading date                   |
| `open`      | Opening stock price            |
| `high`      | Highest stock price of the day |
| `low`       | Lowest stock price of the day  |
| `close`     | Closing stock price            |
| `adj_close` | Adjusted closing price         |
| `volume`    | Number of shares traded        |

The dataset contains **2,469 rows and 7 columns**.

---

## 🔍 Project Workflow

### 1. Import Required Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
```

Pandas is used for data loading, cleaning, manipulation, and statistical analysis. Matplotlib is used for data visualization.

---

### 2. Load the Dataset

```python
df = pd.read_csv("/content/SHOP.csv")
```

The `read_csv()` function loads the Shopify stock dataset into a Pandas DataFrame.

---

### 3. Inspect the Dataset

The first five records are displayed using:

```python
print(df.head())
```

The dataset shape is checked using:

```python
print(df.shape)
```

**Result:**

* Rows: **2,469**
* Columns: **7**

---

### 4. Check Dataset Information

```python
print(df.info())
```

The dataset contains:

* 1 date column
* 5 floating-point columns
* 1 integer column

The `date` column is initially stored as an object.

---

### 5. Check Missing Values

```python
print(df.isnull().sum())
```

There are **no missing values** in the original dataset.

---

### 6. Remove Duplicate Records

```python
df = df.drop_duplicates()
```

Duplicate records are removed to improve data quality.

---

### 7. Convert Date Column

```python
df["date"] = pd.to_datetime(
    df["date"],
    format="mixed",
    errors="coerce"
)
```

The date column is converted into datetime format so that the data can be sorted and used for time-series analysis.

---

### 8. Sort Data by Date

```python
df = df.sort_values("date")
```

The records are arranged in chronological order.

---

### 9. Set Date as Index

```python
df = df.set_index("date")
```

The date is used as the DataFrame index, which is useful for time-series analysis.

---

### 10. Remove Missing Values

```python
df = df.dropna()
```

Any rows containing missing values are removed after the date conversion.

---

## ⚙️ Feature Engineering

Three new features were created.

### Daily Price Change

```python
df["Daily_Price_Change"] = df["close"] - df["open"]
```

This calculates the difference between the closing price and opening price.

### Daily Return Percentage

```python
df["Daily_Return_%"] = (
    (df["close"] - df["open"]) / df["open"]
) * 100
```

This calculates the daily stock return as a percentage.

### Price Range

```python
df["Price_Range"] = df["high"] - df["low"]
```

This calculates the difference between the highest and lowest price of the day.

---

## 📈 Descriptive Statistics

The statistical summary is obtained using:

```python
print(df.describe())
```

Important statistics include:

| Statistic           |    Value |
| ------------------- | -------: |
| Mean Open Price     |  48.4643 |
| Mean High Price     |  49.5055 |
| Mean Low Price      |  47.3478 |
| Mean Close Price    |  48.4566 |
| Minimum Close Price |   1.9330 |
| Maximum Close Price | 169.0600 |

---

## 📊 Return Analysis

### Mean Daily Return

```python
print("Mean Return:", df["Daily_Return_%"].mean())
```

**Mean Daily Return:** approximately **0.0864%**

### Return Variance

```python
print("Return Variance:", df["Daily_Return_%"].var())
```

**Return Variance:** approximately **9.7331**

### Return Standard Deviation

```python
print(
    "Return Standard Deviation:",
    df["Daily_Return_%"].std()
)
```

**Standard Deviation:** approximately **3.1198%**

The standard deviation indicates the amount of variation in Shopify's daily returns.

---

## 📉 Data Visualization

### 1. Shopify Trading Volume Trend

```python
plt.figure(figsize=(12,5))
plt.plot(df.index, df["volume"])
plt.title("Shopify Trading Volume Trend")
plt.xlabel("Date")
plt.ylabel("Volume")
plt.xticks(rotation=45)
plt.show()
```

This visualization shows how Shopify's trading volume changed over time.

---

### 2. Daily Return Distribution

```python
plt.figure(figsize=(12,5))
plt.hist(df["Daily_Return_%"], bins=30)
plt.title("Shopify Daily Return Distribution")
plt.xlabel("Daily Return (%)")
plt.ylabel("Frequency")
plt.show()
```

The histogram shows the distribution and frequency of Shopify's daily returns.

---

### 3. Shopify Price Range Trend

```python
plt.figure(figsize=(12,5))
plt.plot(df.index, df["Price_Range"])
plt.title("Shopify Stock Price Range Trend")
plt.xlabel("Date")
plt.ylabel("Price Range")
plt.xticks(rotation=45)
plt.show()
```

This graph represents the variation in Shopify's daily price range over time.

---

## 🔑 Key Findings

* The dataset contains **2,469 records and 7 original columns**.
* There are **no missing values** in the original dataset.
* Duplicate records were removed during data cleaning.
* The date column was converted to datetime format and used as the index.
* Three new features were created:

  * Daily Price Change
  * Daily Return %
  * Price Range
* The mean daily return is approximately **0.0864%**.
* The variance of daily returns is approximately **9.7331**.
* The standard deviation of daily returns is approximately **3.1198%**.
* Trading volume, daily return distribution, and price range were visualized using Matplotlib.

---

## 📝 Conclusion

The Exploratory Data Analysis provided a clear understanding of the structure, quality, statistical characteristics, and trading behaviour of Shopify stock data.

The dataset was successfully inspected and cleaned, followed by feature engineering and statistical analysis. Visualizations helped identify patterns in trading volume, daily returns, and stock price ranges.

Overall, this project demonstrates how **Python, Pandas, and Matplotlib** can be used to perform EDA and gain meaningful insights from financial market data.

---

## 📁 Project Files

```text
Shopify-Stock-EDA/
│
├── EDA_TASK_3(2).ipynb
├── SHOP.csv
└── README.md
```



BCA Graduate | Aspiring IT Professional

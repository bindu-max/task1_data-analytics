# Task 1: Data Immersion & Wrangling

## Objective

The objective of this task was to explore the dataset, identify data quality issues, clean the data, perform necessary transformations, and prepare an analysis-ready dataset using **Python** and **Pandas**.

## Dataset

**Dataset Name:** `ApexPlanet_DataAnalytics_Dataset (1).xlsx`

The dataset contains customer order information, including:

- Order Details
- Customer Information
- Product Information
- Sales Records
- Order Dates

## Tools and Technologies Used

- Python
- Pandas
- Microsoft Excel

## Steps Performed

### 1. Data Loading

Loaded the dataset from an Excel file using Pandas.

```python
df = pd.read_excel("ApexPlanet_DataAnalytics_Dataset (1).xlsx")
```

### 2. Data Exploration

Performed an initial analysis to understand:

- Dataset shape
- Data types
- Missing values
- Duplicate records

```python
df.info()
df.isnull().sum()
df.duplicated().sum()
```

### 3. Handling Missing Values

Filled missing values using appropriate statistical methods:

- **Age** → Median
- **City** → Mode

```python
df["Age"] = df["Age"].fillna(df["Age"].median())
df["City"] = df["City"].fillna(df["City"].mode()[0])
```

### 4. Removing Duplicates

Removed duplicate records from the dataset.

```python
df = df.drop_duplicates()
```

### 5. Data Type Conversion

Converted columns into appropriate data types.

```python
df["Order_Date"] = pd.to_datetime(df["Order_Date"])
df["Age"] = df["Age"].astype(int)
df["Quantity"] = df["Quantity"].astype(int)
df["Unit_Price"] = df["Unit_Price"].astype(float)
df["Total_Sales"] = df["Total_Sales"].astype(float)
```

### 6. Renaming Columns

Renamed columns for better readability and consistency.

| Original Column | Renamed Column |
|----------------|----------------|
| Order_ID | OrderID |
| Order_Date | OrderDate |
| Customer_ID | CustomerID |
| Customer_Name | CustomerName |
| Unit_Price | UnitPrice |
| Total_Sales | TotalSales |

### 7. Feature Engineering

Created additional date-related features from the `OrderDate` column.

```python
df["Year"] = df["OrderDate"].dt.year
df["Month"] = df["OrderDate"].dt.month
df["Day"] = df["OrderDate"].dt.day
```

New features created:

- Year
- Month
- Day

### 8. Final Validation

Verified:

- Missing values
- Dataset dimensions
- Data types

```python
df.isnull().sum()
df.dtypes
```

### 9. Exporting the Cleaned Dataset

Saved the cleaned dataset for future analysis.

```python
df.to_excel("Cleaned_Sales_Dataset.xlsx", index=False)
```

---

## Results

✅ Missing values handled successfully

✅ Duplicate records removed

✅ Data types standardized

✅ Column names renamed for consistency

✅ Date-based features created

✅ Clean and analysis-ready dataset generated

---

## Input and Output Files

### Input File

`ApexPlanet_DataAnalytics_Dataset (1).xlsx`

### Output File

`Cleaned_Sales_Dataset.xlsx`

---

## Conclusion

The dataset was successfully cleaned and transformed into a structured and analysis-ready format. Data quality issues such as missing values and incorrect data types were resolved. Additional date-based features were created to support future analysis and visualization tasks.


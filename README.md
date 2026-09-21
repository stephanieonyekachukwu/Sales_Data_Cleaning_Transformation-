# 📊 Sales Data Cleaning & Transformation with Excel Power Query

## 📌 Project Overview

This project demonstrates the cleaning and transformation of a poorly structured sales dataset using **Microsoft Excel and Power Query**.

The original dataset contained sales information for three business segments:

* Consumer
* Corporate
* Home Office

The source data was presented in a **cross-tabulated format**, with business segments and shipping modes distributed across different columns. This structure made the dataset difficult to analyze and unsuitable for straightforward reporting.

The objective of this project was to transform the source data into a **clean, standardized, and analysis-ready dataset** while creating a repeatable data-cleaning workflow.

---

## 🎯 Project Objective

The primary objective was to transform the original sales worksheet into a standardized relational dataset that could be used for:

* Sales analysis
* Business segment analysis
* Shipping-mode analysis
* Future dashboard development
* Stakeholder reporting

The final dataset was designed to follow a consistent tabular structure:

**Order ID | Ship Mode | Sales | Segment**

---

## 🛠️ Tools & Technologies

| Tool                | Purpose                                                     |
| ------------------- | ----------------------------------------------------------- |
| **Microsoft Excel** | Data storage, validation, and final output                  |
| **Power Query**     | Data cleaning, transformation, restructuring, and appending |

---

## 📂 Source Dataset

The original workbook contained a worksheet named:

**`Dirty 1`**

The dataset included:

* Order IDs
* Sales information
* Shipping modes
* Consumer segment
* Corporate segment
* Home Office segment
* Grand Total information

### Original Structure

The source data was not organized as a conventional transaction table. Instead, sales for the different segments were arranged across separate sections, while shipping modes were represented as individual columns.

This created several challenges for analysis.

---

## ⚠️ Data Quality & Structural Issues

The initial assessment identified the following issues:

### 1. Cross-Tabulated Structure

Consumer, Corporate, and Home Office data were arranged in separate sections rather than being represented by a single `Segment` field.

### 2. Shipping Modes Stored as Columns

Shipping modes were stored as separate columns:

* First Class
* Same Day
* Second Class
* Standard Class

This prevented `Ship Mode` from functioning as a standard categorical field.

### 3. Header and Metadata Rows

The source contained non-transactional header and metadata information that needed to be removed before analysis.

### 4. Grand Total Rows

The source included `Grand Total` and other non-transaction rows that needed to be excluded from the transaction-level dataset.

### 5. Inconsistent Segment Structures

The three segment sections were positioned differently within the source worksheet and therefore required individual transformation before they could be combined.

---

# 🔄 Data Transformation Process

## Step 1 — Import Source Data

The `Dirty 1` worksheet was imported into **Power Query**.

The original source query was preserved to maintain a clear separation between the raw data and the transformation process.

---

## Step 2 — Create Segment-Specific Queries

Separate queries were created for:

* `Consumer`
* `Corporate`
* `Home Office`

This allowed each segment to be transformed independently while maintaining the original source data.

---

## Step 3 — Remove Unnecessary Data

For each segment, unnecessary columns and non-transaction information were removed.

The transformation focused on retaining the fields required for the final analysis:

* Order ID
* Shipping-mode sales columns

---

## Step 4 — Unpivot Shipping Modes

The four shipping-mode columns were transformed using **Unpivot Columns**.

### Before

| Order ID | First Class | Same Day | Second Class | Standard Class |
| -------- | ----------: | -------: | -----------: | -------------: |
| Order 1  |       Value |    Value |        Value |          Value |

### After

| Order ID | Ship Mode      | Sales |
| -------- | -------------- | ----: |
| Order 1  | First Class    | Value |
| Order 1  | Same Day       | Value |
| Order 1  | Second Class   | Value |
| Order 1  | Standard Class | Value |

This transformation converted the shipping modes from columns into values within a single `Ship Mode` column.

---

## Step 5 — Remove Non-Transaction Records

`Grand Total` and other non-transaction rows were filtered out from each segment query.

This ensured that the final dataset contained transaction-level records rather than summary rows.

---

## Step 6 — Standardize Column Names

The transformed queries were standardized using the following field names:

| Field       | Description                    |
| ----------- | ------------------------------ |
| `Order ID`  | Identifies the order           |
| `Ship Mode` | Identifies the shipping method |
| `Sales`     | Contains the sales amount      |

---

## Step 7 — Add Segment Field

A `Segment` column was added to each query.

| Query       | Segment Value |
| ----------- | ------------- |
| Consumer    | Consumer      |
| Corporate   | Corporate     |
| Home Office | Home Office   |

This ensured that each record retained its original business-segment classification after the datasets were combined.

The resulting structure was:

**Order ID | Ship Mode | Sales | Segment**

---

## Step 8 — Standardize Data Types

The data types were standardized before the queries were appended.

| Field       | Data Type      |
| ----------- | -------------- |
| `Order ID`  | Text           |
| `Ship Mode` | Text           |
| `Sales`     | Decimal Number |
| `Segment`   | Text           |

Standardizing data types ensured compatibility across the three datasets and reduced the risk of data-type inconsistencies during analysis.

---

# 🔗 Step 9 — Append Segment Queries

The three cleaned queries were combined using **Power Query → Append Queries as New**.

The following queries were appended:

1. Consumer
2. Corporate
3. Home Office

The resulting query was named:

### `Sales_Final`

---

# 📊 Final Dataset

The final `Sales_Final` dataset contains:

| Metric                |    Result |
| --------------------- | --------: |
| **Records**           | **1,019** |
| **Fields**            |     **4** |
| **Business Segments** |     **3** |

### Record Distribution

| Segment     |   Records |
| ----------- | --------: |
| Consumer    |       444 |
| Corporate   |       444 |
| Home Office |       131 |
| **Total**   | **1,019** |

**444 + 444 + 131 = 1,019 records**

---

# 🧱 Final Dataset Structure

| Field       | Data Type      | Purpose                         |
| ----------- | -------------- | ------------------------------- |
| `Order ID`  | Text           | Identifies the order            |
| `Ship Mode` | Text           | Identifies the shipping method  |
| `Sales`     | Decimal Number | Contains sales amount           |
| `Segment`   | Text           | Identifies the business segment |

---

# 🔍 Data Quality Validation

After completing the transformations and append operation, the final dataset was validated.

### ✅ Blank / Null Check

The final dataset was reviewed for unexpected blank or null values.

No unexpected blank/null values were identified in the final dataset.

### ✅ Non-Transaction Row Check

`Grand Total` and other non-transaction records were removed during the segment-level transformations.

### ✅ Structural Validation

The final dataset was confirmed to contain the expected four fields:

```text
Order ID
Ship Mode
Sales
Segment
```

### ✅ Segment Validation

The final dataset retained the expected three business segments:

```text
Consumer
Corporate
Home Office
```

### ✅ Duplicate Record Check

A duplicate-record check was performed using Excel's **Remove Duplicates** functionality.

The following four fields were used for the check:

```text
Order ID
Ship Mode
Sales
Segment
```

This check was intended to identify records where all four fields were identical.

---

# 🔧 Power Query Techniques Used

The project demonstrates the following data-transformation techniques:

* Importing data into Power Query
* Duplicating queries
* Selecting columns
* Removing unnecessary columns
* Removing top rows
* Filtering rows
* Removing non-transaction records
* Renaming columns
* Unpivoting columns
* Adding custom columns
* Standardizing data types
* Appending queries
* Loading transformed data into Excel

---

# 📈 Business Value

The transformation converted a difficult-to-analyze cross-tabulated dataset into a standardized relational structure.

The resulting dataset can now be used to analyze sales by:

* **Business Segment**
* **Ship Mode**
* **Order**
* **Sales Amount**

More importantly, the Power Query workflow creates a **repeatable transformation process**.

Instead of manually restructuring the original spreadsheet each time analysis is required, the transformation logic can be refreshed when the source data changes.

This improves consistency, maintainability, and efficiency.

---

# 🔄 Before vs. After

## Before

The original dataset was:

* Cross-tabulated
* Divided into separate segment sections
* Using shipping modes as columns
* Containing header/metadata information
* Containing Grand Total rows
* Difficult to analyze directly

## After

The transformed dataset is:

* Standardized
* Structured in rows and columns
* Organized by Order ID
* Organized by Ship Mode
* Organized by Sales
* Categorized by Segment
* Assigned appropriate data types
* Combined into one dataset
* Loaded back into Excel

---

# 📁 Project Structure

A recommended GitHub repository structure for this project is:

```text
sales-data-cleaning-power-query/
│
├── README.md
│
├── data/
│   ├── raw/
│   │   └── Dirty_1.xlsx
│   │
│   └── cleaned/
│       └── Sales_Final.xlsx
│
├── documentation/
│   └── Sales_Data_Cleaning_Report.pdf
│
└── screenshots/
    ├── source-data.png
    ├── power-query-transformations.png
    ├── sales-final-query.png
    └── final-dataset.png
```

> **Note:** If the source dataset is confidential or contains sensitive business information, do not upload the raw file to a public GitHub repository. Use a sanitized or sample dataset instead.

---

# 🚀 Project Outcome

The project successfully transformed the original `Dirty 1` worksheet into a standardized dataset named:

### `Sales_Final`

The final dataset contains:

**1,019 records across 4 standardized fields.**

The completed transformation provides a structured foundation for further sales analysis and reporting.

### Future Analysis

The cleaned dataset can be used as the foundation for future work such as:

* Sales KPI development
* Segment-level performance analysis
* Ship-mode analysis
* Trend analysis
* Excel dashboard development
* Power BI visualization
* Business performance reporting

**KPI development and dashboard creation are outside the scope of this data-cleaning stage.**

---

# 👤 Skills Demonstrated

This project demonstrates practical experience in:

* **Data Cleaning**
* **Data Transformation**
* **Power Query**
* **Excel**
* **Data Quality Validation**
* **Data Structuring**
* **Relational Data Preparation**
* **ETL Concepts**
* **Analytical Thinking**
* **Documentation**

---

## 📌 Summary

> **Raw cross-tabulated sales data → Power Query transformation → standardized segment queries → unpivoted shipping modes → data validation → appended `Sales_Final` dataset**

The result is a clean, standardized, and analysis-ready sales dataset that can support future business intelligence and reporting activities.


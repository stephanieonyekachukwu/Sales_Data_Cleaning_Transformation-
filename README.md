# 📊 Sales Data Cleaning & Transformation with Excel Power Query

## Project Overview

This project demonstrates how **Microsoft Excel Power Query** was used to transform a poorly structured sales dataset into a clean, standardized, and analysis-ready dataset.

The source data contained three business segments:

* Consumer
* Corporate
* Home Office

The original dataset was cross-tabulated, with segments and shipping modes distributed across different columns. It also contained header/metadata information and `Grand Total` rows, making it unsuitable for straightforward analysis.

---

## 🎯 Objective

The goal was to restructure the raw dataset into a standardized table that could support reliable sales analysis and future reporting.

The target structure was:

**Order ID | Ship Mode | Sales | Segment**

---

## 🛠️ Tools Used

* **Microsoft Excel**
* **Power Query**

---

## 🔍 Data Quality Issues

The source dataset presented several challenges:

* Cross-tabulated segment structure
* Shipping modes stored as separate columns
* Header and metadata rows
* `Grand Total` and other non-transaction records
* Different structures across the three business segments

---

## 🔄 Data Transformation Process

The data was imported into Power Query while preserving the original source.

Separate queries were created for:

* Consumer
* Corporate
* Home Office

Each query was independently cleaned by:

1. Removing unnecessary columns and non-transaction information
2. Filtering out `Grand Total` records
3. Renaming and standardizing columns
4. **Unpivoting** the shipping-mode columns
5. Standardizing data types
6. Adding a `Segment` field

The three cleaned queries were then appended into a new query named:

### `Sales_Final`

---

## 📊 Final Dataset

| Segment     |   Records |
| ----------- | --------: |
| Consumer    |       444 |
| Corporate   |       444 |
| Home Office |       131 |
| **Total**   | **1,019** |

The final dataset contains **1,019 records and 4 standardized fields**:

| Field       | Data Type      |
| ----------- | -------------- |
| `Order ID`  | Text           |
| `Ship Mode` | Text           |
| `Sales`     | Decimal Number |
| `Segment`   | Text           |

---

## ✅ Data Validation

The final dataset was validated for:

* Blank/null values
* Non-transaction records
* Expected field structure
* Segment values
* Data types
* Duplicate records using `Order ID`, `Ship Mode`, `Sales`, and `Segment`

The final dataset was then loaded back into Excel for further analysis.

---

## 💼 Business Value

The transformation converted a difficult-to-analyze cross-tabulated dataset into a standardized relational structure.

The cleaned dataset can now support analysis by:

* Business segment
* Shipping mode
* Order
* Sales amount

The Power Query workflow also provides a **repeatable transformation process**, reducing the need for manual restructuring when the source data is refreshed.

---

## 🔧 Key Skills Demonstrated

* Excel
* Power Query
* Data Cleaning
* Data Transformation
* Data Validation
* ETL Concepts
* Data Structuring
* Analytical Thinking
* Documentation

---

## 🚀 Project Outcome

The original `Dirty 1` worksheet was successfully transformed into the standardized `Sales_Final` dataset containing:

**1,019 records | 4 fields | 3 business segments**

This cleaned dataset provides a reliable foundation for future sales analysis, KPI development, and dashboard creation.

> **Raw Data → Power Query → Cleaned Segment Queries → Unpivot → Validate → Append → `Sales_Final`**

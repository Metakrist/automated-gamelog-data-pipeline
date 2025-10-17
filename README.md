# automated-gamelog-data-pipeline
# Automated Game Log ETL Data Pipeline

## 🧩 Overview
This project is a **Python-based ETL (Extract, Transform, Load) data pipeline** that automates the retrieval, validation, and reporting of **game log data** from a MySQL database.  
It integrates database querying, data transformation, and Excel report generation into a single automated workflow.

The automation reduces manual work by dynamically managing date ranges, handling timezone adjustments, validating extracted data, and exporting results into standardized Excel reports for analysis.

---

## ⚙️ ETL Workflow Summary

### 🟢 **Extract**
- Connects securely to the **MySQL database**.
- Executes SQL queries to retrieve game log data within defined start and end dates.
- Dynamically adjusts the date window for each run (e.g., previous day’s data or a set time range).

### 🟡 **Transform**
- Validates and cleans the extracted data:
  - Removes unwanted rows (e.g., `Game = 'summary'`)
  - Ensures correct data types and value consistency
  - Applies timezone adjustments for multiple regions (e.g., `+8`, `0`, `-3`)
- Prepares data for reporting by reformatting columns and applying standardized naming conventions.

### 🔵 **Load**
- Loads the validated data into Excel files (`.xlsx`) using either:
  - Standardized templates (e.g., for report submission), or  
  - Dynamically generated filenames with timestamps and timezone offsets.  
- Appends to existing sheets or creates new ones automatically.
- Stores output files in a designated folder for reporting and archival.

---

## 💡 Key Features
- **Fully Automated Workflow** – From extraction to report generation  
- **Dynamic Date Management** – No need for manual input  
- **Multi-Timezone Support** – Generates reports across different time zones  
- **Data Validation Layer** – Ensures only clean and correct data is stored  
- **Excel Reporting Integration** – Saves directly to `.xlsx` format with templates  
- **Notebook Transparency** – Displays clear process updates and status messages

---

## 🧠 Technologies & Libraries
| Library | Purpose |
|----------|----------|
| **pandas** | Data manipulation, cleaning, and Excel export |
| **mysql.connector** | Database connection and SQL query execution |
| **datetime** | Date range and time management |
| **openpyxl** | Writing to and updating Excel files |
| **os / pathlib** | File handling and directory operations |
| **IPython.display / tqdm** | Visual process updates within Jupyter Notebook |

---

## 🧮 Data Pipeline Flow

```
┌────────────────────┐
│   MySQL Database   │
└─────────┬──────────┘
          │
          ▼
 ┌────────────────────┐
 │   Extract (E)      │
 │ - Run SQL queries  │
 │ - Fetch data       │
 └─────────┬──────────┘
           │
           ▼
 ┌────────────────────┐
 │   Transform (T)    │
 │ - Validate records │
 │ - Filter rows      │
 │ - Adjust timezones │
 └─────────┬──────────┘
           │
           ▼
 ┌────────────────────┐
 │     Load (L)       │
 │ - Export to Excel  │
 │ - Append/Save File │
 └────────────────────┘

🚀 How to Run
1. Clone the Repository
git clone https://github.com/<your-username>/automated-gamelog-data-pipeline.git
cd automated-gamelog-data-pipeline

2. Install Dependencies
pip install pandas mysql-connector-python openpyxl tqdm

3. Run the Notebook

Open in Jupyter Notebook or VSCode:

jupyter notebook Smash_GMT-3_GameLogs_db_extraction_101725.ipynb

4. Output

Excel reports are automatically generated in the /Output folder, using dynamic filenames such as:

smashgldbextract_2024-08-14(+8).xlsx

🧾 Example Output
| Date       | Game  | Player  | Bet | Win | Status    |
| ---------- | ----- | ------- | --- | --- | --------- |
| 2024-08-14 | Smash | user123 | 100 | 250 | Completed |

🏁 Summary

This project demonstrates a complete ETL data pipeline built using Python and MySQL.
It showcases the ability to:

Automate data extraction from a relational database

Apply transformation and validation logic dynamically

Load clean data into well-structured Excel reports

The workflow is designed to be scalable, efficient, and transparent, ideal for analytics and reporting environments.

Krist Ian
Data Analyst | Automation Developer
📧 [https://github.com/Metakrist]

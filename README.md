# 🚴 Divvy Bike Data Warehouse with Microsoft Azure

This project demonstrates how to build a comprehensive cloud-based data warehouse solution using Microsoft Azure tools to analyze data from the **Divvy bike-sharing program** in Chicago. The workflow encompasses setting up an OLTP-like PostgreSQL environment, extracting and transforming data using Azure Synapse Analytics, and designing a star schema for optimized analysis.

---

## 📦 Project Overview

The objective of this project is to analyze Divvy’s ridership patterns and revenue behavior using both real and fabricated datasets. We simulate a production OLTP system in **Azure PostgreSQL**, extract the data into **Azure Blob Storage**, and transform it into a **star schema** within **Azure Synapse Analytics** using serverless SQL pools. This model supports advanced analytical queries based on ride duration, user demographics, station usage, and payment patterns.

---

## 🗂️ Data Details

The datasets utilized in this project include:

- **Trip Data** (real): Information on bike trips, including start and end times, and station IDs.
- **Account Data** (mock): Simulated account information, including membership type and signup dates.
- **Rider Data** (mock): Demographic details such as birth year and gender.
- **Payment Data** (mock): Simulated revenue data, including amounts and payment dates.

These datasets are initially uploaded into PostgreSQL and subsequently extracted into Blob Storage for staging and processing in Synapse.

---

## 🧱 Data Schema Design

The project begins with a normalized relational model in PostgreSQL, reflecting a real-time transactional system. To facilitate analytical querying, the data is restructured into a **star schema** in Synapse with the following structure:

### Relational Schema

![Original Data Schema](https://raw.githubusercontent.com/haoranwang99/Database-Azure-Divvy/main/re-modelling/Original%20Data%20Schema.png)

### Star Schema

![star schema](https://raw.githubusercontent.com/haoranwang99/Database-Azure-Divvy/main/re-modelling/star%20schema.png)

The design includes two **fact tables** (`fact_trip` and `fact_payment`) and multiple **dimension tables** (`dim_rider`, `dim_account`, `dim_station`, `dim_date`). This setup enhances querying flexibility for key performance indicators such as average ride time, trip frequency by age group, and revenue per user segment.

For a detailed explanation of the rationale behind using two fact tables, refer to the [Star_Schema_Justification](https://github.com/haoranwang99/Database-Azure-Divvy/blob/main/re-modelling/Star_Schema_Justification.pdf) document.

---

## 🔄 Project Workflow

1. **Data Simulation & Loading**
   - Load all four datasets into **Azure PostgreSQL** using the provided Python ETL script.
2. **Data Extraction**
   - Extract data into **Azure Blob Storage** using Synapse’s ingestion tools.
3. **Data Staging**
   - Load flat files into **external staging tables** using serverless SQL pools.
4. **Data Modeling**
   - Transform raw data into **fact and dimension tables** using CETAS.
5. **Analytics & Visualization**
   - Utilize SQL queries for analytical insights into ride behavior and spending patterns.

---

## 💻 Technologies Used

- **Azure PostgreSQL**
- **Azure Blob Storage**
- **Azure Synapse Analytics**
- **Python** (for ETL processes)
- **SQL** (for CETAS, star schema transformation)
- **pgAdmin** (for PostgreSQL exploration)

---

## 📁 Repository Structure

```
📂 Database-Azure-Divvy
├── ProjectDataToPostgres.py      # Python script to simulate OLTP loading
├── re-modelling/                 # Directory containing schema diagrams and justification document
├── SQL/                          # Directory containing SQL scripts for data transformation
├── project.ipynb                 # Jupyter Notebook documenting the project workflow
└── README.md                     # Project overview and instructions
```

---

## 👤 Author

**Haoran Wang**  
[GitHub Profile](https://github.com/haoranwang99)

---

## 📜 License

This project is licensed under the MIT License – feel free to use, modify, and distribute as permitted.

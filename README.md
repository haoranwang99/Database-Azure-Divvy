# 🚴 Divvy Bike Data Warehouse with Microsoft Azure

This project demonstrates how to build a complete cloud-based data warehouse solution using Microsoft Azure tools to analyze data from the **Divvy bike-sharing program** in Chicago. The workflow includes setting up an OLTP-like PostgreSQL environment, extracting and transforming data using Azure Synapse Analytics, and designing a star schema for optimized analysis.

---

## 📦 Project Overview

The goal of this project is to analyze Divvy’s ridership patterns and revenue behavior using both real and fabricated datasets. We simulate a production OLTP system in **Azure PostgreSQL**, extract the data into **Azure Blob Storage**, and transform it into a **star schema** within **Azure Synapse Analytics** using serverless SQL pools. From there, the model supports advanced analytical queries based on ride time, user demographics, station usage, and payment patterns.

---

## 🗂️ Data Details

The data used in this project includes:
- **Trip Data** (real): Information on bike trips including start and end times and station IDs.
- **Account Data** (mock): Simulated account information including membership type and signup dates.
- **Rider Data** (mock): Demographic details like birth year and gender.
- **Payment Data** (mock): Simulated revenue data including amount and payment dates.

These datasets are uploaded into PostgreSQL and later extracted into Blob Storage for staging and processing in Synapse.

---

## 🧱 Data Schema Design

We begin with a normalized relational model in PostgreSQL, which reflects a real-time transactional system. To enable analytical querying, the data is restructured into a **star schema** in Synapse with the following structure:

### Relational Schema

![Original Data Schema](https://raw.githubusercontent.com/haoranwang99/Database-Azure-Divvy/main/re-modelling/Original Data Schema.png)

### Star Schema

![star schema](https://raw.githubusercontent.com/haoranwang99/Database-Azure-Divvy/main/re-modelling/star schema.png)

The design includes two **fact tables** (trip and payment) and multiple **dimension tables** (rider, account, station, date). This setup enhances querying flexibility for KPIs such as average ride time, trip frequency by age group, and revenue per user segment.

👉 [Star_Schema_Justification](https://github.com/haoranwang99/Database-Azure-Divvy/blob/main/re-modelling/Star_Schema_Justification.pdf)

---

## 🔄 Project Workflow

1. **Data Simulation & Loading**
   - Load all four datasets into **Azure PostgreSQL** using a Python ETL script.
2. **Data Extraction**
   - Extract data into **Azure Blob Storage** using Synapse’s ingestion tools.
3. **Data Staging**
   - Load flat files into **external staging tables** using serverless SQL pools.
4. **Data Modeling**
   - Transform raw data into **fact and dimension tables** using CETAS.
5. **Analytics & Visualization**
   - Use SQL queries for analytical insights into ride behavior and spending.

---

## 💻 Technologies Used

- **Azure PostgreSQL**
- **Azure Blob Storage**
- **Azure Synapse Analytics**
- **Python (ETL)**
- **SQL (CETAS, star schema transformation)**
- **pgAdmin** for PostgreSQL exploration

---

## 📁 Repository Structure

```
📂 Database-Azure-Divvy
├── ProjectDataToPostgres.py      # Python script to simulate OLTP loading
├── re-modelling/                 # Star and relational schema diagrams
├── SQL/                          # All SQL scripts for transformation
├── project.ipynb                 # Final project notebook
└── README.md                     # Project overview and instructions
```

---

## 👤 Author

**Haoran Wang**  
🔗 [GitHub Profile](https://github.com/haoranwang99)

---

## 📜 License

MIT License – open for use, collaboration, and exploration.

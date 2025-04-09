# 🚴‍♂️ Divvy Bike Data Warehouse Project (Azure Synapse Analytics)

This project leverages **Azure Synapse Analytics** to build a cloud-based **data warehouse** solution using data from the **Divvy bike-sharing program** in Chicago, Illinois, USA.

## 📊 Project Overview

Divvy is a popular bike-sharing system in Chicago. Riders can purchase passes and unlock bikes at various stations using kiosks or a mobile app. The anonymized trip data is publicly available and serves as the foundation for this project.

To simulate a production environment, the dataset has been enhanced with **mock account, rider, and payment information**. The primary goal is to **analyze ridership behavior and payment patterns** through the construction of a data warehouse solution.

---

## 🧠 Business Objectives

The data warehouse is designed to support the following business outcomes:

### 🚴‍♀️ Ride Duration Analysis
- By **date/time** (day of week, time of day)
- By **starting and ending station**
- By **rider age** at time of ride
- By **membership type** (member or casual)

### 💳 Revenue Analysis
- By **month, quarter, year**
- By **member** and their **age at account start**

### 📈 Advanced Member Spending Analysis
- Analyze **spending per member** based on:
  - Average number of rides per month
  - Average ride duration per month

---

## 📐 Star Schema Design

To effectively analyze the Divvy bike-sharing data, a star schema was designed based on the relational data tables. This schema facilitates efficient querying and reporting by organizing data into fact and dimension tables.

### Relational Schema

The initial relational schema outlines the structure of the source data tables and their relationships. This schema serves as the foundation for the star schema design.

![Relational Schema](https://raw.githubusercontent.com/haoranwang99/Database-Azure-Divvy/main/re-modelling/relational-schema.png)

### Star Schema

The star schema restructures the relational data into a central fact table surrounded by dimension tables, optimizing it for analytical queries.

![Star Schema](https://raw.githubusercontent.com/haoranwang99/Database-Azure-Divvy/main/re-modelling/star-schemas.png)

For a detailed explanation of the rationale behind using two fact tables, refer to the [Two Fact Tables Justification](https://github.com/haoranwang99/Database-Azure-Divvy/blob/main/re-modelling/Two_Fact_Tables_Justification.pdf) document.

---

## 🧭 Implementation Workflow

This project follows a structured data engineering pipeline:

### 1. Cloud Resource Provisioning
- Deploy an **Azure Database for PostgreSQL** to simulate OLTP data sources.
- Create an **Azure Synapse Analytics Workspace** using the built-in **serverless SQL pool**.
- Set up **Azure Blob Storage** for data staging and transformation.

### 2. Data Ingestion & Simulation
- Execute the `ProjectDataToPostgres.py` script to:
  - Generate tables and populate data in PostgreSQL.
  - Verify using database tools like `pgAdmin`.

### 3. Data Extraction
- Use **Synapse Ingest Wizard** to extract data from PostgreSQL into **Azure Blob Storage** as raw text files.

### 4. Staging & External Tables
- Load the ingested files from Blob Storage into **external staging tables** using Synapse serverless SQL pool.

### 5. Data Transformation & Modeling
- Design and implement a **star schema** with dimension and fact tables.
- Use **CETAS (CREATE EXTERNAL TABLE AS SELECT)** to transform and materialize data.

### 6. Analytics & Insights
- Query the star schema to support business objectives and derive actionable insights for ridership and revenue trends.

---

## 🛠️ Technologies Used

- **Azure Synapse Analytics**
- **Azure Blob Storage**
- **Azure Database for PostgreSQL**
- **Python** (ETL script)
- **SQL** (for transformations and querying)
- **pgAdmin** (for PostgreSQL access)

---

## 📁 Repository Structure

```
📂 Database-Azure-Divvy
├── ProjectDataToPostgres.py      # Python script to create and upload PostgreSQL data
├── re-modelling/                 # Star schema and relational model diagrams
├── SQL/                          # Folder for SQL scripts (transformation, staging, etc.)
└── README.md                     # You're reading it!
```

---

## 🚧 Status

🔧 Project is in progress – stay tuned for:
- Star schema implementation
- SQL transformation scripts
- Final analytics outputs and reports

---

## 👤 Author

**Haoran Wang**  
🔗 [GitHub Profile](https://github.com/haoranwang99)

---

## 📜 License

MIT License – feel free to fork and build upon this project!

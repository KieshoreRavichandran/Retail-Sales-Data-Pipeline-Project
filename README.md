# Retail-Sales-Data-Pipeline-Project

## 1. Introduction

This project implements an end-to-end retail sales data pipeline using Azure data services. The goal was to ingest data from various source systems, transform it, load it into a target system, and visualize the data to analyze sales trends. I assumed the role of a Data Engineer responsible for the implementation.

**Technologies Used:**

* Azure Data Factory (ADF)
* Azure Data Lake Storage Gen2 (ADLS Gen2)
* Azure SQL Database
* Power BI
* Draw.io (for architecture diagram)
* GitHub (for version control and submission)

## 2. Architecture

![Architecture Diagram](architecture_diagram/architecture.png)

The architecture diagram above illustrates the flow of data from the source systems (API, CSV, On-Prem SQL Server) through Azure Data Factory for ingestion and transformation, landing in Azure Data Lake Storage (Bronze and Silver layers), and finally into Azure SQL Database for consumption by Power BI.

* **Source Systems:** Provide raw data.
* **Azure Data Factory:** Orchestrates the pipeline and performs data transformations.
* **Azure Data Lake Storage Gen2:** Stores data in raw (Bronze) and transformed (Silver) formats.
* **Azure SQL Database:** Serves as the target relational database for processed data.
* **Power BI:** Used for creating visualizations and analyzing the data.

## 3. Implementation Steps

### 3.1 Setting up Azure Resources

I provisioned the following Azure services:

* Azure Data Lake Storage Gen2 account with hierarchical namespace enabled.
* Azure Data Factory instance.
* Azure SQL Database.
* Configured necessary linked services and integration runtimes in ADF.

### 3.2 Source System Integration

* **API:** [Describe how you connected to/simulated the API, the endpoint used, and the ADF activities (Web, Copy) for Bronze ingestion.]
* **CSV:** [Describe how you loaded the CSV data from Kaggle into the Bronze layer using ADF (Copy activity).]
* **On-Prem SQL Server:** [Describe how you extracted data from your local SQL Server (using SHIR if needed) and loaded it into the Bronze layer (Copy activity). Mention the `Customers`, `Products`, and `Sales` tables.]

### 3.3 Azure Data Lake Storage (ADLS)

Data was organized into two layers:

* **Bronze Layer:** Raw data ingested directly from the sources (e.g., `/bronze/api/raw_data.json`, `/bronze/csv/raw_data.csv`, `/bronze/sql/raw_data/`).
* **Silver Layer:** Cleansed and transformed data ready for loading into the target (e.g., `/silver/customers/cleaned.parquet`, `/silver/products/cleaned.parquet`, `/silver/sales/transformed.parquet`).

### 3.4 Data Transformation (Azure Data Factory Data Flow)

The following Data Flow(s) were created to transform data from Bronze to Silver:

* **[Name of your Data Flow(s)]:** [Describe the transformations performed (e.g., cleaning, data type conversions, joining, selecting columns) for each table (Customers, Products, Sales).]

### 3.5 Target System (Azure SQL Database)

Transformed data from the Silver layer was loaded into the `Customers`, `Products`, and `Sales` tables in Azure SQL Database using ADF Copy activities.

### 3.6 Data Visualization (Power BI)

Power BI Desktop was connected to the Azure SQL Database. A data model was created based on the relationships between the `Customers`, `Products`, and `Sales` tables. The following key visualizations were created:

* [List your key visualizations and the insights they provide (e.g., Total Sales over Time, Sales by Product Category, Top Customers, etc.)]

### 3.7 Data Validations

* **Row Count Check:** Row counts were validated after ingestion to the Bronze layer for each source to ensure data consistency. [Describe how you implemented these checks using Lookup or Get Metadata and If Condition activities.]
* **Pipeline JSON Validation:** The pipeline configurations were reviewed to ensure they are properly defined and valid as per ADF standards.

### 3.8 Triggers

* **Tumbling Window Trigger:** Configured for the API ingestion pipeline to run [Specify frequency and window size].
* **Scheduled Trigger:** Configured for the on-premises SQL Server ingestion pipeline to run [Specify schedule and frequency].

## 4. Project Deliverables

* **SQL Scripts:** Located in the `sql_scripts` folder:
    * `ddl.sql`: Contains the DDL script for creating the database schema.
    * `dml_sample_data.sql`: (Optional) Contains DML scripts for inserting sample data.
* **Pipeline JSON:** Exported JSON files of all ADF pipelines are located in the `pipeline_json` folder.
* **Documentation:** This `README.md` file serves as the project documentation.

## 5. Key Considerations and Challenges

* [Discuss any challenges you faced and how you overcame them.]
* [Mention any key design decisions and your reasoning.]
* [Highlight any limitations or potential future improvements.]

## 6. Conclusion

This project provided valuable hands-on experience in building a complete data pipeline in Azure. I gained practical skills in data ingestion, transformation, loading, validation, automation, and visualization using various Azure services.

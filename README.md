# Retail AI Analyst — End-to-End Data Pipeline & LLM-Powered Analytics

An end-to-end retail analytics project that integrates data from multiple sources, processes it through a cloud data pipeline, and enables users to ask natural-language questions about retail sales, products, stores, and trends through an interactive Streamlit application powered by a hosted Large Language Model (LLM) API.

## Project Overview

Retail businesses generate data across transactions, stores, products, and customer systems. Bringing these datasets together and making them accessible for analysis requires a structured data pipeline.

This project demonstrates a retail data engineering and AI analytics workflow using Azure data services, Databricks, and Streamlit. The pipeline organizes data into Bronze, Silver, and Gold layers, while the final application allows users to query retail data in natural language and receive answers with tables and numerical summaries.

## Architecture



**Pipeline:** Data Sources → Azure Data Factory → Azure Data Lake Storage (ADLS) → Databricks Medallion Architecture → Streamlit AI Analyst
## Retail AI Analyst — Workflow & Application

<p align="center">
  <img src="./Retail%20AI%20Analyst%20Data%20Pipeline.png" width="100%" alt="Retail AI Analyst Data Pipeline">
</p>

<p align="center">
  <img src="./Retail%20AI%20Analyst-1.png" width="85%" alt="Retail AI Analyst Streamlit Application">
</p>

## Key Features

### 1. Multi-Source Data Integration

- Transaction data from Azure SQL Database.
- Store information from Azure SQL Database.
- Product information from Azure SQL Database.
- Customer data retrieved from an API in JSON format.

### 2. ETL with Azure Data Factory

- Integrates data from multiple sources.
- Performs extraction and transformation steps.
- Loads data into Azure Data Lake Storage.
- Provides a structured workflow for data ingestion.
  
<p align="center">
  <img src="./Screenshot%20(222).png" width="85%" alt="Retail AI Analyst Additional Screenshot">
</p>

### 3. Centralized Data Storage with ADLS

- Uses Azure Data Lake Storage as the central data repository.
- Stores incoming data before downstream processing.
- Separates data ingestion from analytics and transformation.

### 4. Databricks Medallion Architecture

The data processing workflow follows three layers:

| Layer      | Purpose                                               |
| ---------- | ----------------------------------------------------- |
| **Bronze** | Stores ingested raw data.                             |
| **Silver** | Filters, cleans, and transforms data.                 |
| **Gold**   | Organizes business-ready data for analytical queries. |

The Gold dataset serves as the data source for the retail analytics application.
<p align="center">
  <img src="./Screenshot%20(233).png" width="85%" alt="Retail AI Analyst Additional Screenshot">
</p>


### 5. Streamlit AI Analyst

The interactive application enables users to ask questions about retail data using natural language.

**Application capabilities:**

- Preview the available sales dataset.
- Inspect dataset information.
- Ask questions about sales, products, stores, and trends.
- Retrieve relevant records and present results in tables.
- Display numerical summaries such as sales amount, quantity sold, and transaction counts.

A hosted LLM API powers the conversational interface, while the application uses the prepared Databricks Gold CSV dataset as its data source.

## Example Questions

- What were the sales in Delhi on New Year's Day 2025?
- Which store is located in Bangalore?
- Which products generate the highest sales?
- How do sales vary across stores and locations?
- What trends can be identified from the available retail data?

The accuracy and scope of answers depend on the available dataset and the application's data-retrieval logic.

## Technology Stack

| Technology                     | Purpose                                        |
| ------------------------------ | ---------------------------------------------- |
| Azure SQL Database             | Transaction, store, and product data sources   |
| Customer API (JSON)            | Customer data ingestion                        |
| Azure Data Factory             | ETL orchestration and data movement            |
| Azure Data Lake Storage (ADLS) | Centralized data storage                       |
| Databricks                     | Data transformation and Medallion Architecture |
| Python                         | Data processing and application logic          |
| Pandas                         | Dataset loading and manipulation               |
| Hosted LLM API                 | Natural-language question answering            |
| Streamlit                      | Interactive web application                    |

## Project Workflow

1. **Data ingestion:** Obtain transaction, store, and product data from Azure SQL Database and customer data from a JSON API.
2. **ETL pipeline:** Use Azure Data Factory to integrate the sources and move data into ADLS.
3. **Data storage:** Maintain the ingested datasets in centralized cloud storage.
4. **Data transformation:** Process the data in Databricks using Bronze, Silver, and Gold layers.
5. **Business-ready dataset:** Prepare the Gold CSV for retail analytics.
6. **AI-powered analysis:** Connect the Streamlit application to the prepared dataset and a hosted LLM API.
7. **Interactive insights:** Allow users to ask natural-language questions and view answers, tables, and numerical summaries.

## Running the Application

### Prerequisites

- Python 3.10 or a compatible version.
- Access to the hosted LLM API used by the application.
- The prepared Gold CSV dataset.

### Install dependencies

```bash
pip install streamlit pandas requests
```

Install any additional packages required by your implementation.

### Configure the API key

Store the LLM API key in an environment variable or Streamlit secrets. Do not commit API keys to GitHub.

For Streamlit secrets, create a `.streamlit/secrets.toml` file:

```toml
LLM_API_KEY = "your_api_key_here"
```

Ensure this file is excluded through `.gitignore`.

### Launch the application

```bash
streamlit run app.py
```

## Important Implementation Notes

- The demonstrated application uses a prepared Gold CSV as its data source; it should not be described as querying Databricks live unless that connection is implemented.
- The hosted LLM API provides language-generation capabilities. The application's data retrieval and prompt logic determine how answers are grounded in the retail dataset.
- The architecture describes the intended end-to-end workflow; cloud resources and pipeline orchestration should only be claimed as deployed if they have actually been configured and run.
- Validate important numerical results against the source dataset.

## Future Improvements

- Connect the application directly to Databricks SQL instead of relying on a static CSV.
- Add more advanced sales, product, and store-level analytics.
- Introduce automated data-quality checks and pipeline monitoring.
- Add charts and visual summaries to the conversational interface.
- Deploy the application to a managed hosting service.

---

**Project Domain:** Retail Analytics · Data Engineering · ETL · Cloud Data Platforms · LLM-Powered Analytics

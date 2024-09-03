# Summary of Data Transformation Phase and Challenge

![[Summary of Data Transformation Phase and Challenge.png]]
## Introduction
- Completion of data transformation phase.
- Summary of key concepts and a practical challenge for hands-on practice.

## Data Transformation Overview
### 1. Ingestion Phase Recap
- Ingest data from various sources (databases, APIs, files) using services like Data Factory, Synapse Pipelines, or Logic Apps.
- Store ingested data in the raw layer of a data lake in native formats (CSV, JSON).

### 2. Challenges with Raw Data
- Raw data often has quality issues (nulls, incorrect data, missing values).
- Original data format may not be suitable for analytics.
- Need for applying business rules and combining datasets for better insights.

### 3. Transformation Goals
- Transform raw data into a format suitable for querying.
- Aim to create a star or dimensional model with fact and dimension tables.

## Dimensional Modeling
### 1. Dimensional Model
- Denormalize data for easy querying.
- **Fact Tables**: Indicate measurable events (e.g., sales).
- **Dimension Tables**: Provide context to facts (e.g., products, customers, dates).

### 2. Data Lake Zones
- Decide on the number of zones (bronze, silver, gold) based on requirements.
- Use Delta format for transformed data from the second layer onwards.

## Azure Services for Transformation
### 1. Databricks
- Notebooks for writing code in SQL, Scala, R, or Python.
- Autoloader for automatic data processing.

### 2. DBT (Data Build Tool)
- Write transformations using SQL with Jinja templating.
- Use data warehouses like Databricks SQL Warehouses for executing queries.

### 3. Synapse Spark Pools
- Managed Apache Spark environment for data transformations.
- Integration with Synapse Pipelines for a unified toolset.

### 4. Data Factory Data Flows
- Visual, low-code/no-code approach for designing transformations.
- Use built-in activities for common transformations.

## Practical Challenge
### 1. Data Ingestion
- Ingest LEGO set data from a source (e.g., Rebrickable API) into the raw layer of a data lake.

### 2. Transformation and Modeling
- Create a dimensional model with the following tables:
  - **LEGO Sets Dimension**: Store all LEGO sets with relevant details.
  - **Own Sets Fact Table**: Track which LEGO sets are owned by users.
  - **User Profile Dimension**: Store user profiles from Rebrickable.
  - **Date Dimension**: Track purchase dates for LEGO sets.

### 3. Additional Requirements
- Combine data from multiple sources.
- Implement business rules for data transformation.
- Use Delta format for all transformed data.
- Register tables in a catalog for easy querying.

## Tools and Services
### 1. Databricks
- Use notebooks for transformation and Autoloader for automated processing.

### 2. Data Factory
- Orchestrate the ingestion and transformation processes.

### 3. Synapse
- Use Synapse Spark Pools and Data Flows as alternatives to Databricks.

### 4. Security
- Implement proper data security measures.
- Use Azure Key Vault for storing secrets.

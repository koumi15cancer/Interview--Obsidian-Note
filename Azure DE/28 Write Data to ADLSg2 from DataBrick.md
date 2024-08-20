# Transforming and Persisting Data with Azure Databricks

![[Transforming and Persisting Data with Azure Databricks.png]]

## Introduction
- Focus on persisting data transformation results in a data lake.
- Discusses saving transformed data to various targets (e.g., Azure SQL Database, Synapse SQL Pool).

## Configuration for Data Persistence
- **Cluster-Level Configuration**: Move connectivity configuration to the cluster level for persistence across notebooks.

## Steps for Data Persistence

### 1. Loading and Transforming Data
- Load JSON data into a DataFrame.
- Transform JSON data into a tabular format.

### 2. Saving Data to Data Lake
- **Create Containers**: Set up new containers (e.g., "curated") for storing data.
- **Save Data as Delta Files**: Write transformed data back to the data lake as Delta files.

### 3. Reading Saved Data
- Verify the data is saved correctly by reading it back into Databricks.

## Creating and Managing Tables

### 1. Managed Tables
- Register tables in Databricks' catalog.
- Data is stored in Databricks-managed storage.

### 2. External Tables
- Store data in user-managed data lakes.
- Register external tables in the catalog, specifying the location of data storage.

## Advantages of Using the Catalog
- **User-Friendly Access**: Allows users to access data without needing to know the storage location.
- **Consistent Data Management**: Provides a centralized catalog of available data tables.

## Performing Data Operations

### 1. Inserting Data
- Insert new rows into the table using SQL statements.

### 2. Updating Data
- Update existing rows with new values.

### 3. Deleting Data
- Remove specific rows from the table.

## Advanced Features

### 1. Identity Columns
- Automatically generate unique IDs for rows using the identity property.

## Summary
- Multiple methods for persisting data transformations.
- Importance of configuring and managing data storage effectively.
- Using Databricks' catalog for easier data access and management.

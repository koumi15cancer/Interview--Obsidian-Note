# Data Transformation with Data Flows in Azure Synapse Analytics
![[Data Transformation with Data Flows in Azure Synapse Analytics.png]]
## Introduction
- Azure Databricks, Spark pools, and DBT typically require coding in Python, Scala, R, or SQL.
- Data flows provide a visual, low-code/no-code method for data transformation.

## Typical BI Workflow
- **Data Sources**: Files (CSV, JSON, XML), databases, APIs.
- **Data Ingestion**: Using Azure Data Factory (ADF) to load data into Azure Data Lake Storage Gen2 (ADLS Gen2).
- **Data Layers**:
  - **Raw Layer**: Stores data in native formats.
  - **Transformed Layer**: Data transformed using data flows.

## Using Data Flows in Azure Synapse
- **Purpose**: Enable data transformation without writing extensive code.
- **Integration**: Available within Azure Data Factory and Synapse Pipelines.

## Configuration and Setup
1. **Create Data Flow**: Start in the Develop tab of Synapse.
2. **Define Source**: Indicate where the data is coming from (e.g., ADLS Gen2).

## Data Flow Steps
- **Source Options**: Integration dataset, inline dataset, workspace database.
- **Schema Drift**: Allows flexibility for changes in data schema.
- **Projection Tab**: Displays schema of input and output data.
- **Data Preview**: Provides a preview of the actual data after each transformation step.

## Implementing Transformations
1. **Exploding Arrays**: Use the Flatten transformation to handle nested arrays.
2. **Handling Nulls**: Use Derived Column transformation to replace or manage null values.
3. **Filtering Data**: Use Filter transformation to exclude unwanted rows.
4. **Removing Unnecessary Columns**: Use Select transformation to choose relevant columns.
5. **Changing Data Types**: Use Cast transformation to convert data types.
6. **Adding Business Logic**: Use Derived Column transformation to apply conditional logic.

## Syncing Data
- **Saving Data**: Use the Sync transformation to write data back to ADLS Gen2 in Delta format.

## Data Flow Transformations Overview
- **Multiple Inputs/Outputs**: Join, conditional split, exists, union, lookup.
- **Schema Modifiers**: Derived column, select, aggregate, surrogate key, pivot, unpivot, window, rank, external call, cast.
- **Formatters**: Flatten, parse, stringify.
- **Row Modifiers**: Filter, sort, alter row, assert.
- **Flowlets**: Modularize frequent transformations.
- **Sync**: Dump data from a data flow to a destination.

## Advanced Configuration
1. **Integration Runtime**: Configure for debugging and execution.
2. **Performance Optimization**: Use the Optimize tab for improving performance.
3. **Data Quality Checks**: Use Assert transformation for data validation.

## Summary
- Data flows provide an easy-to-use, visual approach to data transformation.
- Suitable for non-programmers and scenarios where minimal coding is preferred.
- Limitations: Less flexible compared to full coding environments like Databricks or Spark pools.
- Integration: Available within Azure Data Factory and Synapse Pipelines for seamless data processing.

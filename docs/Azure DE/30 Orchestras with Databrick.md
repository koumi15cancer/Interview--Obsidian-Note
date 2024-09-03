# Orchestrating Azure Databricks Notebooks in BI Workflow

![[Orchestrating Azure Databricks Notebooks in BI Workflow.png]]

## Introduction
- Azure Databricks is used for data transformation.
- Focus on automating the execution of Databricks notebooks within a production environment, avoiding manual execution.

## Typical BI Workflow
- **Data Sources**: Various sources like files, databases, APIs.
- **Data Ingestion**: Using Azure Data Factory (ADF) to ingest data into Azure Data Lake Storage Gen2 (ADLS Gen2).
- **Data Layers**:
  - **Raw Layer**: Stores data in its native format.
  - **Transformed Layer**: Data transformed using Databricks.

## Orchestrating Databricks Notebooks
- **Orchestration with ADF**: Use ADF pipelines to orchestrate the execution of Databricks notebooks.
- **Creating Pipelines**: Extend ADF pipelines to include data transformation steps using Databricks.

## Setting Up Databricks and ADF
1. **Create a Databricks Notebook**: A simple notebook to demonstrate the process.
2. **Create an ADF Pipeline**: Integrate Databricks notebook execution into the pipeline.

## Linking ADF with Databricks
- **Create Linked Service**: In ADF, create a linked service to connect to Databricks.
  - Use appropriate authentication methods (Managed Identity or Personal Access Token).
- **Configure Notebook Activity**: Use the notebook activity in ADF to specify which notebook to execute.

## Authentication and Permissions
- **Personal Access Token**: Used for initial demonstration but not recommended for production.
- **Managed Identity**: Preferred method for secure and automated execution.
  - Ensure the managed identity has the necessary permissions in Databricks.

## Cluster Types in Databricks
- **Interactive Cluster**: Used for development and interactive workloads.
- **Job Cluster**: Used for automated production workloads, more cost-effective.

## Advanced Configuration
1. **Parameterizing Notebooks**: Use Databricks widgets to pass parameters from ADF to the notebook.
2. **Cluster Configuration**: Define job clusters in the linked service configuration for on-demand creation.

## Example Execution
1. **Setup and Execution**: Configure and execute the pipeline to run the Databricks notebook.
2. **Logging and Monitoring**: Monitor the execution logs and ensure the notebook runs with the provided parameters.

## Additional Orchestration Options
- **Databricks Workflows**: Databricks' native orchestration tool to schedule and run notebooks.

## Summary
- **Integration with ADF**: Databricks notebooks can be orchestrated using ADF for automated and efficient data transformation.
- **Managed Identity**: Recommended for secure authentication.
- **Job Clusters**: Preferred for production workloads to reduce costs.
- **Dynamic Parameters**: Use widgets to pass parameters from ADF to Databricks notebooks.

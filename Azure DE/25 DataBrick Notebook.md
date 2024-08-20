# Exploring Azure Databricks: Notebooks, Spark, and Data Transformation

![[Exploring Azure Databricks_ Notebooks, Spark, and Data Transformation.png]]

## Introduction
This article revisits Azure Databricks, explaining the differences between trial and premium tiers and demonstrating how to use notebooks and Spark for data transformations.

## Trial vs. Premium Tier
- **Trial Period:** Free for two weeks, applicable only to Databricks usage charges (DBUs).
- **Premium Tier:** Paid to both Databricks and Azure. Premium offers enhanced security features, such as role-based access control, authentication, audit logs, and conditional authentication.

## Key Concepts in Azure Databricks
- **Clusters:** You can create multiple clusters with different configurations for various purposes. Be mindful of terminating unused clusters to avoid charges.
- **Workspace:** Organize notebooks and files logically within the workspace. The shared folder is accessible to all users, while private folders are user-specific.

## Databricks Notebooks
- **Languages:** Support for Python, SQL, Scala, and R. Each notebook has a default language, but cells can switch languages as needed.
- **DBUtils:** Databricks Utilities provide commands to interact with the environment programmatically, such as file system operations (e.g., listing directories, copying files).

## Practical Example
1. **Connecting to Data Lake:** Authenticate using account keys (not recommended for production).
2. **Sample Datasets:** Utilize built-in sample datasets for practice. Use `dbutils.fs.ls` to list available datasets.
3. **Loading Data:** Load data from sample datasets or your own data lake into a dataframe.
4. **Displaying Data:** Use `display` function to visualize data in an interactive table format.

## Data Transformation
- **Infer Schema:** Automatically infer the schema of a CSV file to get appropriate data types.
- **Explicit Schema:** Define the schema explicitly to avoid the overhead of inferring it.
- **SQL and Python Interoperability:** Switch between SQL and Python within the same notebook. Create temporary views to share data between languages.
- **Visualization:** Use built-in visualization tools to create charts and graphs from data.

## Practical Tips
- **Avoid Hardcoding Secrets:** Do not store sensitive credentials in notebooks.
- **Consistent Language Use:** Stick to one language within a project for easier maintenance.
- **Workspace Management:** Organize and set permissions for folders and notebooks within the workspace.

## Example Code

### Listing Sample Datasets
```python
dbutils.fs.ls("/databricks-datasets")


# Load data into a dataframe
df = spark.read.format("delta").load("/databricks-datasets/learning-spark-v2/people/people-10m.delta")

# Display the dataframe
display(df)

#Infer Schema
df = spark.read.format("csv").option("header", "true").option("inferSchema", "true").load("path/to/csv/file")
display(df)

#Explicit Schema
from pyspark.sql.types import StructType, StructField, IntegerType, StringType, BooleanType, TimestampType

schema = StructType([
    StructField("CustomerID", IntegerType(), True),
    StructField("NameStyle", BooleanType(), True),
    StructField("FirstName", StringType(), True),
    StructField("MiddleName", StringType(), True),
    StructField("LastName", StringType(), True),
    StructField("ModifiedDate", TimestampType(), True)
])

df = spark.read.format("csv").schema(schema).load("path/to/csv/file")
display(df)

#SQL Query
SELECT LastName, COUNT(*) as NameCount
FROM my_data
GROUP BY LastName
ORDER BY NameCount DESC

#Visualization

`display(df)`


## Conclusion

Azure Databricks is a powerful platform for data transformation, offering extensive features for data engineers and scientists. It supports multiple languages, easy data manipulation, and visualization capabilities, making it a versatile tool for various data processing needs.
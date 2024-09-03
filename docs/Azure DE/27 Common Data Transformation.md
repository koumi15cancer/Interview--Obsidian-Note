# Transforming JSON Data into a Tabular Format with Azure Databricks

![[Transforming JSON Data into a Tabular Format with Azure Databricks.png]]

## Introduction
This article discusses how to transform raw JSON data into a structured tabular format using Azure Databricks. The process involves several common data transformations.

## Data Overview
The JSON file contains complex structures like nested arrays. The goal is to extract relevant data into a flat, tabular format.

## Data Transformation Steps

### 1. Loading and Inspecting Data
- **Load JSON File**: The data is loaded into a DataFrame.
- **Inspect Data**: The JSON structure is inspected, revealing nested arrays and unnecessary technical columns.

### 2. Flattening the JSON Structure
- **Exploding Arrays**: The `explode` function is used to flatten arrays, creating a row for each object in the array.

```python
from pyspark.sql.functions import explode

df2 = df.withColumn("exploded_array", explode("results"))
```
- **Inspecting the Flattened Data**: The resulting DataFrame has duplicated technical columns and the exploded array as individual rows.

### 3. Transforming Data using SQL

- **Creating a Temporary View**: The DataFrame is made available for SQL queries.

```python
df2.createOrReplaceTempView("my_data")
```
- **Extracting Fields**: SQL queries are used to extract fields from the exploded array into individual columns.

```sql
SELECT
  exploded_array.last_modified_DT AS last_modified_date_time,
  exploded_array.name,
  exploded_array.number_of_parts,
  exploded_array.image_URL,
  exploded_array.set_number,
  exploded_array.set_URL
FROM my_data

```

**Removing Unnecessary Columns**: Technical columns are excluded from the query.

```sql
SELECT
  exploded_array.last_modified_DT AS last_modified_date_time,
  exploded_array.name,
  exploded_array.number_of_parts,
  exploded_array.image_URL,
  exploded_array.set_number,
  exploded_array.set_URL
FROM my_data

```

### 4. Renaming Columns

- **User-Friendly Column Names**: Columns are renamed to be more descriptive and user-friendly.

```sql
SELECT
  exploded_array.last_modified_DT AS last_modified_date_time,
  exploded_array.name AS minifig_name,
  exploded_array.number_of_parts AS parts_count,
  exploded_array.image_URL AS image_link,
  exploded_array.set_number AS set_id,
  exploded_array.set_URL AS set_link
FROM my_data

```

### 5. Converting Data Types

- **Date and Number Conversion**: Columns are converted to appropriate data types (e.g., date, integer

```sql
SELECT
  CAST(exploded_array.last_modified_DT AS DATE) AS last_modified_date,
  CAST(exploded_array.last_modified_DT AS TIMESTAMP) AS last_modified_date_time,
  CAST(exploded_array.number_of_parts AS INTEGER) AS parts_count,
  exploded_array.name AS minifig_name,
  exploded_array.image_URL AS image_link,
  exploded_array.set_number AS set_id,
  exploded_array.set_URL AS set_link
FROM my_data

```
### 6. Adding Business Logic

- **Conditional Logic**: New columns are added based on business rules using SQL case statements.

```sql
SELECT
  exploded_array.last_modified_DT AS last_modified_date_time,
  exploded_array.name AS minifig_name,
  exploded_array.number_of_parts AS parts_count,
  exploded_array.image_URL AS image_link,
  exploded_array.set_number AS set_id,
  exploded_array.set_URL AS set_link,
  CASE
    WHEN exploded_array.name LIKE '%Toy%' THEN 'Toy'
    WHEN exploded_array.name LIKE '%Droid%' THEN 'Droid'
    ELSE 'Other'
  END AS minifig_type
FROM my_data

```

### 7. Handling Duplicates

- **Finding Duplicates**: Duplicates are identified based on key columns.

```sql
SELECT
  exploded_array.set_number,
  COUNT(*)
FROM my_data
GROUP BY exploded_array.set_number
HAVING COUNT(*) > 1
ORDER BY COUNT(*) DESC

```

**Removing Duplicates**: Window functions are used to keep only the latest version of each record.

```sql
WITH ranked_data AS (
  SELECT
    *,
    ROW_NUMBER() OVER (PARTITION BY exploded_array.set_number ORDER BY exploded_array.last_modified_DT DESC) AS rn
  FROM my_data
)
SELECT * FROM ranked_data WHERE rn = 1

```

### 8. Handling Null Values

- **Replacing Nulls**: Null values are replaced with default values.

```sql
SELECT
  COALESCE(exploded_array.image_URL, 'Not Available') AS image_link,
  exploded_array.last_modified_DT AS last_modified_date_time,
  exploded_array.name AS minifig_name,
  exploded_array.number_of_parts AS parts_count,
  exploded_array.set_number AS set_id,
  exploded_array.set_URL AS set_link
FROM my_data

```

## Conclusion

Azure Databricks provides powerful tools for transforming JSON data into structured tabular formats. This article demonstrated how to flatten nested structures, rename columns, convert data types, add business logic, handle duplicates, and manage null values. These transformations are essential for preparing data for analysis and business use.

Reference:
[https://itziktsql.com/books](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXVBdXRBOVhwSktqTkRUTkdBVlFvNlBEX3BVZ3xBQ3Jtc0tscnE1YnAxVS1ucTNTMVR0SjF1Tk9XQnA3cFNJOExtbzBIMHBqYUNIQi1LYS0xSTJTWXNIemJKek1nSXRTWmVsSXhSMEZhbXZ1djc5MGdKNW9jb2lYb0ZNRUNUMkJVNkVPOTd6RzNNckZzak5PVUxwTQ&q=https%3A%2F%2Fitziktsql.com%2Fbooks&v=4oGCTjl3FvA)

# Understanding Dimensional Modeling and Data Lake Organization

![[Understanding Dimensional Modeling and Data Lake Organization.png]]

## Introduction
Dimensional modeling and data lake organization are crucial topics for data engineers. This article explores how to handle changing dimensions in data modeling and how to organize data layers within a data lake effectively.

## Handling Changing Dimensions
In dimensional modeling, it's essential to manage changes in dimension data accurately. The following are common methods to handle such changes:

### Slowly Changing Dimensions (SCDs)
- **SCD Type 1:** This method simply overwrites existing data without keeping any history. It's useful when historical data changes are not significant. For instance, if an employee's last name changes, the new name replaces the old one.
- **SCD Type 2:** This approach maintains a full history by creating new rows for each change, with validity periods to track when each version was active. It's beneficial for scenarios where historical data needs to be preserved.
- **SCD Type 3:** This type retains only the previous version of the data by adding extra fields to store both the current and prior values. This method is suitable when only the most recent change history is needed.

### Practical Examples
- When a product is rebranded, businesses might use SCD Type 2 to keep track of all previous names or SCD Type 1 to overwrite the old name, based on their requirements.
- For employee data, such as name changes due to marriage, different SCD types can be used depending on whether the history of the name changes needs to be preserved.

## Organizing Data Layers in a Data Lake
Organizing data within a data lake is essential for ensuring efficient data processing and analysis. Various architectures and approaches can be adopted for this purpose.

### Medallion Architecture
1. **Bronze Layer:** Raw data without transformations, containing possible quality issues and duplicates.
2. **Silver Layer:** Cleaned and filtered data, prepared for further analysis but still in a detailed format.
3. **Gold Layer:** Aggregated and business-ready data, suitable for final analysis and reporting.

### Challenges with Medallion Architecture
- **Ambiguity:** Lack of detailed guidelines on transformations at each layer.
- **Complexity:** May not fit all business needs; sometimes more layers are needed to handle complex transformations and ensure data quality.

### Alternative Approaches
- **Microsoft’s Approach:** Suggests using two physical data lakes with multiple containers within each for more detailed processing stages.
- **Custom Layers:** Creating more than three layers if necessary, based on the complexity of the data processing and the need for maintainability and support.

### Best Practices
- **Communication:** Ensure all team members understand the purpose and rules of each layer to maintain consistency and clarity.
- **Customization:** Adapt the number of layers to fit the specific needs of the project, avoiding unnecessary complexity but ensuring sufficient detail to handle the data transformations properly.

## Conclusion
When dealing with changing dimensions, utilize established patterns like SCDs to handle data changes effectively. For organizing data in a data lake, understand different architectural patterns like the Medallion architecture and Microsoft’s guidelines, and choose an approach that balances simplicity with the need for detailed data processing.

Reference:
[Data lake zones and containers - Cloud Adoption Framework | Microsoft Learn](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/cloud-scale-analytics/best-practices/data-lake-zones)
[(1) Post | LinkedIn](https://www.linkedin.com/posts/sqlbi_medallion-databricks-fabric-activity-7140269823653044224-Tg4c/?utm_source=share&utm_medium=member_desktop)
[Behind the Hype - The Medallion Architecture Doesn't Work (youtube.com)](https://www.youtube.com/watch?v=fz4tax6nKZM)

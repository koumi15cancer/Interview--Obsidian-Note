- self intro - 5'
- Daily work ?
- ---> Dig in indepth questions


## Azure questions
- Storage Account
- Data Factory
- Dynamic Data Factory
- Azure DataFactory Integration Runtime
- Error Handling Azure Data Factory
- Executing ADF Pipeline
- Anonymous Access, Access Key
- Key Vault, Identity Manager
- SAS - Shared Access Signature
- ACL - Access Control List
- ARM Base CIDCD - Selective AF ADF

Datawarehouse vs datalake ? ([What is the difference between a data lake and a data warehouse? · Start Data Engineering](https://www.startdataengineering.com/post/data-lake-warehouse-diff/))
Datawarehouse vs data lake house? 

ETL vs ELT vs EL ? 

[Whats the difference between ETL & ELT? · Start Data Engineering](https://www.startdataengineering.com/post/elt-vs-etl/)

- Usage for which scenario ?
- Pattern



# Data Pipeline Design Patterns

## Data Flow
- [Data Pipeline Design Patterns - #1. Data flow patterns · Start Data Engineering](https://www.startdataengineering.com/post/design-patterns/)
## Source & Sink
- ### Source Replayability
- ### Source Ordering
- ### Sink Overwritability


## Data pipeline patterns
### Extraction patterns
- #### Time ranged
- #### Full Snapshot
- #### Lookback
- #### Streaming

### Behavioral
- ####  Idempotent
- #### Self-healing

### Structural
- #### Multi-hop pipelines
- #### Conditional/ Dynamic pipelines
- #### Disconnected data pipelines

## SCD ( Slowly Changing Dimension)


[6 Steps to Avoid Messy Data in Your Warehouse · Start Data Engineering](https://www.startdataengineering.com/post/n-steps-avoid-messy-dw/#2-six-steps-for-a-clean-data-warehouse)
## 2.3. Good input data is necessary for a good data warehouse

No matter how good your data model and pipelines are, if your input data is wrong, the data in your warehouse will be unusable (Garbage In, Garbage Out).

It’s critical to ensure that your input datasets are meeting your expectations before you use them in your data pipelines. Use the five verticals below to define expectations for your input data.

1. **`Data Freshness`**: Is the data as recent as expected?
2. **`Data Types`**: Does the input data type change? Have columns been added/modified without notifying the data team?
3. **`Data Constraints`**: Does the input data respect constraints such as uniqueness, non-null, relationship, and enum set?
4. **`Data Size Variance`**: Does the input data size remain consistent across loads (or overtime periods)?
5. **`Data Metric Variance`**: Do the critical metrics in the input data remain consistent across loads (or overtime periods)?


# Metadata & Logging

[Data Engineering Best Practices - #2. Metadata & Logging · Start Data Engineering](https://www.startdataengineering.com/post/de_best_practices_log/)


## Window Functions

[6 Key Concepts, to Master Window Functions · Start Data Engineering](https://www.startdataengineering.com/post/6-concepts-to-clearly-understand-window-functions/)


## Scale data pipeline

[How to Scale Your Data Pipelines · Start Data Engineering](https://www.startdataengineering.com/post/scale-data-pipelines/)


# Data idempotent
[How to make data pipelines idempotent · Start Data Engineering](https://www.startdataengineering.com/post/why-how-idempotent-data-pipeline/)

# Spark
[3 Key techniques, to optimize your Apache Spark code · Start Data Engineering](https://www.startdataengineering.com/post/how-to-optimize-your-spark-jobs/)

# DB
Columnar vs Row based
[What Does It Mean for a Column to Be Indexed · Start Data Engineering](https://www.startdataengineering.com/post/what-does-it-mean-for-a-column-to-be-indexed/)


- **Can you explain the key differences between columnar storage and row-based storage? When would you choose one over the other?**
    
- **What types of workloads are best suited for columnar storage, and why? Conversely, when might you prefer a row-based storage format?**
    
- **In the context of data analytics, how does columnar storage improve query performance compared to row-based storage?**
    
- **How does the compression of data differ in columnar vs. row storage systems? Can you describe the impact this has on storage efficiency and query performance?**
    
- **What are some potential drawbacks of using columnar storage for transactional systems?**
    
- **Have you worked with databases that support both columnar and row-based storage, such as SQL Server or Oracle? How do you decide which storage format to use for specific tables or use cases?**
    
- **How does the use of columnar storage impact data loading and ETL performance compared to row-based storage? What strategies can optimize this process?**
    
- **In a data lake or data warehouse setup, what benefits does columnar storage provide for OLAP (Online Analytical Processing) workloads?**
    
- **Can you discuss a scenario in your experience where you switched from row-based to columnar storage (or vice versa) and the impact it had on performance or data accessibility?**
    
- **How does columnar storage impact indexing and partitioning strategies compared to traditional row storage?**
- 
-------------------


- **Can you explain what a deadlock is in the context of row-based databases? How does it occur, and what are some common scenarios where deadlocks might happen?**
    
    - "A deadlock in row-based databases occurs when two or more transactions are waiting on each other to release locks on rows, resulting in a standstill where none of the transactions can proceed. Common scenarios include concurrent updates where Transaction A locks Row 1 and waits for Row 2, while Transaction B locks Row 2 and waits for Row 1. Without intervention, these transactions would be indefinitely stuck."
- **What are some differences in how deadlocks might occur in row-based storage versus column-based storage?**
    
    - "Deadlocks are more common in row-based storage due to the finer granularity of row-level locks. In contrast, column-based databases often use a different locking mechanism, such as partition or block-level locking, which can reduce the likelihood of row-level contention. However, if multiple updates are required on columns that overlap across rows, deadlocks can still occur but are generally less frequent."
- **When a deadlock occurs, how does a database typically detect it, and what actions are taken to resolve it?**
    
    - "Databases typically use deadlock detection algorithms, such as wait-for graphs, to detect cycles where transactions are stuck in a wait chain. When a deadlock is identified, the database chooses a 'victim' transaction to roll back, based on factors like resource consumption and lock duration. This releases the locks and allows other transactions to continue."
- **What strategies do you employ to prevent deadlocks in row-based databases, particularly in systems with high concurrent access?**
    
    - "One effective strategy is to access resources in a consistent order across all transactions. For example, ensuring that transactions always lock rows in a specific sequence reduces the chances of circular wait conditions. Additionally, keeping transactions short and reducing the scope of row locks by committing frequently can lower the likelihood of deadlocks."
- **Can you describe a time when you encountered a deadlock issue in a database? How did you diagnose and resolve it?**
    
    - "In a previous role, we had frequent deadlocks in a transactional system with high update frequency. We diagnosed it using the database's deadlock trace logs and found that inconsistent ordering in updates was the root cause. We modified the application logic to acquire locks in a consistent order and implemented row-level locking only where necessary. This significantly reduced deadlock occurrences."
- **How does transaction isolation level impact the likelihood of deadlocks? Can you explain how using different isolation levels (e.g., Read Committed, Serializable) affects concurrency control?**
    
    - "Higher isolation levels like Serializable reduce concurrency by restricting access to data, which can increase the chance of deadlocks because of prolonged lock holding. In contrast, lower levels, like Read Committed, release locks sooner, which can reduce deadlock frequency but may allow phenomena like non-repeatable reads. Choosing the right level depends on balancing data consistency needs with performance."
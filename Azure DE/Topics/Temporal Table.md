### Detailed Summary of Temporal Tables in SQL Server

**Temporal tables**, or system-versioned temporal tables, enable the tracking of historical data changes by maintaining two tables: the current table and a history table. This feature supports auditing, data recovery, and trend analysis.

#### Key Features:
- **System-Versioning**: Automatically keeps history of all changes.
- **Period Columns**: `ValidFrom` and `ValidTo` columns indicate the time range for which each row is valid.
- **Historical Data Storage**: A separate history table stores all versions of the data rows.

#### Use Cases:
1. **Auditing Changes**: Track how data has changed over time.
2. **Historical Data Analysis**: Reconstruct the state of the data at any point in time.
3. **Trend Analysis**: Analyze how data changes over periods.
4. **Data Recovery**: Restore data to a previous state if changes were incorrect or accidental.

#### Creating a Temporal Table:
A temporal table requires:
- A primary key.
- Two datetime2 columns for the validity period.
- System-versioning to be enabled.

**Example:**
```sql
CREATE TABLE dbo.Employee (
    [EmployeeID] INT NOT NULL PRIMARY KEY,
    [Name] NVARCHAR(100),
    [Position] VARCHAR(100),
    [Department] VARCHAR(100),
    [Address] NVARCHAR(1024),
    [AnnualSalary] DECIMAL(10, 2),
    [ValidFrom] DATETIME2 GENERATED ALWAYS AS ROW START,
    [ValidTo] DATETIME2 GENERATED ALWAYS AS ROW END,
    PERIOD FOR SYSTEM_TIME (ValidFrom, ValidTo)
)
WITH (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.EmployeeHistory));
```
### Managing Temporal Tables

**Querying Historical Data**: Use the `FOR SYSTEM_TIME` clause.

**Altering Temporal Tables**: You can add or drop columns, change indexes, or even switch off system-versioning temporarily.

**Dropping Temporal Tables**: You must first turn off system-versioning.

#### Example of Querying Historical Data:
```sql
SELECT * 
FROM dbo.Employee 
FOR SYSTEM_TIME AS OF '2021-01-01T00:00:00.0000000'

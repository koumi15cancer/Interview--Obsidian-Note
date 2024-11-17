## What is a Database?

A database is an organized collection of structured information, or data, typically stored electronically in a computer system. A database is usually controlled by a Database Management System (DBMS). Together, the data and the DBMS, along with the applications that are associated with them, are referred to as a database system, often shortened to just database.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-what-is-dbms "Permalink")What is DBMS?

A database typically requires a comprehensive database software program known as a Database Management System (DBMS). A DBMS serves as an interface between the database and its end-users or programs, allowing users to retrieve, update, and manage how the information is organized and optimized. A DBMS also facilitates oversight and control of databases, enabling a variety of administrative operations such as performance monitoring, tuning, and backup and recovery.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-components "Permalink")Components

Here are some common components found across different databases:

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-schema "Permalink")Schema

The role of a schema is to define the shape of a data structure, and specify what kinds of data can go where. Schemas can be strictly enforced across the entire database, loosely enforced on part of the database, or they might not exist at all.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-table "Permalink")Table

Each table contains various columns just like in a spreadsheet. A table can have as meager as two columns and upwards of a hundred or more columns, depending upon the kind of information being put in the table.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-column "Permalink")Column

A column contains a set of data values of a particular type, one value for each row of the database. A column may contain text values, numbers, enums, timestamps, etc.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-row "Permalink")Row

Data in a table is recorded in rows. There can be thousands or millions of rows in a table having any particular information.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-types "Permalink")Types

![database-types](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/databases-and-dbms/database-types.png)

Below are different types of databases:

- **[SQL](https://karanpratapsingh.com/courses/system-design/sql-databases)**
- **[NoSQL](https://karanpratapsingh.com/courses/system-design/nosql-databases)**
    - Document
    - Key-value
    - Graph
    - Timeseries
    - Wide column
    - Multi-model

SQL and NoSQL databases are broad topics and will be discussed separately in [SQL databases](https://karanpratapsingh.com/courses/system-design/sql-databases) and [NoSQL databases](https://karanpratapsingh.com/courses/system-design/nosql-databases). Learn how they compare to each other in [SQL vs NoSQL databases](https://karanpratapsingh.com/courses/system-design/sql-vs-nosql-databases).

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-challenges "Permalink")Challenges

Some common challenges faced while running databases at scale:

- **Absorbing significant increases in data volume**: The explosion of data coming in from sensors, connected machines, and dozens of other sources.
- **Ensuring data security**: Data breaches are happening everywhere these days, it's more important than ever to ensure that data is secure but also easily accessible to users.
- **Keeping up with demand**: Companies need real-time access to their data to support timely decision-making and to take advantage of new opportunities.
- **Managing and maintaining the database and infrastructure**: As databases become more complex and data volumes grow, companies are faced with the expense of hiring additional talent to manage their databases.
- **Removing limits on scalability**: A business needs to grow if it's going to survive, and its data management must grow along with it. But it's very difficult to predict how much capacity the company will need, particularly with on-premises databases.
- **Ensuring data residency, data sovereignty, or latency requirements**: Some organizations have use cases that are better suited to run on-premises. In those cases, engineered systems that are pre-configured and pre-optimized for running the database are ideal.
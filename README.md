Retail Sales Data Engineering Project
1. Data Background
The dataset utilized originates from TPCDS, a well-known dataset designed for database testing, with a specific emphasis on Retail Sales. It encompasses sales records from both websites and catalogs, along with detailed information on inventory levels for each item within every warehouse. Moreover, it incorporates 15 dimensional tables containing valuable information about customers, warehouses, items, and more. The dataset is divided into two parts:

1.1 RDS
Postgres DB in AWS RDS: All tables, except for the inventory tables, are stored here.
These tables are refreshed every day with the latest sales data, requiring daily ETL processes.
1.2 S3 Bucket
Inventory Table: Stored in an S3 bucket.
Each day, a new file containing the most recent data is deposited into the S3 bucket.
The inventory table typically registers data at the end of each week, leading to one entry per item per warehouse on a weekly basis.
2. Metabase Requirements
Our ultimate objective is to generate dashboards and reports using the BI tool Metabase. It is essential to comprehend the requirements for Metabase dashboards and reports:

Determine the top and bottom-performing items of the week by analyzing sales amounts and quantities.
Show items with low inventory levels on a weekly basis.
Identify items with low stock levels, including their associated week and warehouse numbers, marked as "True".
Based on these requirements, we need to know the sales amounts and quantities, inventory details from the inventory table, and a synthesis of sales and inventory data for metric calculations. Regarding dimension tables, we need information about items, weeks, warehouses, etc., requiring the dimension tables Item, Warehouse, and Date.

However, if we only based on the above business requirements in Metabase, it's challenging to define the data model. So we need to introduce new columns and tables (Data Model) in the data warehouse to meet these reporting requirements.

3. Project Infrastructure
The entire infrastructure for this project is constructed in the cloud:

Servers: Several servers are created on the AWS cloud.
Tools: Various tools are installed on these servers, including Airbyte for data ingestion and Metabase as the BI tool for building dashboards.
Cloud Data Warehouse: An account is created on Snowflake, which is used to store data and perform data transformation.
AWS Lambda: AWS Lambda, a serverless service, is used to ingest data from AWS data storage (S3).
4. Part One: Data Ingestion
The first part of the project involves Data Ingestion. It entails connecting to two data sources: the Postgres database and the AWS S3 bucket.

Airbyte: Establish a connection to the raw_st schema of the Postgres database on AWS RDS, and transfer all tables to the Snowflake data warehouse.
AWS Lambda: Connect to the AWS S3 bucket and transfer the file named inventory.csv from the S3 bucket to the Snowflake data warehouse.
5. Part Two: Data Transformation
The next stage of the project focuses on data transformation within the Snowflake data warehouse. This involves reshaping tables from their original structure to the desired format. Throughout this phase, tasks include:

Creating a data model
Developing ETL scripts
Establishing a schedule for the data loading process
6. Part Three: Data Analysis
In the last part of this project, establish a connection between the Snowflake data warehouse and the BI tool (Metabase). This connection allows for the creation and display of dashboards and reports in Metabase, utilizing the data stored in Snowflake.

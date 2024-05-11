# DataEndineering
Data Engineering projects


Data Engineering Project: ELT Pipeline
Overview:
This project focuses on building an Extract, Load, Transform (ELT) pipeline consisting of three fundamental steps: data ingestion, data transformation, and data visualization.

Data Overview
The data for this project is categorized based on its storage location into two types:

Data stored in Amazon RDS.
Data stored in an S3 bucket.
Steps Involved:
Data Ingestion:

Utilize Airflow for data stored in Amazon RDS.
Use AWS Lambda function for data stored in S3 bucket.
Aggregate all data into a Snowflake data warehouse.
Data Transformation:

Perform transformation according to client requirements on the Snowflake data warehouse.
Data Visualization:

Connect Snowflake with a metadata application for data insights and visualization.

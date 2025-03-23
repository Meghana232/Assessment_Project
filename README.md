# Assessment_Project
This project describes a data pipeline using AWS s3,Glue and Redshift to ingest,validate and transform the data.
Pipline consists of following steps:
1. ** Data Ingestion **: Uploaded data into AWS Glue
2. ** Data Validation **: Validations have been performed using python script
3. ** Staging ** : Normalized and stored data in staging tables in glue using SQL.
4. ** Transformations **: Created a new SQL table named mview_weekly_sales which consists of following columns totals of sales_units,sales_dollars, and discount_dollars grouped by pos_site_id, sku_id, fsclwk_id,price_substate_id and type.
  ## setup Instructions
  ### prerequisites:
  aws account with AWS GLue,S3,Redshift Configured
  python pyathena and pandas package

## configure AWS CLI
configure AWS CLI by executing the following command
AWS Configure

## data ingestion
assuming the extracted files are stored locally and now copying those files to s3 bucket by executing the following command
aws s3 cp C:\Users\maggi\Downloads\data s3://data-pipeline-bucket/raw-data/ --recursive
## Setting up AWS Glue Catalog and external Table
1. create database in AWS Glue
2. create a crawler
3. run the crawler
## verify and query data in amazon redshift
create external schema raw_data_schema 
from data_catalog
database 'raw_data_db' #database name that you've given while creating it in AWS Glue
IAM_ROLE 'arn:aws:iam::your-account-id:role/YourGlueRole'
REGION 'us-east-1';

SELECT * FROM RAW_DATA_SCHEMA.TRANSACTIONS LIMIT 10;
## Run Script
Till now we have ingested the data now we need to validate the data to perform validation we need to execute the script 
data_validation.py

We can execute those sql files in amazon redshift query editor

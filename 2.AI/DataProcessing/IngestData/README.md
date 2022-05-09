# Ingest data
## [Spark](Spark/README.md)
## 1. Direct Connect
## 2. Storage Gateway	
<img src="images/1.png">

## 3. Snowball
<img src="images/2.png">

## 4. Snowmobile
<img src="images/3.png">

## 5. SDK and CLI
- Software Driven architecture
- SDK and CLI can integrate with other tools as well

## [6. Data Migration Service (DMS)](https://aws.amazon.com/blogs/big-data/loading-ongoing-data-lake-changes-with-aws-dms-and-aws-glue/)
- Migrate Onpremise Databases to AWS
- Enable Continuous Replication via CDC 
  - Change Data Capture: Create a task that captures ongoing changes after you complete your initial (full-load) migration to a supported target data store
- User must create an EC2 to perform replication tasks
- SCT: Schema Conversion Tool
  - OLTP - SQL Server or Oracle To MySQL, PostgrSQL or Aurora
  - OLAP - Teradata or Oracle To Redshift
- DMS also as Migration tool for migrating One AWS DB to another AWS DB (ex: AWS MySQL to AWS Aurora)

## 7. AWS Data Pipeline
- AWS Data Pipeline is a web service that helps you reliably process and move data between 
  - Different AWS compute and storage services, as well as 
  - On-Premises data sources, **at specified intervals.**
- With AWS Data Pipeline, you can regularly 
  - Access your data where it’s stored, 
  - Transform and process it at scale, and 
  - Efficiently transfer the results to AWS services such as Amazon S3, Amazon RDS, Amazon DynamoDB, and Amazon EMR.
- Data Pipeline does not support external MySQL databases. 
  - It only supports the JDBC database, Amazon RDS, and Amazon Redshift.
- AWS Data Pipeline is more suitable for running scheduled tasks.										
- If you need to replicate a database and also want to **load on-going changes**, use AWS DMS										
### Data Pipeline: Task Runner Package for On Premise										
- To enable running activities using on-premise resources, AWS Data Pipeline supplies a Task Runner package that can be installed on your on-premise hosts. 
- This package continuously polls the AWS Data Pipeline service for work to perform. 
- When it’s time to run a particular activity on your on-premise resources, for example, executing a DB stored procedure or a database dump, AWS Data Pipeline will issue the appropriate command to the Task Runner. 
- In order to ensure that your pipeline activities are highly available, you can optionally assign multiple Task Runners to poll for a given job. 
- This way, if one Task Runner becomes unavailable, the others will simply pick up its work.
## 8. Streaming Data
- is generated Continuously
- has smaller Payloads
- comes from thousands of sources
### Examples										
- Heart Rate and fitnes monitoring
- In Game player activity
- Social Networking activity
### Kinesis
- Ingests, Buffers and Processes streaming data in real time
#### Real Time Processing of Streaming data										
- Goal is to respond as data arrives
  - Mobile GPS App suggests alternate routes based on traffic jams (It ingests live feed and notices traffic jams)
  - Real Time usage alerts to customer whne usage crosses specified Threshold
<img src="images/4.png">

#### Batch Processing of Data/Streaming data										
- Data/Streaming data can be stored in databases or in S3, this data is then analysed by hourly, daily or weekly scheduled jobs
- The batch processing is useful to NOTIFY CUSTOMERS periodically for changes to their accounts
  - Utility Bill Generation
  - Daily/Monthly reports
<img src="images/5.png">

- Sending data via KCL to EMR for Batch Processing
<img src="images/6.png">

<img src="images/7.png">

<img src="images/8.png">

<img src="images/9.png">

<img src="images/10.png">

<img src="images/11.png">

<img src="images/12.png">

<img src="images/13.png">

<img src="images/14.png">

<img src="images/15.png">

<img src="images/16.png">

<img src="images/17.png">

<img src="images/18.png">

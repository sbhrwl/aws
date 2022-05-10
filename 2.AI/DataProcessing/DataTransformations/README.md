# Data transformations
## Datalake and S3
- With a data lake built on Amazon S3, you can use native AWS services to run 
  - Big data analytics, 
  - Machine learning (ML), 
  - Artificial intelligence (AI), 
  - High-performance computing (HPC), and 
  - Media data processing applications to gain insights from your unstructured data sets.
<img src="images/1.png">

- Amazon S3 is designed for 99.999999999% (11 9s) of data durability. 
- With that level of durability, you can expect that if you store 10,000,000 objects in Amazon S3, you should only expect to lose a single object every 10,000 years! 
- The service automatically creates and stores copies of all uploaded S3 objects across multiple systems. 
- This means your data is available when needed and protected against failures, errors, and threats.
### Data Transformations	
- Collect data in Native format in datalake (S3)
- Transform data in data lake for analytics and downstream use cases
## AWS Glue
- Managed Spark Environment
- Glue ETL provides an easy option to automatically generate ETL scripts and run the script as a scheduled job.
- Glue ETL provisions required Spark infrastructure to run the job and automatically terminates the environment after the job is completed.
- Glue ETL is best suited for batch ETL use cases and it’s not meant to process streaming data, except Glue ETL job
<img src="images/2.png">

- AWS Glue ML Transforms job can perform Transformation tasks (ex: deduplication) in a serverless fashion
- Library and Framework support with Glue
  - **Python Shell** supports Glue jobs relying on libraries such as numpy, pandas and sklearn. 
  - **PySpark** supports Glue jobs written primarily using Python API of Apache Spark.
- Data Store support
  - Glue crawler connects to data stores
    - S3
    - RDS
    - Redshift
    - DynamoDB
    - DocumentDB
    - JDBC supported sources
- Limitations with Glue
  - Glue doesnot support input type as **Timestream**
  - Glue cannot write the output in **RecordIO-Protobuf** format										
### How Glue collects metadata
- Glue Crawlers run using "Built-in" classifiers as well as "Custom" classifiers
- Glue crawler connects to data stores
  - S3
  - RDS
  - Redshift
  - DynamoDB
  - DocumentDB
  - JDBC supported sources
- Glue crawler collects "Meta data" information
- This "Meta data" information is an ETL script.
- The ETL script can be generated in scala or python and it runs on Apache Spark
- This "Meta data" information is writting to Data Catalog
- Now we can query underlying data of Data Catalog via Athena
<img src="images/3.png">

- **The Glue generated ETL script can be used to load data on AWS EMR managed HIVE or SPARK table**

## EMR
- Amazon EMR: Big data distributed processing			
- Managed Hadoop Environment
- Amazon EMR is a managed cluster platform that simplifies running big data frameworks, such as Apache Hadoop and Apache Spark, on AWS to
  - Process and 
  - Analyze vast amounts of data. 
- By using these frameworks and related open-source projects, such as Apache Hive and Apache Pig, you can process data for analytics purposes and business intelligence workloads.
- Log Analysis is the most common use case of EMR
- Additionally, you can use Amazon EMR to transform and move large amounts of data into and out of other AWS data stores and databases.										
<img src="images/4.png">

### EMR Cluster
<img src="images/5.png">

### EMR Applications										
- Amazon EMR can help you instantly provision as much or as little capacity as you like to perform Data-Intensive tasks for applications such as 
  - Data mining, 
  - Web indexing, 
  - Log file analysis, 
  - Machine learning,
  - Financial analysis,
  - Scientific simulation, and 
  - Bioinformatics research. 
- Amazon EMR lets you focus on crunching or analyzing your data without having to worry about Tuning of clusters running open-source big data applications or the compute capacity upon which they sit.
- Amazon EMR requires managing underlying infrastructure, with Kinsesis we do not need to manage underlying infrastructure

### Use cases
- Glue not an option for Big data
  - Glue won't allow you to utilize different big data frameworks effectively, unlike Amazon EMR										
										
- HPC Vs Big data and Distributed processing										
  - HPC is FsX for Lustre, Big Data and Distributed processing is EMR										
										
- EMR with RedShift: Deadly Combination										
<img src="images/6.png">

- File Conversions to Parquet with EMR
  - Load S3 data (In Datalake) TO EMR Hive table and write them back in Parquet format										
  - Load S3 data (In Datalake) TO EMR Spark table and write them back in Parquet format
<img src="images/7.png">

- File Conversions to RecordIO-Protobuf format with EMR										
  - Glue cannot write the output in RecordIO-Protobuf format.
  - Lambda is not suited for long-running processes such as the task of transforming 1TB data into RecordIO-Protobuf format. 
  - Kinesis Firehose is not meant to be used for batch processing use cases and it cannot write data in RecorIO-Protobuf format. 
  - Apache Spark (running on the EMR cluster in this use-case) can write the output in RecorIO-Protobuf format.
  - The Glue generated ETL script can be used to load data on AWS EMR managed HIVE or SPARK table										

# Projects
- [Design principals](https://github.com/sbhrwl/aws/blob/main/1.Basics/2.UseCases/1.DesignPrincipals/README.md)
- [Security Principals](https://github.com/sbhrwl/system_design/blob/main/docs/Security/README.md)
- [Typical AWS Network Architecture](TypicalAWSarchitecture/README.md)
- [Micro services architecture](MicroServicesArchitecture/README.md)
- [Web applications](#web-applications)
  - [Caching strategies](#caching-strategies)
  - [Serverless architectures](#serverless-architectures)
- [High Availability architectural designs](#high-availability-architectural-designs)
- [Moving data to cloud](#moving-data-to-cloud)
- [Event driven architectures and Data analytics](#event-driven-architectures-and-data-analytics)
- [Other use cases](#other-use-cases)
  - [HPC](#hpc)

## Web applications
- [3 Tier Web app](3TierWebApp/README.md)
  - APP tiers, Security Design, Privileges, Logging, Monitoring
- [Stateless, Scalable and High Available Web app- What time is it?](StatelessWebApp/README.md)
  - Route 53 (TTL, A and Alias records)
  - Multi AZ to survive disasters
  - ELB Health Checks and Security Group Rules
- [Statefull Web app- MyClothes.com](StatefulWebApp/README.md)
  - Following 3 Tier architecture with Session affinity, Cookies, replaced finally with Server session in Elastic cache, 
  - Scalable and High Available RDS
- [Web app showing Images for the Users- MyWordPress.com](StatefulWebAppPictures/README.md)
  - Aurora Mysql in Multi AZ, EBS in in each AZ, replaced finally with EFS
  - Storing data in EBS (single instance application) Vs Storing data in EFS (distributed application)

### [Caching strategies](CachingStrategies/README.md)
- [Introduce Stickiness (Session Affinity)](StatefulWebApp/README.md)
- [Introduce User Cookies](StatefulWebApp/README.md)
- [Introduce Server Session using Elastic cache (overcomes challenges with cookies)](StatefulWebApp/README.md)
- [Caching at the API Gateway](MyTodoList/README.md#caching-at-the-api-gateway)
- [DAX caching layer](MyTodoList/README.md#caching-at-the-api-gateway)

### Serverless architectures
- [Mobile application- MyTodoList](MyTodoList/README.md)
  - Serverless REST API: HTTPS, API Gateway, Lambda, DynamoDB
  - Security for authentication and authorization with Cognito, STS
- [Distributing paid content](DistributingPaidContent/README.md)
- [Serverless hosted website- MyBlog.com](MyBlog/README.md)
  - Static content being distributed using CloudFront with S3
  - Global DynamoDB table to serve the data globally, DynamoDB streams to trigger a Lambda function
  - S3 can trigger SQS / SNS / Lambda to notify of events
- [Invoke lambda from API](InvokeLambdaFromAPI/README.md)
  - Lambda code, API gateway setup
- [API-Kinesis-S3](https://drive.google.com/drive/u/0/folders/109yWGA_es3a9MekffBQ6s3x81o1QycPX)
## High Availability architectural designs
- [Creating a highly available EC2 instance with ASG + EBS](HighAvailablity/README.md)
- [High Availability for a Bastion Hosts](HighAvailablity/README.md)
- [Instantiating Apps Quickly](InstantiatingAppsQuickly/README.md)
## Moving data to cloud
- [Transferring Data On premise to AWS](https://github.com/sbhrwl/aws/blob/main/1.Basics/2.UseCases/4.MovingDataToCloud/Snow/README.md)
  - Snowball, Snowball Edge, Snow Mobile, Snowball To Glacier
- [Replication of Data On premise to AWS](https://github.com/sbhrwl/aws/blob/main/1.Basics/2.UseCases/4.MovingDataToCloud/Replication/README.md)
  - Transferring Large Data [Site To Site VPN, Direct Connect, Snowball, Secured On going Replications]
  - Replication with DataSync, Data Migration Service (DMS)
- [DataSync](https://github.com/sbhrwl/aws/blob/main/1.Basics/2.UseCases/4.MovingDataToCloud/DataSync/README.md)
- [Data pipeline](https://github.com/sbhrwl/aws/blob/main/2.AI/DataProcessing/IngestData/README.md)
  - [Data Pipeline with Amazon RDS](https://github.com/sbhrwl/aws/blob/main/2.AI/DataProcessing/IngestData/README.md#data-pipeline-with-amazon-rds)  
  - [Data Pipeline with Amazon DynamoDB](https://github.com/sbhrwl/aws/blob/main/2.AI/DataProcessing/IngestData/README.md#data-pipeline-with-amazon-dynamodb)
## Event driven architectures and Data analytics
### Bigdata analytics
- [Basics](https://github.com/sbhrwl/system_design/blob/main/projects/BigdataAnalytics/README.md)
- [AWS services for event driven architectures](https://github.com/sbhrwl/aws/blob/main/1.Basics/3.Projects/EventDrivenArchitectures/README.md)
- [Big Data Ingestion Pipeline](BigDataIngestionPipeline/README.md)
- [BigQuery data warehouse architecture](https://github.com/sbhrwl/gcp/blob/master/data_analytics%2FREADME.md)
- [Workflow with dataflow](https://github.com/sbhrwl/gcp/blob/master/dataflow%2FREADME.md)
### AI on streaming data
- [Metering AI applications](https://github.com/sbhrwl/system_design/blob/main/projects/MeteringAIApplications/README.md)
- [Machine learning with BigQuery using SQL - BQML](https://github.com/sbhrwl/gcp/blob/master/docs/big_query/README.md#machine-learning-with-bigquery)
- [IoT Data Processing and Analytics](https://github.com/sbhrwl/system_design/blob/main/projects/IoTDataProcessingAnalytics/README.md)
- [DDos Attack Catcher](https://github.com/sbhrwl/system_design/blob/main/projects/DDosAttackCatcher/README.md)
- [Product Recommendation](https://github.com/sbhrwl/system_design/blob/main/projects/ProductRecommendation/README.md)
- [AI-Air Conditioner](https://github.com/sbhrwl/system_design/blob/main/projects/AI-AirConditioner/AI-AirConditioner.md)
- [Instagram Reels](https://github.com/sbhrwl/system_design/blob/main/projects/Instagram_Reels/README.md)
- [Serverless your Machine Learning Model](https://medium.com/analytics-vidhya/serverless-your-machine-learning-model-with-pycaret-and-aws-lambda-c33334ee6011)
- [Cloud-based Microservices Architecture at Netflix](https://medium.com/swlh/a-design-analysis-of-cloud-based-microservices-architecture-at-netflix-98836b2da45f)
- [Tech companies architecture](https://www.linkedin.com/posts/rajendrauppal_softwarearchitecture-softwaredesign-softwareengineers-activity-6984804253202571264-41Ln?utm_source=share&utm_medium=member_android)
## [Use cases](https://github.com/sbhrwl/system_design/blob/main/docs/DataProcessing/4.BigData/README.md#use-cases)
- **Big Data Analytics**: Processing and analyzing massive datasets stored in S3, GCS, or ADLS.
- **ETL Workflows**: Extract, transform, and load data in preparation for analytics or machine learning.
- **Real-Time Data Processing**: Handle real-time data ingestion and processing for event-driven architectures.
- **Machine Learning and AI**: Machine learning on massive datasets, integrated with cloud-based AI services.
- [Refer architecture 1](https://github.com/sbhrwl/gcp/blob/master/dataflow/README.md)
- [Refer architecture 2](https://github.com/sbhrwl/gcp/blob/master/datalake/README.md)

### Metering data analytics
- [Enrich IoT data](https://github.com/sbhrwl/system_design/blob/main/projects/ReadEventQueue/README.md)
- [TechStack](https://github.com/sbhrwl/system_design/blob/main/projects/TechStack/README.md)
- [Generate Attacks](subscribeToActiveMQ/README.md)
- [Metering infra on cloud](MeteringInfraOnCloud/README.md)
- [Choosing the Right Database](ChoosingTheRightDatabase/README.md)
- [Tech companies architecture](https://www.linkedin.com/posts/rajendrauppal_softwarearchitecture-softwaredesign-softwareengineers-activity-6984804253202571264-41Ln?utm_source=share&utm_medium=member_android)
## Other use cases
- [Offloading software updates](SoftwareUpdatesOffloading/README.md)
- [Blocking an IP address](BlockingIP/README.md)
- [Secure file upload](https://drive.google.com/drive/u/0/folders/109yWGA_es3a9MekffBQ6s3x81o1QycPX)
### HPC
- The cloud is the perfect place to perform HPC (High performance computing)
- You can create a very high number of resources in no time
- You can speed up time to results by adding more resources
- You can pay only for the systems you have used
- Perform genomics, computational chemistry, financial risk modeling, weather prediction, machine learning, deep learning, autonomous driving
- Which services help perform HPC?
  - Elastic Fabric Adapter (EFA)
    - Improved ENA for HPC, only works for Linux
    - Great for inter-node communications, tightly coupled workloads
    - Leverages Message Passing Interface (MPI) standard
    - Bypasses the underlying Linux OS to provide low-latency, reliable transport

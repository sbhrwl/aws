# Projects
- [Micro services architecture](#micro-services-architecture)
- [Web applications](#web-applications)
  - [Caching strategies](#caching-strategies)
  - [Serverless architectures](#serverless-architectures)
- [High Availability architectural designs](#high-availability-architectural-designs)
- [Event driven architectures and Data analytics](#event-driven-architectures-and-data-analytics)
- [Moving data to cloud](#moving-data-to-cloud)
- [Other use cases](#other-use-cases)
  - [HPC](#hpc)
## [Micro services architecture](MicroServicesArchitecture/README.md)
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
## High Availability architectural designs
- [Creating a highly available EC2 instance with ASG + EBS](HighAvailablity/README.md)
- [High Availability for a Bastion Hosts](HighAvailablity/README.md)
- [Instantiating Apps Quickly](InstantiatingAppsQuickly/README.md)

## Event driven architectures and Data analytics
- [Basics of event driven architectures](EventDrivenArchitectures/README.md)
- [Big Data Ingestion Pipeline](BigDataIngestionPipeline/README.md)
- [Metering infra on cloud](MeteringInfraOnCloud/README.md)
- [Choosing the Right Database](ChoosingTheRightDatabase/README.md)
- [Tech companies architecture](https://www.linkedin.com/posts/rajendrauppal_softwarearchitecture-softwaredesign-softwareengineers-activity-6984804253202571264-41Ln?utm_source=share&utm_medium=member_android)

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

## Other use cases
- [Offloading software updates](SoftwareUpdatesOffloading/README.md)
- [Blocking an IP address](BlockingIP/README.md)
- [Secure file upload](https://drive.google.com/drive/u/0/folders/109yWGA_es3a9MekffBQ6s3x81o1QycPX)
### HPC
- The cloud is the perfect place to perform HPC
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

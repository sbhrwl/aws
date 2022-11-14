# Projects
- [Web applications](#web-applications)
  - [Caching strategies](#caching-strategies)
  - [Serverless architectures](#serverless-architectures)
- [High Availability architectural designs](#high-availability-architectural-designs)
- [Event driven architectures and Data analytics](#event-driven-architectures-and-data-analytics)
- [HPC](#hpc)
- [Phases of a project](#phases-of-a-project)
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

### Fix
- [Micro Services architecture](MicroServicesArchitecture/README.md)
- [Distributing paid content](DistributingPaidContent/README.md)
- [Offloading software updates](SoftwareUpdatesOffloading/README.md)
- [Big Data Ingestion Pipeline](BigDataIngestionPipeline/README.md)
- [Event driven architectures](EventDrivenArchitectures/README.md)
- [Caching Strategies](CachingStrategies/README.md)
- [Blocking an IP address](BlockingIP/README.md)
- [Metering infra on cloud](MeteringInfraOnCloud/README.md)
- [Secure file upload](https://drive.google.com/drive/u/0/folders/109yWGA_es3a9MekffBQ6s3x81o1QycPX)
- [Choosing the Right Database](ChoosingTheRightDatabase/README.md)
- [Tech companies architecture](https://www.linkedin.com/posts/rajendrauppal_softwarearchitecture-softwaredesign-softwareengineers-activity-6984804253202571264-41Ln?utm_source=share&utm_medium=member_android)

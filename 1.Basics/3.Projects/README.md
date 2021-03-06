# Projects
- [Stateless Web App- What time is it?](StatelessWebApp/README.md)
- [Stateful Web App- MyClothes.com](StatefulWebApp/README.md)
- [Stateful Web App- MyWordPress.com](StatefulWebAppPictures/README.md)
- [Metering infra on cloud](MeteringInfraOnCloud/README.md)
- [Invoke lambda from API](InvokeLambdaFromAPI/README.md)
  - Lambda code, API gateway setup
- [Secure file upload](https://drive.google.com/drive/u/0/folders/109yWGA_es3a9MekffBQ6s3x81o1QycPX)
- Serverless Architectures
  - [Mobile application- MyTodoList](MyTodoList/README.md)
  - [Serverless hosted website- MyBlog.com](MyBlog/README.md)
  - [Serverless your Machine Learning Model](https://medium.com/analytics-vidhya/serverless-your-machine-learning-model-with-pycaret-and-aws-lambda-c33334ee6011)
  - [API-Kinesis-S3](https://drive.google.com/drive/u/0/folders/109yWGA_es3a9MekffBQ6s3x81o1QycPX)
- [Micro Services architecture](MicroServicesArchitecture/README.md)
- [Distributing paid content](DistributingPaidContent/README.md)
- [Offloading software updates](SoftwareUpdatesOffloading/README.md)
- [Big Data Ingestion Pipeline](BigDataIngestionPipeline/README.md)
- [Choosing the Right Database](ChoosingTheRightDatabase/README.md)
## 3Tier-Architecture
<img src="3Tier-Architecture.png">

- [3 Tier web application](3TierWebApp/README.md)
  - APP tiers, Security Design, Privileges, Logging, Monitoring
- [2 Tier web application](2TierWebApp/README.md)

## Instantiating Apps Quickly
<img src="InstantiatingAppsQuickly.png">

- [Event driven architectures](EventDrivenArchitectures/README.md)
- [Caching Strategies](CachingStrategies/README.md)
- [Blocking an IP address](BlockingIP/README.md)
## Creating a highly available EC2 instance with ASG + EBS
<img src="HA-EC2.png">

## High Availability for a Bastion Host
- HA options for the bastion host
  - Run 2 across 2 AZ
  - Run 1 across 2 AZ with 1 ASG 1:1:1
- Routing to the bastion host
  - If 1 bastion host, use an elastic IP with ec2 user-data script to access it
  - If 2 bastion hosts, use an Network Load Balancer (layer 4) deployed in multiple AZ
  - If NLB, the bastion hosts can live in the private subnet directly
- Note: Can???t use ALB as the ALB is layer 7 (HTTP protocol)
<img src="HA-BastionHost.png">

## HPC
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

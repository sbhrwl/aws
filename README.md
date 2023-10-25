# AWS
- [Networking](#networking)
- [Hybrid cloud](#hybrid-cloud)
- [Moving data to cloud](#moving-data-to-cloud)
- [Compute](#compute)
- [Auto scaling and High availability](#auto-scaling-and-high-availability)
- [Distributing content](#distributing-content)
- [Decoupling applications](#decoupling-applications)
- [Security](#security)
- [Monitoring and Logging](#monitoring-and-logging)
- [DevOps](#devops)
- [Storage](#storage)
- [Databases](#databases)
- [Datalake](#datalake)
- [Big data](#big-data)
- [AI](#ai)
- [Services](#services)
- [Support](#support)
- [Design principals](#design-principals)
- [Serverless analytics](#serverless-analytics)
- [Projects](#projects)
- [Links](#links)
## Networking
- [Networking fundamentals](1.Basics/1.Fundamentals/1.Networking/README.md)
  - [Network protocols](https://github.com/sbhrwl/system_design/blob/main/docs/Security/4.CommunicationAndNetworkSecurity/NetworkProtocols.md)
- [Cloud fundamentals](1.Basics/1.Fundamentals/2.Cloud/README.md)
  - Deployment models (Public cloud, Private cloud)
  - Service models (Infrastructure As A Service, Platform As A Service, Software As A Service)
- [Global Infrastructure](1.Basics/1.Fundamentals/3.GlobalInfra/README.md)
  - Regions, Availability zones (Placement group), Edge locations (Cloudfront infra)
- [VPC](1.Basics/1.Fundamentals/5.VPC/README.md)
  - Subnet, Internet Gateway, Route Table, NAT, DNS Resolution, NACL, Adding Internet Gateway to Main Route table of VPC
  - VPC-Defaults, NAT Gateway Vs NAT Instance, DNS-DHCP options, DNS Hostnames
  - VPC- IPv4 and IPv6 adressing (Dual Stack mode), Attaching IPv6 CIDRs to a subnet, Ephemerel Ports
  - Connection Between VPCs (VPC Endpoint (Endpoint Policy (VPC endpoint Policy for S3)), VPC Private Link, VPC Classic Link, VPC Peering, AWS Resource Access Manager, Sharing VPC resources together with VPC Peering and RAM)
- [Security perspective - (Domain 4- Communication and Network Security )](https://github.com/sbhrwl/system_design/blob/main/docs/Security/README.md)
## Hybrid cloud
- [Hybrid Connections](1.Basics/1.Fundamentals/11.Hybrid/HybridConnections/README.md)
  - Client VPN, Site to Site VPN, VPN Cloud Hub
  - On premise to AWS[Direct Connect, Direct Connect Gateway, Transit Gateway, Transit Gateway + DX  Gateway]
- [Hybrid Storage](1.Basics/1.Fundamentals/11.Hybrid/HybridStorage/README.md)
- FsX for Windows, Integrate with Microsoft AD
- FsX for Lustre, Integration with S3, Hot Storage
- Storage Gateway (File Gatweway, Volume Gateway, Tape Gateway, Hardware Appliance)
## Moving data to cloud
- [Transferring Data On premise to AWS](1.Basics/2.UseCases/4.MovingDataToCloud/Snow/README.md)
  - Snowball, Snowball Edge, Snow Mobile, Snowball To Glacier
- [Replication of Data On premise to AWS](1.Basics/2.UseCases/4.MovingDataToCloud/Replication/README.md)
  - Transferring Large Data [Site To Site VPN, Direct Connect, Snowball, Secured On going Replications]
  - Replication with DataSync, Data Migration Service (DMS)
- [DataSync](1.Basics/2.UseCases/4.MovingDataToCloud/DataSync/README.md)
- [Data pipeline](https://github.com/sbhrwl/aws/blob/main/2.AI/DataProcessing/IngestData/README.md)
## Compute
- [EC2](1.Basics/1.Fundamentals/4.EC2/README.md)
  - Connect to EC2, Security Group, Instance lifecycle, Instance family, Instance launch types
  - Dedicated host Vs instance, Spot request, ENI Vs ENA Vs EFA, Placement Groups (Enhanced_networking, vCPU-based "ON DEMAND INSTANCE limit per Region")
- [EKS]()
- Serverless
  - [API Gateway](1.Basics/2.UseCases/7.Serverless/API-Gateway/README.md)
    - Endpoints [Edge Optimized (Default), Regional, Private], Throttling
    - API Gateway Security [IAM Permission, Lambda Authorizer, Cognito User Pool]
    - API Gateway with Lambda
    - Migrating On Premise Linux API server to AWS and making it HA
  - [Lambda](1.Basics/2.UseCases/7.Serverless/Lambda/README.md)
    - Limits [Execution Limits, Deployment Limits], Lambda Metrices that Cloudwatch can track
    - Lambda@Edge (Global lambda)
  - [DynamoDB](1.Basics/2.UseCases/7.Serverless/DynamoDB/README.md)
    - Provisioned Throughput, Capacity Planning, On Demand Capacity
    - DynamoDB Accelerator (DAX), DaX Cluster, DynamoDB Streams, Global Table
    - Aurora Globa DB Vs DynamoDB Global Table
## Auto scaling and High availability
- [ASG](1.Basics/1.Fundamentals/6.ASG/README.md)
  - Step Scaling Vs Simple scaling, HA setup, Launch Templates
  - EC2 Cloudwatch agent, ELB Health Check for ASG, ASG-SNS and Instance State Change Events
- [ELB](1.Basics/1.Fundamentals/7.ELB/README.md)
  - NLB, ALB, CLB, ELB Health checks
  - NLB-Routing, Encryption in Transit, NLB-BYOIP - Static IP
  - ONLY ALB supports path-based routing and host-based routing (Perfect Forward Secrecy), ALB- Authentication via CUP, ALB - Weighted Routing
  - How to make an Application running in multi AZ on EC2 instances backed by Aurora DB exposed via ALB resilient to sporadic increase in request rate
  - Distribute traffic between On premise servers and AWS Web servers deployed on EC2
  - Configure a **NAT gateway** for each AZ with an Elastic IP
- [Route53](1.Basics/1.Fundamentals/8.Route53/README.md)
  - TTL, Registrar, Routing Policies (Routing based on location)
  - Alias records, Failovers, Supported DNS Record Types, DNSSEC
## Distributing content
- [Cloudfront](1.Basics/2.UseCases/6.DistributingContent/Cloudfront.md)
  - Origins [S3 Bucket, Custome Origin (HTTP)], Geo Restriction (WAF offers Geo Match condition)
  - HTTPS Support, How long can an Object stay in the cache?, Origin Failover
  - Cloudfront Signed URL/Cloudfront Signed Cookies, Cloudfront Signed URL Vs S3 Pre Signed URL
  - Cloudfront Vs S3 Cross Region Replciation
- [Global accelerator](1.Basics/2.UseCases/6.DistributingContent/GlobalAccelerator.md)
  - AWS Global Accelerator vs CloudFront, Traffic traverses the AWS global network, Why GA, GA and NLB
## Decoupling applications
- [SQS](1.Basics/2.UseCases/5.DecouplingApplications/SQS/README.md)
- [SNS](1.Basics/2.UseCases/5.DecouplingApplications/SNS/README.md)
- [Kinesis](1.Basics/2.UseCases/5.DecouplingApplications/Kinesis/README.md)
- [SWF](1.Basics/2.UseCases/5.DecouplingApplications/SWF/README.md)
- [Step functions](1.Basics/2.UseCases/5.DecouplingApplications/StepFunction/README.md)
  - Serverless Orchestration
## Security
- [IAM](1.Basics/2.UseCases/2.Security/IAM.md)
  - Authentication and Authorization, Roles Vs Resource based policies, Permisssion Boundary, IAM Federation
  - Root Account, IAM Query API, IAM-ACM
- [Identity federation](1.Basics/2.UseCases/3.IdentityFederation/README.md)
  - STS Assume Role (AssumeRole with SAML, AssumeRole with WebIdentity, GetSession Token)
  - SAML 2.0 Federation (API access to AWS, Access the AWS Management Console)
  - SAML2 LDAP, SAML2 ADFS
  - [ADconnector](1.Basics/2.UseCases/3.IdentityFederation/ADconnector.md)
  - [Cognito](1.Basics/2.UseCases/3.IdentityFederation/Cognito.md)
    - Cognito User Pool, Cognito Sync->AppSync,Cognito Identity Pool/Federation
- [KMS](1.Basics/2.UseCases/2.Security/KMS.md)
  - Customer Master Key, Key Policies, You cannot store credentials in KMS
- [Security perspective - (Domain 3- Software engineering and Domain 5- Identity and Access Management)](https://github.com/sbhrwl/system_design/blob/main/docs/Security/README.md)
## Monitoring and Logging
- [Cloudwatch](1.Basics/2.UseCases/8.Monitoring/Cloudwatch.md)
- [Cloudtrail](1.Basics/2.UseCases/8.Monitoring/Cloudtrail.md)
  - Object Level Logging, Encryption and Cloudtrail,Cloudtrail in all Regions
- [S3 or Server access logs](1.Basics/2.UseCases/8.Monitoring/S3accessLogs.md)
  - S3 Access Logs Vs Cloudtrail [Logging Operations, Logging Events (Data events, Management events)]
- [ELB access logs](1.Basics/2.UseCases/8.Monitoring/ELBaccessLogs.md)
  - Capture information about HTTP requests, Analysing logs with EMR/Hadoop
- [VPC Flow logs](1.Basics/2.UseCases/8.Monitoring/VPCflowLogs.md)
- [AWS X-Ray]()
- [AWS Inspector]()
## DevOps
- [DR](1.Basics/2.UseCases/2.Security/DR.md)
- [Security perspective - (Domain 8- Software Development and Security)](https://github.com/sbhrwl/system_design/blob/main/docs/Security/README.md)
- [Security perspective - (Domain 7- Security Operations)](https://github.com/sbhrwl/system_design/blob/main/docs/Security/README.md)
### Storage
- [EBS](1.Basics/1.Fundamentals/9.Storage/EBS/README.md)
  - Volume Types, Snapshots, Data Lifecycle Manager, Encryption
  - RAID, Instance Store, EC2 Status Checks on EBS, EBS Optimized Instances
- [EFS](1.Basics/1.Fundamentals/9.Storage/EFS/README.md)
  - Lifecycle/Storage Tiers, Performance and Throughput mode, EFS configuration, Attach VPC, AZ, Subnets and Security groups
  - How to configure EFS  which will hold HOME directory for users?, EFS with EC2, EFS is Highly available, EBS is not
  - When OBJECT based storage is needed, opt for S3. S3 is best for High Performance OBJECT based storage needs
  - EFS offers File System Interface, S3 doesnot, POSIX permissions, EFS Big Data Workloads
- [S3](1.Basics/1.Fundamentals/9.Storage/S3/README.md)
  - Versioning, CORS, Consistency Model, S3 Vs EFS, What is the correct indication that an object was successfully stored when you put objects in Amazon S3?
  - S3 Encryption[SSE-S3, SSE-KMS, SSE-C, Client Side Encryption, Encryption In transit, Cloud HSM, KMS with CloudHSM, Envelope Encryption]
  - S3 Security[User Based IAM Policies, Resource based ACL, Bucket Policy, Other(User Security, Logging and Audit, VPC Endpoint Policy), ACLs]
  - EC2 to Read S3
  - S3 with Cloudfront (Verisoning)
- [S3Advance](1.Basics/1.Fundamentals/9.Storage/S3Advance/README.md)
  - MFA-DELETE, Server/S3 Access Logs, S3 Replication
  - S3 Pre Signed URLS, CRR, Object Lock/Vault lock, S3 Event notification
  - S3 Storage Classes[Standard, Glacier, Glacier Deep Archive], Life cycle Rules
  - S3 Retrievals[Expedited retrievals, Provisioned capacity]
  - S3 Performance[Baseline Performance, Upload(Multipart Upload, **S3 Transfer Acceleration**), Download, Options for Upload(Pre signed URLs, Multi part upload, S3TA, GA)]
  - S3 Transfer Acceleration Vs Global Accelerator
  - Byte Range Fetch, S3 Parallel Requests, S3 Parallel request and Byte Range Fetches to DOWNLOAD LARGE Object
  - S3-Select
### Databases
- [RDS](1.Basics/1.Fundamentals/10.Databases/RDS/README.md)
  - DB Subnet Group, RDS Backups (Automated Backups, DB snapshots), DR, RDS Encryption, RDS Security, RDS Enhanced Monitoring
  - Read Replicas, Read Replica and Encryption keys, create an encrypted cross-region Read Replica, HA Read Replica
    - When would Amazon RDS automatically perform a failover to the standby replica
    - Security Patching, Offloading Reads, Cost Effectivenes of Offloading Read Options
  - MultiAZ-DR-HA
  - RDS In Transit Encryption, Enhanced Monitoring, RDS Event subscription
- [Aurora](1.Basics/1.Fundamentals/10.Databases/Aurora/README.md)
  - Aurora Security, DR, Read Replicas, Read Scaling with Multi AZ deployment, MultiAZ Or ReadReplica
  - Aurora Cluster Endpoints (Writer Endpoint, Reader Endpoint, Custom Endpoint)
  - Failovers with Aurora, Aurora Serverless,	Enhanced Monitoring, Aurora Global DB, Inter Region DR, Aurora Globa DB Vs DynamoDB Global Table
- [Elasticcache](1.Basics/1.Fundamentals/10.Databases/Elasticcache/README.md)
  - DB Cache, Session store, Write Through, Security
  - Redis(Remote Dictionary Server), Memcached
## [Datalake](https://drive.google.com/drive/u/0/folders/1eVM5cPoc-SwNaWopF_Yw5hoRXpbYrPnn)
## [AI](2.AI/README.md)
## [Services](https://drive.google.com/drive/u/0/folders/1ePxjdA9MI5arPMNxWpaG8BslyZjZ6KIu)
## [Support](https://drive.google.com/drive/u/0/folders/1eOe4f4HRPdWUsEngpABwc800TvO-pH0T)
## [Design principals](1.Basics/2.UseCases/1.DesignPrincipals/README.md)
- Design Principals, Design Concepts, Security Principals, Shared Controls
## [Serverless analytics](https://drive.google.com/drive/u/0/folders/1lsuWQwYVsdEnm_73_yHJQOyJuuMkNYRv)
## [Projects](1.Basics/3.Projects/README.md)
## Links
  - [Console](https://aws.amazon.com/console/)
  - [AWS Architecture Center](https://aws.amazon.com/architecture/?cards-all.sort-by=item.additionalFields.sortDate&cards-all.sort-order=desc&awsf.content-type=*all&awsf.methodology=*all&awsf.tech-category=*all&awsf.industries=*all)
  - [AWS Solutions Library](https://aws.amazon.com/solutions/)
  - [Amazon SageMaker Documentation](https://docs.aws.amazon.com/sagemaker/index.html)
  - [AWS Samples-Github](https://github.com/aws-samples/)
  - [Quickstart-amazon-eks](https://github.com/aws-quickstart/quickstart-amazon-eks)
  - [AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc&wa-guidance-whitepapers.sort-by=item.additionalFields.sortDate&wa-guidance-whitepapers.sort-order=desc)

# Replication of Data On premise to AWS
## 1. Transferring Large Data			
- Site To Site VPN			
- Direct Connect			
- Snowball			
- Secured On going Replications:
  - Site to Site VPN
  - Direct Connect with Data Sync as welll as DMS			
## 2. Replication with DataSync			
- Create a Data Sync Agent On premise			
- Data Sync Agent will connect to AWS Data sync service exposed via a Service endpoint			
- Datasync agent supports NFS and SMB for traferring data from On premise server			
- Replicate Data to S3, EFS or FsX for Windows			
- DataSync utilises DX connection or over Internet			
- DataSync suports direct movement to S3 Glacier and Glacier Deep Archive			
## 3. Data Migration Service (DMS)			
- Migrate Data bases to AWS			
- Enable Continuous Replication via CDC			
- User must create an EC2 to perform replication tasks			
- SCT: Schema Conversion Tool
  - OLTP - SQL Server or Oracle To MySQL, PostgrSQL or Aurora
  - OLAP - Teradata or Oracle To Redshift			
- DMS is also used to migrate from AWS RDS (including Aurora) to Redshift. DMS will use S3 as an intermidiary storage before migrating data to Redshift			
## On-Premise strategy with AWS 
- Ability to download Amazon Linux 2 AMI as aVM (.iso format)
  - VMWare, KVM,VirtualBox (Oracle VM). Microsoft Hyper-V
- VM Import / Export
  - Migrate existing applications into EC2
  - Create a DR repository strategy for your on-premise VMs
  - Can export back the VMs from EC2 to on-premise
- AWS Application Discovery Service
  - Gather information about your on-premise servers to plan a migration
  - Server utilization and dependency mappings 
  - Track with AWS Migration Hub
- AWS Database Migration Service (DMS)
  - replicate On-premise => AWS, AWS => AWS, AWS => On-premise
  - Works with various database technologies (Oracle, MySQI_, DynamoDB, etc..)
- AWS Server Migration Service (SMS)
  - Incremental replication of on-premise live servers to AWS 

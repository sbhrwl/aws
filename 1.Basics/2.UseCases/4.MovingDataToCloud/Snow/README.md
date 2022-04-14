# Transferring Data On premise to AWS
## 1. Snowball		
- Physical data transfer (not over network)		
- PetaBytes of data IN or OUT of AWS		
- KMS 256 bit encryption		
- If it takes more than 1 week to transfer data over network use Snowball		
- Requires installing Snowball device on Customer servers		
- Data is uploaded to S3		
- Tracking is done via SNS, text messages and AWS console		
## 2. Snowball Edge		
- Adds Computation capability to the Snowball Device, Has inherent support for EC2 (sbe-1, sbe-c and sbe-g Instance types)		
  - Storage Optimized: 24vCPU		
  - Compute Optimized: 52vCPU and optional GPU		
- Supports Custom EC2 AMI as well		
- Supports custom LAMBDA functions as well		
- Preprocess Data while moving		
- DataMigration, Machine Learning, Image Collation and IoT capture		
## 3. Snow Mobile		
- Transfer EXA bytes of data (1k PB)		
- Each Snowmobile has 100PB of capacity, use multiple in parallel		
- Use SnowMobile if you have more than 10 PB		
## 4. Snowball To Glacier		
- Snowball To S3, S3 to Glacier via Lifecycle policy		

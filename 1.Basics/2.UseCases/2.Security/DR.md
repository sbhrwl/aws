# Disaster Recovery
1. Backup Restore
2. Pilot Light
3. Warm Standby
4. Multi Site		
   - Hot site
   - Multi region

## DR tips
- Backup
  - EBS Snapshots, RDS automated backups / Snapshots, etc... 
  - Regular pushes to S3 / S3 IA / Glacier, Lifecycle Policy, Cross Region Replication 
  - From On-Premise: Snowball or Storage Gateway
- High Availability
  -  Use RouteS3 to migrate DNS over from Region to Region
  -  RDS Multi-AZ, ElastiCache Multi-AZ, EFS, S3
  -  Site to Site VPN as a recovery from Direct Connect
- Replication
  - RDS Replication (Cross Region),AWS Aurora + Global Databases
  - Database replication from on-premise to RDS 
  - Storage Gateway
- Automation
  - CloudFormation / Elastic Beanstalk to re-create a whole new environment
  - Recover / Reboot EC2 instances with CloudWatch if alarms fail
  - AWS Lambda functions for customized automations 
- Chaos
  - Netflix has a "simian-army" randomly terminating EC2 

# Disaster Recovery
- [Strategies](#strategies)
- [Tips](#tips)
- [Metrics for disaster recovery plan](#metrics-for-disaster-recovery-plan)
## Strategies
- Backup Restore
  - Restore from a backup
- Pilot Light
  - replicate your data from one Region to another and provision a copy of your core workload infrastructure
  - Resources required to support data replication and backup, such as databases and object storage, are always on.
  - Other elements, such as application servers, are loaded with application code and configurations, but are "switched off" and are only used during testing or when **disaster recovery failover is invoked**.
- Multi Site		
  - You can run your workload simultaneously in multiple Regions as part of a multi-site **active/active** or hot standby **active/passive** strategy.
  - Multi-site active/active serves traffic from all regions to which it is deployed, whereas hot standby serves traffic only from a single region, and the other Region(s) are only used for disaster recovery
- Standby
  - **Warm standby**
    - The warm standby approach involves ensuring that there is a `scaled down`, but `fully functional`, copy of your production environment in another Region. 
    - This approach **extends the pilot light concept** and decreases the time to recovery because your workload is always-on in another Region
  - **Hot standby**
    - Have instance groups exist in multiple regions, and traffic is forwarded with a global load balancer.
    - You can also implement this for data storage services like multi-regional Cloud Storage buckets and database services like Spanner and Firestore.
  - **Cold standby**.
    - You should create snapshots of persistent disks, machine images and data backups and store them in a **multi-region** storage.
    - Snapshots are taken that could be used to recreate the system.
    - If the main region fails, you can spin up service in the backup region using the snapshot images and persistent disks.
    - You will have to route requests to the new region, and it's vital to document and test this recovery procedure regularly.

## Tips
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

## Metrics for disaster recovery plan
- Recovery point objective (`RPO`) and the Recovery time objective (`RTO`).
- The recovery point objective is the **amount of data that would be acceptable to lose** and
- The recovery time objective is **how long it can take to be back up and running**.
  - You should brainstorm scenarios that might cause data loss or service failures and build a table
  - This can be helpful to provide structure on the different scenarios and to prioritize them accordingly.
  - You should create a plan for how to recover based on the disaster scenarios that you define.
  - `For each scenario`, devise a strategy based on the `risk` and `recovery point` and `time` objectives.
  - This isn't something that you want to simply document and leave.
  - You should communicate the process for recovering from failures to all parties.
  - The procedure should be tested and validated regularly, at least once per year, and ideally, recovery becomes a part of daily operations which helps streamline the process.

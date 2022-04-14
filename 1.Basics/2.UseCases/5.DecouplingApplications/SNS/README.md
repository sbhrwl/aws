# SNS
## 1. Overview		
- Upto 1 Million subscription per topic		
- Subscribers can be:
  - SQS
  - HTTP/HTTPS
  - Lambda
  - Emails
  - SMS
  - Mobile notification		

## 2. Integration		
- Cloudwatch can send directly to SNS		
- ASG alarms
- S3 bucket events
- Cloudformation (ex: deployment failed)		

## 3. Publish Messages		
- TOPIC Publish:
use SDK		
- DIRECT Publish:
For Mobile APPS SDK
Works with Google GCM, Amazon ADM		

## 4. Security		
- Encryption:
- In flight: HTTPS
- At rest: KMS
  - CSE also supported		
- Access Controls: IAM policies to restrict access to SNS API		
- SQS Access Policies:
- Configure Cross Account access
- Allow another services (SNS, S3) to write to SQS		

## 5. SNS Fan Out
<img src=images/1.png width=500>

<img src=images/2.png width=500>

# KMS

## 1. Overview		
- Fully Manage Key policies
  - Create key policy
  - Rotate key policy
  - Enable and Disable key policy		
- Key Usage can be Audited in Cloudtrail		
- Pay for API call to KMS		
- KMS can only encrypt 4KB of data per call, If data>4KB, use ENVELOPE Encryption		

## 2. Customer Master Key		
- Symmetric Keys (AES 256 keys):
Most of the time we are using symmetric keys		
- Asymmetric Keys (RSA: Public encrypt and private decrypt)		
- What does CMK offers
  - AWS Managed User Key (Default)
  - User key CREATED in KMS
  - User key IMPORTED in KMS		
## 3. Key Policies		
- To give access to KMS
  - Make sure KEY policy allows the user
  - Make sure IAM policy allows API calls		
- Default Key Policy
  - Complete access to the ROOT user		
- Custom Key Policy
  - Define Users, Roles that can access the KMS key
  - Define who can ADMINISTER key
  - Useful for CROSS ACCOUNT ACCESS of your KMS key		
## 4. Use Case		
- Encrypting Snapshots (EBS or EBS backed RDS instance)		
- Copying Snapshots across Accounts		
## 1. Keys are different form credentials (don't confuse)											
- "Store the credentials in AWS Key Management Service and use environment variables in the function code pointing to KMS" is incorrect. 
- You cannot store credentials in KMS, it is used for creating and managing encryption keys											

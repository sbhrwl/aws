# IAM
- By using identity and access management, you define who has access to which resources and outline what can be done to those resources. 
## Authentication and Authorization
- **Authentication**
  - Authentication is the process of validating that users are who they claim to be. The most common method of authentication is using passwords as credentials. 
- **Authorization**
  - Authorization is the process of giving the user permission to access a specific resource or function. Giving someone permission to download a file and providing users with administrative access are some examples of authorization. 
- Sometimes in Authorization, the most important question is not what can users do, but what can they NOT do. 
- Identity and access management approaches
  - You can consider a number of different approaches when addressing identity and access management. 
  - Two of the most important to consider are 
    - **protecting AWS credentials** and 
    - **establishing fine-grained authorization**

## 1. Overview		
-  User: Physical person		
-  Groups: Contains Users		
-  Roles: Internal usage within AWS resources		
-  Policies: JSON document
Assigned to Users directly		
v. Follow Least Privilege principle		

## 2. MFA		
-  Extra level of security		

## 3. Conditions		
-  Restrict Client IP from which API calls are being made 		
-  Restrict the Region the API calls are made to		
-  Restrict based on TAGS		
-  Force MFA		

## 4. Roles Vs Resource based policies		
-  When you assume ROLE (user, application, service), you give up your original permissions and take permissions assigned to the ROLE		
-  When using Resource based policy, the principal does not have to give his permissions		
## 5. Permisssion Boundary			
-  Supported for Users and Roles (not groups)			
-  Sets maximum permissions an IAM entity can get		
## 6. Policy Evaluation			
-  If there is an EXPLICIT DENY, then action is prohibited			
## 7. IAM Federation			
-  Helps Big organisations to integrate their AD with IAM			
-  Enables to access AWS resources using company credentials			
-  Uses SAML standard (AD)			

## 8. Root Account											
-  Only Root account can CLOSE AWS account
-  Only Root account can ENABLE MFA DELETE for S3 bucket											
											
### Access Keys are needed to allow users for making API calls to AWS services: DO NOT get misled by the description	
- Access keys are a combination of an access key ID and a secret access key and you can assign two active access keys to a user at a time. 
- These can be used to make programmatic calls to AWS when using the API in program code or at a command prompt when using the AWS CLI or the AWS PowerShell tools.
<img src=images/4.png width=500>

## 9. IAM Query API
- IAM Query API allows Direct access to the IAM web services using HTTPS			
<img src=images/5.png width=500>

## 10. IAM-ACM
- Importing 3rd party certificates: use IAM and ACM
<img src=images/6.png width=500>
											
## 11. IAM Group is not an IAM IDENTITY, so IAM group can not be used as Principal in IAM Policy	
<img src=images/7.png width=500>

## 12. Using IAM to allow access to Home Directory on S3
- Create IAM policy to give BUCKET Level permisssions											
<img src=images/8.png width=500>

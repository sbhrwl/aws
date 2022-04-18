# IdentityFederation

## Where are Users?											
### In organisation					
i. LDAP					
ii. AD					
iii. Customer Identity broker					
### On the Web					
i. Facebook					
ii. Google					
iii. Cognito User Pool (CUP)					

## Identity Federation											
- Identity Federation is 
  - process of authenticating users via User Pool that you may or may not own (guest users) and then 
  - providing the needed permission to access a resource or perform an operation"											

## Identity Federation in AWS
- Federation lets users outside of AWS to **assume temporary role** for accessing AWS resources.
- These users assume identity provided access role.
- Federations can have many flavors:
  - SAML 2.0
  - Custom Identity Broker
  - Web Identity Federation with Amazon Cognito
  - Web Identity Federation without Amazon Cognito
  - Single Sign On
  - Non-SAML with AWS Microsoft AD
- Using federation, you don’t need to create IAM users (user management is outside of AWS)
- **IAM and Cognito can be used for Identity federation**

## STS: Assume Role									
### 1. Overview	
i. Allows temporary, limited access to AWS resources	
ii. Token is valid for 1 hour	
### 2. AssumeRole	
i. Within your account for enhance security	
ii. For Cross Account Access: assume role in target account to perform actions there	
### 3. AssumeRole with SAML	
i. Return credentials for user, who is logged in with SAML	
### 4. AssumeRole with WebIdentity	
i. Return credentials for users logged in with IdP (Facebook, Google)	
ii. Instead of using WebIdentity use Cognito	
### 5. GetSession Token	
i. GetSession token via MFA	
ii. For AWS user or Root account user	

### Using STS to Assume a Role
• Define an IAM Role within your account or cross-account
• Define which principals can access this IAM Role
• Use AWS STS (Security Token Service) to retrieve credentials and impersonate the IAM Role you have access to (AssumeRole API)
• Temporary credentials can be valid between 15 minutes to 1 hour
## Assume Role with SAML2
### 1. SAML2 LDAP					
i. To Integrate LDAP based Identity store with AWS					
ii. Provides access to AWS console and CLI					
iii. No need to create IAM users for the employees of the organisation					
### 2. SAML2 ADFS					
i. To Integrate AD based Identity store with AWS					
ii. Provides access to AWS console and CLI					
iii. No need to create IAM users for the employees of the organisation					

### 3. Other types of Identity Federation are via
i. Custome Identity Broker (any other Identity store except LDAP or AD, It must also make API call to AWS to generate Token)
ii. Web Identity Broker, use Cognito instead"											

i. IAM and Cognito can be used for Identity federation											
ii. Federation through SAML is OLD way of doing things, use Amazon SSO instead											
## SAML 2.0 Federation
• To integrate Active Directory / ADFS with AWS (or any SAML 2.0)
• Provides access to AWS Console or CLI (through temporary creds)
• No need to create an IAM user for each of your employees

## AWS Cognito
• Goal:
• Provide direct access to AWS Resources from
the Client Side (mobile, web app)
• Example:
• provide (temporary) access to write to S3
bucket using Facebook Login
• Problem:
• We don’t want to create IAM users for our app
users
• How:
• Log in to federated identity provider – or
remain anonymous
• Get temporary AWS credentials back from the
Federated Identity Pool
• These credentials come with a pre-defined IAM
policy stating their permissions

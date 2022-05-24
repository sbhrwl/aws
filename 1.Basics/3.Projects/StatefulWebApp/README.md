# Statefull web app
- Consider a web app behind a Multi AZ ELB exposed via Route53
<img src="images/1.png">
  
## Introduce Stickiness (Session Affinity)
<img src="images/2.png">

## Introduce User Cookies
<img src="images/3.png">

## Introduce Server Session
<img src="images/4.png">

## Storing User Data in a database
<img src="images/5.png">

## Scaling Reads
<img src="images/6.png">

### Scaling Reads (Alternative) – Write Through
<img src="images/7.png">

## Multi AZ to Survive disasters
<img src="images/8.png">

## Securing via Security Groups
<img src="images/9.png">

## Summary
- 3-tier architectures for web applications
- ELB sticky sessions
- Web clients for storing cookies and making our web app stateless
- ElastiCache
  - For storing sessions (alternative: DynamoDB)
  - For caching data from RDS
  - Multi AZ
- RDS
  - For storing user data
  - Read replicas for scaling reads
  - Multi AZ for disaster recovery
- Tight Security with security groups referencing each other

# API Gateway

## 1. Overview
- Proxies Request		
- Caches API repsonses, Enable Caching for a STAGE to improve performance and set TTL, default TTL is 300 seconds and can be increased upto 3600 seconds		
- Transform and validate Requests and Responses		
- Generate SDK and API specifications		
- Enables you to build RESTful APIs and WebSocket APIs that are optimized for serverless workloads		
- Offers Authentication and Authorization		
- You pay only for the API calls you receive and the amount of data transferred out		

## 2.Integration		
- Lambda + API gateway: No infrastructure to manage		
- HTTP Endpoints
  - Internal On Premise HTTP app
  - ALB
- AWS services Expose all AWS API via API Gateway

## 3. Endpoints		
- Edge Optimized (Default)		
  - Request are routed through Cloudfront Edge locations		
  - API gateway still lives in ONE REGION		
- Regional		
  - For Clients within same region		
  - Could manually combine with Cloudfront to offer control over caching and distribution of content		
- Private		
  - Can be accessed only from your VPC by creating INTERFACE endpoint		
  - Define Resource policy to provide access		
### 3.1. API Gateway expose HTTPS endpoints only 

## 4. Throttling		
- Offers Throttling Limits to control spikes in Traffic, ex: 1000 request/seconds 		
- We can also configure to handle burst, ex: 2000 request/second for few seconds		

### 4.1. Throttling: 429 Too Many Requests

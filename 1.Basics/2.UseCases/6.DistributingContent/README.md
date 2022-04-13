# Distributing content
## 1. Overview		
- Caches content at Edge (216 edge locations)		
- DDoS protection, integration with WAF		
- Exposes HTTPS endpoints and can talk to internal HTTP/HTTPS backends		

## 2. Origins		
- S3 Bucket		
  - Distributing files		
  - Enhance Security with Cloudfront OAI		
  - Cloudfront as INGRESS to upload files to S3		
- Custome Origin (HTTP)		
  - ALB (must allow Public IP of Edge locations)		
  - EC2 (must allow Public IP of Edge locations)		
  - S3 website		
  - Any HTTP endpoint 		
- You can't set Lambda@Edge functions as part of your origin group in CloudFront		
## 3. Geo Restriction		
- Whitelist		
Allow user to access content only if they are in approved list of countries		
- Blacklist		
Block user to access content only if there are in blacklist of banned countries		
## 4. HTTPS Support		
- Exposes HTTPS endpoints and can talk to internal HTTPS backends		
- We can associate certificate (generated using ACM etc) with our Web Distribution		
- Enable the SNI support as well when using HTTPS		
## 5. How to restrict users to circumvent Cloudfront
1. When distributing from S3  via Cloudfront
- Use OAI to restrict users to circumvent Cloudfront											
2. When distributing from ELB											
- Create a VPC security Group for the ELB to ALLOW traffic only from Cloudfront internal service IP											
- As Cloudfront Intenal SERVICE IP change also, so use Lambda to UPDATE security group for ELB											
## 6. How long can an Object stay in the cache?											
- You can control how long your objects stay in a CloudFront cache before CloudFront forwards another request to your origin. 
- Reducing the duration allows you to serve dynamic content. 
- Increasing the duration means your users get better performance because your objects are more likely to be served directly from the edge cache. 
- A longer duration also reduces the load on your origin
- The Cache-Control and Expires headers control how long objects stay in the cache. 
- The Cache-Control max-age directive lets you specify how long (in seconds) you want an object to remain in the cache before CloudFront gets the object again from the origin server.

- The minimum expiration time CloudFront supports is 0 seconds for web distributions and 3600 seconds for RTMP distributions
- Typically, CloudFront serves an object from an edge location until the cache duration that you specified passes — that is, until the object expires. 
- After it expires, the next time the edge location gets a user request for the object, CloudFront forwards the request to the origin server to verify that the cache contains the latest version of the object. 
<img src="images/1.png" width=500>

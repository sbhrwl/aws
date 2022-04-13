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
### 3.1 Geo Restriction WAF offers Geo Match condition
<img src="images/2.png" width=500>

#### AWS WAF
- AWS WAF is a web application firewall service that lets you monitor web requests and protect your web applications from malicious requests. 
- Use AWS WAF to block or allow requests based on conditions that you specify, such as the IP addresses. 
- You can also use AWS WAF preconfigured protections to block common attacks like SQL injection or cross-site scripting. 
- Configure AWS WAF on the Application Load Balancer in a VPC You can use AWS WAF with your Application Load Balancer to allow or block requests based on the rules in a web access control list (web ACL). 
- Geographic (Geo) Match Conditions in AWS WAF allows you to use AWS WAF to restrict application access based on the geographic location of your viewers. - With geo match conditions you can choose the countries from which AWS WAF should allow access. 
- Geo match conditions are important for many customers. 
- For example, legal and licensing requirements restrict some customers from delivering their applications outside certain countries. 
- These customers can configure a whitelist that allows only viewers in those countries. 
- Other customers need to prevent the downloading of their encrypted software by users in certain countries. 
- These customers can configure a blacklist so that end-users from those countries are blocked from downloading their software. 
- Incorrect options: 
  - Use Geo Restriction feature of Amazon CloudFront in a VPC 
  - Geo Restriction feature of CloudFront helps in restricting traffic based on the user's geographic location.
  - But, CloudFront works from edge locations and diS MP Mlle Hence, this option itself is incorrect
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

## 7. Origin Failover		
- Create an Origin Group with 2 Origins		
- Specify One Origin as PRIMARY and another Origin as Failover		
- When Primary Origin return HTTP FAILURE codes, Cloudfront Automatically switches to Second Origin		
## 8. Cloudfront Signed URL/Cloudfront Signed Cookies		
- Signed URL: One Signed URL per file		
- Signed Cookie: One Signed Cookie for Multiple files		
- AWS has Trusted Signers to generate Signed URL/Cookies		
- Use SDK or CLI to generate Signed URLs		
  - URL Expiration period
  - IP ranges to access data from
## 9. Field Level Encryption		
- Adds EXTRA Level of ENCRYPTION at Cloudfront EDGE Locations		
## 10. Customize Content		
- Customize the content that is delivered to End Users by using Lambda@Edge		
- Allows us to Execute Authentication Functions/Process in AWS locations CLOSE to the end users		

## 11. Cloudfront Signed URL Vs S3 Pre Signed URL
<img src="images/3.png" width=500>

## 12. Cloudfront Vs S3 Cross Region Replciation
### CloudFront
- Global Edge network
- Files are cached for a TTL (maybe a day) • Great for static content that must be available everywhere 
### S3 Cross Region Replication
- Must be setup for each region you want replication to happen
- Files are updated in near real-time • Read only
- Great for dynamic content that needs to be available at low-latency in few regions 

## 13. GlobalAccelerator
## 1. Overview		
- Creates 2 AnyCast IP for our Application, you can use IP address that was used to access EXISTING application		
- AnyCast IP send Traffic directly to Edge Location		
- Edge location send the traffic directly to the application		
## 2. Consistent Performance		
- Intelligent Routing to LOWEST Latency		
- Fast regional failover		
- Internal AWS network		
## 3. Health Checks		
- GA performs Health checks to our Application		
- Makes Application GLOBAL		
- FAILOVER < 1 minute		
## 4. Security		
- ONLY 2 IP to be Whitelisted		
- DDoS protection with AWS Shield		
## 5. Steps
- Launch an Instance in US
- Launch an Instance in India 
- Create GLobal accelerator
- Add "listener (Port 80-HTTP traffic) 
- Add Endpoint Group 
  - One endpoint group for US 
  - One endpoint group for India 
- 6. Add EC2 instance (or LB) to endpoint group 

## AWS Global Accelerator vs CloudFront 
- They both use the AWS global network and its edge locations around the world
- Both services integrate with AWS Shield for DDoS protection. 
### CloudFront
- Improves performance for both cacheable content (such as images and videos)
- Dynamic content (such as API acceleration and dynamic site delivery)
- Content is served at the edge 
### Global Accelerator
- Improves performance for a range of applications over TCP or UDP
- Proxying packets at the edge to applications running in one or more AWS Regions.
- Good fit for non-HTTP use cases, such as gaming (UDP), loT (MQTT), orVoice over IP
- Good for HTTP use cases that require static IP addresses
- Good for HTTP use cases that required deterministic. fast regional failover 
<img src="images/4.png" width=500>

###
- A web application is deployed in multiple regions behind an ELB Application Load Balancer. 
- You need deterministic routing to the closest region and automatic failover. 
- Traffic should traverse the AWS global network for consistent performance."											
### 
- CORRECT: "Configure AWS Global Accelerator and configure the ALBS as targets" is the correct answer. 
- INCORRECT: "Place an EC2 Proxy in front of the ALB and configure automatic (allover^ is incorrect. Placing an EC2 proxy in front of the ALB does not meet the requirements. This solution does not ensure deterministic routing the closest region and failover is happening within a region which does not protect against regional failure. Also, this introduces a potential bottleneck and lack of redundancy. 
- INCORRECT: "Create a ROUGESS:Alias record for each ALB and configure a latency-based routing policy" is incorrect. A Route 53 Alias record for each ALB with latency-based routing does provide routing based on latency and failover. However, the traffic istWoltrayerke 1WRIVSolobist network. 
- INCORRECT: "Use a Clendlfrandlitribution with multiple custom origins in each region and configure for high availability is incorrect. You can use  CloudFront with multiple custom origins and configure for HA. However, the traffic will not be traverse the **AWS global network**
## Why GA
- When the application usage grows, the number of IP addresses and endpoints that you need to manage also increase.											
- AWS Global Accelerator allows you to scale your network up or down											
- AWS Global Accelerator lets you associate regional resources, such as load balancers and EC2 instances, to two static IP addresses. 											
iv. You only whitelist these addresses once in your client applications, firewalls, and DNS records.											
											
### Use cases											
- With AWS Global Accelerator, you can 
  - add or remove endpoints in the AWS Regions, 
  - run blue/green deployment, and 
  - A/B test without needing to update the IP addresses in your client applications."											
- This is particularly useful for IoT, retail, media, automotive, and healthcare use cases in which client applications cannot be updated frequently.																
### How does GA helps to reduce number of IP addresses? Use Endpoint group											
- If you have multiple resources in multiple regions, you can use AWS Global Accelerator to reduce the number of IP addresses. 											
- By creating one endpoint group, you can add all of your EC2 instances in different regions in that group.											
- The created accelerator would have two static IP addresses that you can use to create a security rule in your firewall device.											
- Instead of regularly adding the Amazon EC2 IP addresses in your firewall, you can use the static IP addresses of AWS Global Accelerator to automate the process and eliminate this repetitive task.											
											
### GA and NLB											
- NLB is not suitable to route traffic to your ALBs across multiple Regions. 
- You have to use AWS Global Accelerator instead.

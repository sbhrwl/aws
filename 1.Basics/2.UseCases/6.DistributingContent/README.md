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


## AWS WAF
- AWS WAF is a web application firewall service that lets you monitor web requests and protect your web applications from malicious requests. Use AWS WAF to block or allow requests based on conditions that you specify, such as the IP addresses. You can also use AWS WAF preconfigured protections to block common attacks like SQL injection or cross-site scripting. Configure AWS WAF on the Application Load Balancer in a VPC You can use AWS WAF with your Application Load Balancer to allow or block requests based on the rules in a web access control list (web ACL). Geographic (Geo) Match Conditions in AWS WAF allows you to use AWS WAF to restrict application access based on the geographic location of your viewers. With geo match conditions you can choose the countries from which AWS WAF should allow access. Geo match conditions are important for many customers. For example, legal and licensing requirements restrict some customers from delivering their applications outside certain countries. These customers can configure a whitelist that allows only viewers in those countries. Other customers need to prevent the downloading of their encrypted software by users in certain countries. These customers can configure a blacklist so that end-users from those countries are blocked from downloading their software. Incorrect options: Use Geo Restriction feature of Amazon CloudFront in a VPC - Geo Restriction feature of CloudFront helps in restricting traffic based on the user's geographic location. But, CloudFront works from edge locations and diS MP Mlle Hence, this option itself is incorrect and • 

## CloudFront:
• Global Edge network • Files are cached for a TTL (maybe a day) • Great for static content that must be available everywhere 
• S3 Cross Region Replication: • Must be setup for each region you want replication to happen • Files are updated in near real-time • Read only • Great for dynamic content that needs to be available at low-latency in few regions 

## GlobalAccelerator:
- 1. Launch an Instance in US 2. Launch an Instance in India 3. Create GLobal accelerator r 4. Add "listener (Port 80-HTTP traffic) 5. Add Endpoint Group 5.1. One endpoint group for US 5.2. One endpoint group for India 6. Add EC2 instance (or LB) to endpoint group 

## AWS Global Accelerator vs CloudFront 
• They both use the AWS global network and its edge locations around the world • Both services integrate with AWS Shield for DDoS protection. 
• CloudFront • Improves performance for both cacheable content (such as images and videos) • Dynamic content (such as API acceleration and dynamic site delivery) • Content is served at the edge 
• Global Accelerator • Improves performance for a ‘A.cle range of applications over TCP or UDP • Proxying packets at the edge to applications running in one or more AWS Regions. • Good fit for non-HTTP use cases, such as gaming (UDP), loT (MQTT), orVoice over IP • Good for HTTP use cases that require static IP addresses • Good for HTTP use cases that required deterministic. fast regional failover 

### CORRECT: "Configure AWS Global Accelerator and configure the ALBS as targets" is the correct answer. 
INCORRECT: "Place an EC2 Proxy in front of the ALB and configure automatic (allover^ is incorrect. Placing an EC2 proxy in front of the ALB does not meet the requirements. This solution does not ensure deterministic routing the closest region and failover is happening within a region which does not protect against regional failure. Also, this introduces a potential bottleneck and lack of redundancy. 
INCORRECT: "Create a ROUGESS:Alias record for each ALB and configure a latency-based routing policy" is incorrect. A Route 53 Alias record for each ALB with latency-based routing does provide routing based on latency and failover. However, the traffic istWoltrayerke 1WRIVSolobist network. 
INCORRECT: "Use a Clendlfrandlitribution with multiple custom origins in each region and configure for high availability" is incorrect. You can use CloudFront 
with multiple custom origins and configure for HA. However, the traf f tO_MWoltraversethe-AWS global netvgffic 

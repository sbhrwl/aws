# What time is it

## Use case
- **Stateless web app**
- We want to start small and can accept downtime
- We want to fully scale vertically and horizontally, no downtime

### Starting simple
<img src="images/1.png">

### Scaling vertically
<img src="images/2.png">

### Scaling horizontally
<img src="images/3.png">

#### Adding and removing instances
<img src="images/4.png">

#### Scaling horizontally with a load balancer
<img src="images/5.png">

#### Scaling horizontally, with an auto-scaling group
<img src="images/6.png">

#### Making our app multi-AZ
<img src="images/7.png">

##### Reserving capacity
<img src="images/8.png">

## Summary
- Public vs Private IP and EC2 instances
- Elastic IP vs Route 53 vs Load Balancers
- Route 53 
  - TTL, 
  - `A` records and 
  - `Alias` Records
- Maintaining EC2 instances manually vs Auto Scaling Groups
- Multi AZ to survive disasters
- ELB Health Checks
  - Security Group Rules
- Reservation of capacity for costing savings when possible
- We’re considering 5 pillars for a well architected application:
  - costs, 
  - performance, 
  - reliability, 
  - security, 
  - operational excellence

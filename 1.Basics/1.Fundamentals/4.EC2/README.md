# EC2

## 1. Connect to EC2		
- Windows SSH		
- Linux		
- EC2 Instance Connect		
- Session Manager		
## 2. Security Group		
- All Inbound Blocked		
- All Outbound Authorized to all IP addresses		
## 3. IPs		
- Public IP		
- Private IP (retained when instance is stopped)		
- Elastic IP (5 per account)
- Elastic IP is assiciated with the Private IP on the instance
## 4. ENI		
- ENI is a Network Adaptor		
- ENI is attached to EC2 instance		
- Gives Public and Private IP to an EC2		
- Attaching ENI to Instance:
  - Hot Attach: When it is running
  - Warm Attach: When it is Stopped
  - Cold Attached: When Instance is being Launched	
## 5. User Data		
- Scripts entered as User data are executed as the root user, hence do not need the sudo command in the script.		
## 6. Default Addressing Protocol		
- By default, a new EC2 instance uses an IPv4 addressing protocol	
## 7. Instance Meta data		
- http://169.254.169.254/latest/meta-data/
- Instance Metadata Query tool		
## 8. FTP		
- The FTP protocol uses TCP via ports 20 and 21	
## 9. Instance Launch Types		
- OnDemand 
  - It has vCPU limit per region for an account
- Reserved		
  - Standard Reserved		
  - Convertible Reserved		
  - Scheduled Reserved		
- Dedicated Host		
- Dedicated Instance		
- Spot Instance		
## 10. Instance Family		
- M/T/R/X/D/H/I/G/P/F/C		
- T2/T3 burstable		
- T2/T3 unlimited Burst		
- An instance family has many instance Types		
## 11. AMI		
- Create Instance from AMI		
- Copy AMI to Different Account (Cross Account AMI copy)		
- Copy AMI to Different Region		
## 12. Placement Groups		
- Cluster		
- Spread (multiple AZ but within same REGION)
- Partition
## Instance lifecycle
<img src="images/Instance_Lifecycle.png">

## dedicated_host_vs_instance
<img src="images/dedicated_host_vs_instance.png">

## dedicated_host_vs_instance1
<img src="images/dedicated_host_vs_instance1.png">

## Enhanced_networking
<img src="images/Enhanced_networking.png">

## eni_ena_efa
<img src="images/eni_ena_efa.png">

## instance_families
<img src="images/instance_families.png">

## instance_families_q1
<img src="images/instance_families_q1.png">

## instance_families_q2
<img src="images/instance_families_q2.png">

## Instance_Lifecycle
<img src="images/Instance_Lifecycle.png">

## Instance_Lifecycle_states
<img src="images/Instance_Lifecycle_states.png">

## terminate_spot_instance
<img src="images/terminate_spot_instance.png">

## vCPU-1
<img src="images/vCPU-1.png">

## vCPU-2
<img src="images/vCPU-2.png">

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
## 4. Default Addressing Protocol		
- By default, a new EC2 instance uses an IPv4 addressing protocol	
## 5. FTP		
- The FTP protocol uses TCP via ports 20 and 21	
## 6. AMI		
- Create Instance from AMI		
- Copy AMI to Different Account (Cross Account AMI copy)		
- Copy AMI to Different Region	
## 7. User Data		
- Scripts entered as User data are executed as the root user, hence do not need the sudo command in the script.		
## 8. Instance Meta data		
- http://169.254.169.254/latest/meta-data/
- Instance Metadata Query tool		
## 9. Instance lifecycle
<img src="images/Instance_Lifecycle.png">

### Lifecycle states
<img src="images/Instance_Lifecycle_states.png">

- **EC2 Hibernate** You are charged for EC2 instance when instance is in STOPPING state preparing for Hibernate

## 10. Instance family		
- M/T/R/X/D/H/I/G/P/F/C
- M/T: General Purpose Instances
- C: Compute Optimized										
- R/X: Memory Optimized									
- D/H/I: Storage Optimized				
- G/P/F: Accelerated Computing Instances
- T2/T3 burstable/unlimited Burst		
- An instance family has many instance types
<img src="images/instance_families.png">
								
- Instance **Family support Encryption** but not all Instance TYPES in that family might support encryption
<img src="images/instance_families_q1.png">

- Choose the Instance which supports your **workload**
<img src="images/instance_families_q2.png">

## 11. Instance launch types		
- OnDemand 
  - It has vCPU limit per region for an account
- Reserved		
  - Standard Reserved		
  - Convertible Reserved		
  - Scheduled Reserved		
- Dedicated Host		
- Dedicated Instance		
- Spot Instance
## 12. Dedicated host Vs instance
- Dedicated Instances may share hardware with other instances from the **same AWS account** that are not Dedicated Instances.
- Dedicated Instances are obviously **more Cost effective** (per Instance billing) compared Dedicated Host (per Host billing)
<img src="images/dedicated_host_vs_instance.png">

- A host is a machine or VM that applications "run on" and **each HOST one can run N instances** of the application
<img src="images/dedicated_host_vs_instance1.png">

## 13. Spot request
- Request Types			
  - One time			
  - Persistent
- Request Criteria
  - Max Spot Price
  - Spot Block: Adhoc schedule needs
    - example: We need 15 EC2 instances for 5 hours per day, at the end of quarter for 5 days
    - This is not a good case for Scheduled Reserved instances
    - Scheduled reserved instances are ideal for workloads that run for a certain number of hours each day, but not for just 5 days per quarter.
- **Spot Fleet** = Spot Instance+OnDemand Instances
  - Spot Fleet Request	
    - Specify Launch pools					
      - OS					
      - AZ					
      - Instance type					
- Allocation Strategy					
  - Capacity Optimized					
  - Diversified					
  - Lowest Price					
- How to **CANCEL Spot Request** to **TERMINATE Spot Instance**
<img src="images/terminate_spot_instance.png">

## 14. ENI Vs ENA Vs EFA
- ENI
  - ENI is a Network Adaptor		
  - ENI is attached to EC2 instance		
  - Gives Public and Private IP to an EC2		
  - Attaching ENI to Instance:
    - Hot Attach: When it is running
    - Warm Attach: When it is Stopped
    - Cold Attached: When Instance is being Launched	
- ENA											
  - Amazon EC2 provides enhanced networking capabilities through the Elastic Network Adapter (ENA). 
  - It supports network speeds of up to 100 Gbps for supported instance types. 
  - Elastic Network Adapters (ENAs) provide traditional IP networking features that are required to support VPC networking
- EFA											
  - An Elastic Fabric Adapter (EFA) is simply an Elastic Network Adapter (ENA) with added capabilities. 
  - It provides all of the functionality of an ENA, with additional OS-bypass functionality."											
<img src="images/eni_ena_efa.png">

- What is **OS-bypass** functionality?
  - OS-bypass is an access model that allows HPC and machine learning applications to communicate directly with the network interface hardware to provide low-latency, reliable transport functionality.
- EFA is not for Windows Instances
  - The OS-bypass capabilities of EFAs are not supported on Windows instances. 
  - If you attach an EFA to a Windows instance, the instance functions as an Elastic Network Adapter, without the added EFA capabilities.
  - Elastic Network Adapters (ENAs) provide traditional IP networking features that are required to support VPC networking"											
## 15. Placement Groups		
- Cluster		
- Spread (multiple AZ but within same REGION)
- Partition

- Use Spread Placement group to Handle **Hardware Node failure**
  - An application that you will be deploying in your VPC requires 14 EC2 instances that must be placed on distinct underlying hardware to reduce the impact of the failure of a hardware node. The instances will use varying instance types. What configuration will cater to these requirements taking cost-effectiveness into account?
  - **Spread Placement Group**
    - A spread placement group is a group of instances that are each placed on distinct underlying hardware. 
    - Spread placement groups are recommended for applications that have a small number of critical instances that should be kept separate from each other. 
    - Launching instances in a spread placement group reduces the risk of simultaneous failures that might occur when instances share the same underlying hardware."											

- Add **needed number of instances** at the launch to avoid **insufficient capacity error**
  - The system running on Placement group was working fine for a couple of weeks, however, when they try to add new instances to the placement group that already has running EC2 instances, they receive an **insufficient capacity error**?
  - It is recommended that you launch the number of instances that you need in the placement group in a single launch request and that you use the same instance type for all instances in the placement group. 
  - If you try to add more instances to the placement group later, or if you try to launch more than one instance type in the placement group, you increase your chances of getting an insufficient capacity error.
  - If you receive a capacity error when launching an instance in a placement group that already has running instances, stop and start all of the instances in the placement group, and try the launch again. 
  - Restarting the instances may migrate them to hardware that has capacity for all the requested instances.

- **Enhanced networking**
  - Enhanced Networking offers HIGH PPS													
  - While Deploying a HPC on a cluster make sure that you 
    - Use Placement Groups and 
    - Choose EC2 instances with Enhanced networking
    - AWS currently supports Enhanced Networking capabilities using SR-IOV
    - SR-IOV provides DIRECT access to network adapters, higher PPS and lower latency"													
<img src="images/Enhanced_networking.png">

- **vCPU** based `ON DEMAND INSTANCE limit per Region`
<img src="images/vCPU-1.png">

<img src="images/vCPU-2.png">

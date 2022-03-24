# EC2

|1. Connect to EC2|			2. Security Group		|	3. IPs	|		4. ENI		|
|-----------------|-----------------|------|------|
|i. Windows SSH		|	i. All Inbound Blocked	|		i. Public IP		|	i. ENI is a Network Adaptor		
|ii. Linux		|	ii. All Outbound Authorized to all IP addresses		|	ii. Private IP (retained when instance is stopped)	|	ii. ENI is attached to EC2 instance|
|iii. EC2 Instance Connect||iii. Elastic IP (5 per account) - Elastic IP is associated with the **Private IP** on the instance|iii. Gives Public and Private IP to an EC2|
|iv. Session Manager|||iv. Attaching ENI to Instance:|
||||a. Hot Attach: When it is running|
||||b. Warm Attach: When it is Stopped|
||||c. Cold Attached: When Instance is being Launched|

## Instance lifecycle
<img src="images/Instance_Lifecycle.png">

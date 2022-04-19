# Cloudwatch
## 1. Metrics
## 2. Custom Metrics					
## 3. Dashboard
## 4. Logs
## 5. Events	
## 6. Alarms
### Cloudwatch Alarm											
- Alarm Evaluation Period
  - Number of MOST RECENT DATA POINTS to evaluate when determining Alarm state											
- Cooldown period
  - The cooldown period is a configurable setting for your Auto Scaling group that helps to ensure that it doesn't launch or terminate additional instances before the previous scaling activity takes effect so this would help. After the Auto Scaling group dynamically scales using a simple scaling policy, it waits for the cooldown period to complete before resuming scaling activities. 
  - After the autoscaling group dynamically scales using a simple scaling policy, it waits for the cooldown period to complete before resuming scaling activities
- The **CloudWatch Alarm valuation period** is the number of the most recent data points to evaluate when determinign alarm state
  - This would help as you can increase the number of datapoints required to trigger an alarm. 
- CORRECT: "Modify the CloudWatch alarm period that triggers your Auto Scaling scale down policy" is the correct answer. 
- CORRECT: "Modify the Auto Scaling group cool-down timers" is the correct answer. 

# SQS

## 1. Standard Queue			
- Unlimited throughput			
- Unlimited messages in the queue			
- Default retention 4 days, maximum 14 days			
- Can have out of order messages (best effort ordering)			
## 2. Producing messages			
- SDK: SendMessage API			
- Message persists in queue until a consumer deletes it			
## 3. Delivery Delay/Delay Queue			
- When Producer pushes a message to queue we can set Delivery delay parameter (value > 0) so that consumers do not see it immediately			
- This is set at Queue level			
- Default is 0 seconds			
- While pushing message to queue, the default value can be overidden using DelaySecond parameter			
## 4. Consuming messages			
- EC2 instances or Lambda or any application			
- Consumer Polls for messages			
- Delete the message using DeleteMessage API			
## 5. Message Visibility timeout			
- After a message is polled by a consumer, it becomes invisible in queue			
- Once message visibility timeout expires, message becomes visible in queue and hence can be polled by another consumer			
- Default message visibility timeout is 30 seconds			
- Use ChangeMessageVisibility API to get moe time to process message			
## 6. Long Polling			
- Helps to reduce cost of using SQS by eleminating the number of empty Responses when no messages are available			
- At Consumer configure parameter
RecieveMessageWaitTimeSeconds			

## 7. ApproximateAgeOfOldestMessage					
- The ApproximateAgeOfOldestMessage metric is useful when applications have time-sensitive messages and you need to ensure that messages are processed within a specific time period.					
- You can use this metric to set Amazon CloudWatch alarms that issue alerts when messages remain in the queue for extended periods of time					
- You can also use alerts to take action, such as increasing the number of consumers to process messages more quickly.					
## 8. Security					
- Encryption:
  - In flight: HTTPS
  - At rest: KMS
  - CSE also supported					
- Access Controls: IAM policies to restrict access to SQS API					
- SQS Access Policies:
  - Configure Cross Account access
  - Allow another services (SNS, S3) to write to SQS					
## 9. Dead letter Queue					
- When consumer fails to process a message within visibility timeout, message goes back to queue.
We can set a threshold of how many times a message can go back to queue					
- After MaximumReceives threshold is exceeded, message goes to a dead letter queue					
- Good for Debugging					
- Process the message from DLQ before it expires (Default 14 days)					
## 10. FIFO Queue					
- Ensures Ordering of data in queue
Messages are processed in order by consumer					
- When using many consumers to process messages from FIFO queue, use a GROUP ID					

## 11. Ordering data in SQS
- Group your messages and have equivalent number of Consumers (No. of consumers = No. of Groups)

## 12. Creating SQS FIFO queue
<img src=images/2.png>

## 13. SQS FIFO queue Prevents DUPLICATES
<img src=images/3.png>

## 14. SQS Decoupling together with Autoscaling
### Autoscaling can be done based on Queue Length Metric
<img src=images/4.png>

### Decoupling between application tiers
<img src=images/5.png>

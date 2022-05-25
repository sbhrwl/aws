# MyBlog
- This website should scale globally
- Blogs are rarely written, but often read
- Some of the website is purely static files, the rest is a dynamic REST API
- Caching must be implement where possible
- Any new users that subscribes should receive a welcome email
- Any photo uploaded to the blog should have a thumbnail generated

## Serving static content, globally
<img src="images/1.png">

## Serving static content, globally, securely
<img src="images/2.png">

## Adding a public serverless REST API
<img src="images/3.png">

## Leveraging DynamoDB Global Tables
<img src="images/4.png">

## User Welcome email flow
<img src="images/5.png">

## Thumbnail Generation flow
<img src="images/6.png">

## Summary
- We’ve seen static content being distributed using CloudFront with S3
- The REST API was serverless, didn’t need Cognito because public
- We leveraged a Global DynamoDB table to serve the data globally
  - (we could have used Aurora Global Database)
- We enabled DynamoDB streams to trigger a Lambda function
- The lambda function had an IAM role which could use SES
- SES (Simple Email Service) was used to send emails in a serverless way
- S3 can trigger SQS / SNS / Lambda to notify of events

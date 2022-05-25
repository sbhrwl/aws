# Software updates offloading
- We have an application running on EC2, that distributes software updates once in a while
- When a new software update is out, we get a lot of request and the content is distributed in mass over the network. It’s very costly
- We don’t want to change our application, but want to optimize our cost and CPU, how can we do it?

## Our application current state
<img src="images/1.png">

## Easy way to fix things!
<img src="images/2.png">

## Why CloudFront?
- No changes to architecture
- Will cache software update files at the edge
- Software update files are not dynamic, they’re static (never changing)
- Our EC2 instances aren’t serverless
- But CloudFront is, and will scale for us
- Our ASG will not scale as much, and we’ll save tremendously in EC2
- We’ll also save in availability, network bandwidth cost, etc
- Easy way to make an existing application more scalable and cheaper

# Event driven architectures

## Use Lambda, SQS and SNS
<img src="images/1.png">

## Fan in Fan out pattern
- deliver to multiple SQS
<img src="images/2.png">

## S3 Events
- S3:ObjectCreated, S3:ObjectRemoved, S3:ObjectRestore, S3:Replication...
- Object name filtering possible (*.jpg)
- Use case: generate thumbnails of images uploaded to S3
- Can create as many “S3 events” as desired
- S3 event notifications typically deliver events in seconds but can sometimes take a minute or longer
- If two writes are made to a single non-versioned object at the same time, it is possible that only a single event notification will be sent
- If you want to ensure that an event notification is sent for every successful write, you can enable versioning on your bucket.
<img src="images/3.png">


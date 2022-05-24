# MyWordPress.com
- We are trying to create a fully scalable WordPress website
- We want that website to access and correctly display picture uploads
- Our user data, and the blog content should be stored in a MySQL database.

## RDS layer
<img src="images/1.png">

## Scaling with Aurora: Multi AZ & Read Replicas
<img src="images/2.png">

## Storing images with EBS
<img src="images/3.png">

<img src="images/4.png">

## Storing images with EFS
<img src="images/5.png">

## Summary
- Aurora Database to have easy Multi-AZ and Read
- Replicas
- Storing data in EBS (single instance application) • Vs Storing data in EFS (distributed application)

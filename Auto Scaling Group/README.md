# Create Auto Scaling Group

We will create an auto scaling group, where we will provision by default 2 instances to be maintained by the auto scaling group, we will then attach it to the load balancer to route traffic to the instances

## Create Auto Scaling Group

Under EC2, click to create auto scaling group, name it TP_ASG and select TPWordpress_LT as the launch template, and click next

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_Name.png)


Select our TP_VPC and select the Public Web One and Public Web two subnets and click next

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_network.png)


Select attach to an existing load balancer and select the TPtargetgroup


Select Elastic Load balancing health check and click next

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_health.png)


Select group size instance capacity, desired 2, minimum 1, maximum 3
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_size.png)


For now we wont select scaling policies, but here you can set the instances to scale in and out according to CPU load, or different scenarios, click next
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_scaling.png)


You can add notifications, when there are changes to your instances, for now we skip
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_notification.png)


You can tag it with WEBASG and click next

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_tag.png)

Click Next

Review and click create
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/ASG_setup.png)


## View Launched instances and website usl

Auto Scaling group has launched two instances
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/launch_ASG.png)


View domain name tutorialpoint.adetunjiaramide.com and create another post to test.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/final_domain_two.png)

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/final_domain.png)


![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/final_domain_three.png)
















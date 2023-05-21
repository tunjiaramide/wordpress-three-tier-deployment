# Create Load Balancer and Route 53

We will create a Load Balancer, with target groups and set up Route 53

## Create Load balancer and target groups

Create Internet facing Application Load balancer and name it TP_LB

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/create_loadbalancer.png)


Choose the TP_VPC and select the public web one and public web two in Network mapping
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/loadbalancer_vpc.png)

Select TPWebSecurity
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/loadbalancer_sg.png)

Create target group in the Listeners 

Select instances and name TP_target_group, leave defaults and next, dont add targets yet, click create.
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/targetgroup_instance.png)

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/targetgroup_name.png)

Refresh and add the TP_target_group to the listener on port 80
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/loadbalancer_targetgroup.png)

Click create load balancer

## Create Route 53 and connect to Load balancer

Register a domain name with AWS or create a hosted zone in Route 53, i have one created, will be creating a record under my hosted zone. 

Will name my hosted zone tutorialpoint.domainname.com, toggle alias and select the load balancer just created. Take note of the A record.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/create_arecordRoute.png)













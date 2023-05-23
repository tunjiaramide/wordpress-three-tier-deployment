# Deploy and host a highly-available WordPress application using EC2, RDS, Route 53, Load balancer, ASG, EFS and VPC.

We will be hosting a highly available, elastic and self healing wordpress application on a three tier web application.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_archictecture_one.png)

## VPC, Public subnets, Private subnets and Nat Gateways
Our Wordpress application will be deployed into a public subnet in a Custom VPC. We will also deploy nat gateways into public subnets, so our database instance in a private subnet can access the internet through the nat gateway.

### RDS and EFS
To achieve elasticity and highly available wordpress that can scale, we need to use Mysql RDS as our database and use NFS to host our wordpress assets, especially the wp-content folder, so if an instance is removed, it wont loose any data.


### Load balancer, ASG and Route53
For us to deploy more instances of our wordpress applications, based on load, we need to set up an Auto Scaling Group, that will increase and decrease our application.

It will be connected to a Load balancer, that will route traffic to the wordpress instances randomly.

As a final step, to access our website from a custom domain name, we will use Route53 to connect our domain name to the Load balancer


### STEPS TO FOLLOW

#### [IAM](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/IAM)
#### [VPC](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/VPC)
#### [NAT GATEWAY](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/Nat-gateway)
#### [SECURITY GROUPS](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/Security-groups)
#### [DB AND EFS](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/DB%20and%20EFS)
#### [LB AND ROUTE53](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/LB%20and%20Route53)
#### [AMI LAUNCH](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/AMI%20Launch)
#### [LAUNCH TEMPLATE](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/Launch%20Template)
#### [AUTO SCALING GROUP](https://github.com/tunjiaramide/wordpress-three-tier-deployment/tree/main/Auto%20Scaling%20Group)

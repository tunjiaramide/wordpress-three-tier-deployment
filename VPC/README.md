# Set up a Custom VPC, Internet Gateways, Public Subnets and Public Route table

In order to successfully deploy our highly available wordpress application, we will be setting up a custom VPC in us-east-1. Create and attach an Internet Gateway to the VPC, then set up two public subnets in two available zones, and attach it to a public route.

## Create VPC, choose CIDR block and enable DNS hostname

Name your VPC, TP_VPC, with cidr block 10.0.0.0/16

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/create_vpc.png)

Enable DNS hostname

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/enable_dns_vpc.png)


## Create Internet Gateway and attach to VPC

Name your Internet Gateway, TP_IGw and attach to TP_VPC

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/create_igw.png)

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/attach_igw.png)


## Create Subnet Public Web One in us-east-1a, with CIDR block and Enable Auto assign IP settings

Name subnet Public Web One in us-east-1a with CIDR block 10.0.1.0/24 under TP_VPC and edit subnet to enable auto assign IP settings

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/public_web_one.png)


## Create Subnet Public Web Two in us-east-1b, with CIDR block and Enable Auto assign IP settings

Name subnet Public Web Two in us-east-1b with CIDR block 10.0.2.0/24 under TP_VPC and edit subnet to enable auto assign IP settings

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/edit_subnet.png)

## Create Public Route, attach Internet Gateway and associate Public Web One and Public Web Two Subnets

Name Public Route, TP_Public_Route and select TP_VPC

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/public_routes.png)

Edit Routes and route TP_IGw internet Gateway to the Internet

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/route_igw.png)

Associate the Public Subnets to the Public Routes

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/associate_public_subnets.png)





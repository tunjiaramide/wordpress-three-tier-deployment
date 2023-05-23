# Create a NAT Gateway, Private Subnets and Private Routes

We need to create private instances to deploy our EFS mount targets and databases inside, so they wont be accessable publicly.


## Create NAT Gateway under Public Web One and Public Web Two and allocate Elastic IP
Name it TP_WebOne_NGw and TP_WebTwo_NGw

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/public_one_nat.png)

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/public_two_nat.png)

## Create Subnet Private App One in us-east-1a with CIDR block
Name it Private App One in us-east-1a with CIDR block 10.0.3.0/24

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/private_app_one.png)


## Create Subnet Private Data One in us-east-1a with CIDR block

Name it Private Data One in us-east-1a with CIDR block 10.0.4.0/24

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/private_data_one.png)


## Create Subnet Private App Two in us-east-1b with CIDR block

Name it Private App Two in us-east-1b with CIDR block 10.0.5.0/24

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/private_app_two.png)


## Create Subnet Private Data Two in us-east-1b with CIDR block

Name it Private Data Two in us-east-1b with CIDR block 10.0.6.0/24

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/private_data_two.png)


## Create Private Routes, Attach Nat Gateways and Associate the private subnets 

Name Private Route - TP_Private_Route_One

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/private_route_one.png)

Route Traffic to TP_WebOne_NGw and associate Private App One and Private Data One subnets

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/route_one_nat.png)

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/associate_private_one.png)

Name Private Route - TP_Private_Route_Two

Route Traffic to TP_WebTwo_NGw and associate Private App Two and Private Data Two subnets

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/associate_private_two.png)





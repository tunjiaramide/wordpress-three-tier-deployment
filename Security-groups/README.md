# Create a Security Groups

We need to create security groups to protect our instances, EFS and databases.
Please select your custom VPC, TP_VPC while creating the SG.

## Create Public Web Security group for the Load balancers and wordpress instances, with port 80 open to the public

Name it TPWebSecurity and open HTTP port 80 to the world, this will house the load balancer and wordpress instances.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/tp_websg.png)


## Create Private App Security group for the EFS, and open NFS port 2049 to only receive traffic from TPWebSecurity

Name it TPAppSecurity and open NFS port 2049 only to TPWebSecurity, this will protect our NFS mount targets only take traffic from the Wordpress instances.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/tp_appsg.png)

## Create Private Data Security group for the Web apps, with port 3306 open and only receive traffic from the Private App Security Group.

Name it TPDataSecurity and open port 3306 only to TPWebSecurity, this will protect our database instance and only take traffic from wordpress instance.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/tp_datasg.png)









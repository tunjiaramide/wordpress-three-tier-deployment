# Create a Database and EFS

We will create an RDS database and NFS server to use with Wordpress.

## Create Subnet Groups with us-east-1a and us-east-1b
Go to RDS and create DB subnet groups, name it TP_DBSubnetGroup
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/create_subnetgroup.png)


Select Available zones, and select the Private Data subnets
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/dbsubnet_group_subnets.png)

## Create Database

Select Standard Create with MySQL
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/select_mysql.png)

Select Multi-AZ DB Instance to deploy in two available zones i choose free tier
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/choose_multi_az.png)

Name the database identifier - tp-database, set the username - tpwordpress and password - tpwordpressdb123
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/set_password.png)

Select instance and storage
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/db_instance.png)

Select TP_VPC and tp_dbsubnetgroup and select no to public access
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/db_vpc.png)

Choose TPDataSecurity in VPC Security Groups and click create
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/db_sg.png)

Under additional configuration, create initial database - tpdbwordpress, which will be used for wordpress installation
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/rds_database_name.png)

## Create EFS

Name it TP_NFS and select TP_VPC, choose customize, disable encryption and click Next
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/create_efs.png)

Select the Private App Subnets, Choose TPAppSecurity in the mount targets, click next to create
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/efs_sg.png)

Take note of the EFS ID
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/efs_complete.png)










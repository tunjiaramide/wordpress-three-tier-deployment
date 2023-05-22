# Create Wordpress AMI

We will create configure a Wordpress instance, install all dependencies, use the RDS, configure the NFS, and update wordpress with the A record we created in Route 53. Then after we will create the AMI and create a Launch template.

## Launch EC2 in public subnet to use to configure AMI

Create EC2 instance, name it wordpress_ami, we will use Amazon linux 2

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/web_amazon.png)

Select Instance t2.micro and choose proceed without key pair
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/web_instance.png)

Under Network, select TP_VPC and Public_Web_One
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/web_vpc.png)

Select TPWebSecurity

Under advanced details, under IAM instance profile, select EC2_EFS_Role
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/web_role.png)


Scroll down under user data update with the code below

Update the DBName, DBUser, DBPassword, DBHost and EFSID created earlier, and copy to install the code below in the instance

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/web_userdata.png)

```
#!/bin/bash -xe

sudo su

# Setpassword & DB Variables
DBName='tpdbwordpress'
DBUser='tpwordpress'
DBPassword='tpwordpressdb123'
DBHost='tp-database.ca9eviv0ckui.us-east-1.rds.amazonaws.com'
EFSID='fs-0208bfa196d8ac641'


# System Updates
yum -y update
yum -y upgrade

# STEP 2 - Install system software - including Web and DB

yum install -y httpd wget amazon-efs-utils
amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2


# STEP 3 - Web and DB Servers Online - and set to startup
systemctl enable httpd
systemctl start httpd

# STEP 4 - Mount EFS on EC2
mkdir -p /var/www/html/wp-content
chown -R ec2-user:apache /var/www/
echo -e "$EFSID:/ /var/www/html/wp-content efs _netdev,tls,iam 0 0" >> /etc/fstab
mount -a -t efs defaults


# STEP 5 - Install Wordpress
wget http://wordpress.org/latest.tar.gz -P /var/www/html
cd /var/www/html
tar -zxvf latest.tar.gz
cp -rvf wordpress/* .
rm -R wordpress
rm latest.tar.gz

# STEP 6 - Configure Wordpress
cp ./wp-config-sample.php ./wp-config.php
sed -i "s/'database_name_here'/'$DBName'/g" wp-config.php
sed -i "s/'username_here'/'$DBUser'/g" wp-config.php
sed -i "s/'password_here'/'$DBPassword'/g" wp-config.php
sed -i "s/'localhost'/'$DBHost'/g" wp-config.php
sed -i "/<?php/a define('FS_METHOD', 'direct');" wp-config.php

# Step 6a - permissions 
usermod -a -G apache ec2-user   
chown -R ec2-user:apache /var/www
chmod 2775 /var/www
find /var/www -type d -exec chmod 2775 {} \;
find /var/www -type f -exec chmod 0664 {} \;


```

We will update the TPDataSecurity to temporarily allow traffic from the TPWebSecurity on port 3306, so the instance can communicate with the Database while we create this AMI.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/edit_datasg.png)


## Instance wordpress and update site url with A record

Log on to the Public IP, set username and password to login

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_install.png)

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_admin.png)


Create a post

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_createpost.png)

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_postsuccess.png)

Once logged in, go to general settings in Wordpress and update the site url to the A record earlier created - tutorialpoint.adetunjiaramide.com

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_siteurl.png)

After clicking update, website will show Temporarily unavailable, that is fine, because we have not added our instances to the load balancer, which is linked to the domain name.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_unavailable.png)

Go back to the instance, and click instance state > stop
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_stop.png)

After in a stopped state, click Actions > Image and templates > Create image
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_createami.png)

Name it wordpress_ami_starter, and click create
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_ami.png)

Once AMI is in a created stage you can proceed
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/wordpress_amiready.png)












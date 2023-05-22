# Create a Launch Template

We will create a launch template from the Wordpress AMI created earlier and use it for our auto scaling group which will be launched in the private app subnets

## Create Launch Template

Go to launch template under intances in EC2, and click launch template
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/LT_find.png)

Name it TPWordpress_LT
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/LT_name.png)

Select the AMI created earlier, wordpress_ami_starter
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/LT_ami.png)

Choose the instance type, t2.micro
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/LT_instance.png)

Under network settings, dont include in template, choose TPAppSecurity 
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/LT_sg.png)

Under Advanced settings, select our instance role
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/LT_role.png)

No need for extra user_data, click create
![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/LT_success.png)














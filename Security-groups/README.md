# Create a Security Groups

We need to create security groups to protect our instances and databases.

## Create Public Web Security group for the Load balancers, with port 80 open and open to the public

Name it TP Web Security and open HTTP port 80 and NFS port 2049 to the internet, this will house the load balancer

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/tp_web_sg.png)


## Create Private App Security group for the Web apps, with port 80 open and only receive traffic from the load balancer

Name it TP App Security and open HTTP port 80 and NFS port 2049 only to TP web security, this will protect our wordpress instance and only take traffic from the load balancer.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/tp_app_sg.png)

## Create Private Data Security group for the Web apps, with port 3306 open and only receive traffic from the Private App Security Group.

Name it TP Data Security and open port 3306 only to TP App security, this will protect our database instance and only take traffic from wordpress instance.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/tp_data_sg.png)









# Set up a IAM roles to attach to the EC2

We will be attaching a NFS File server to the EC2 instances and also connect to the private instances using instance connect from the web console.

We will create an IAM role and attach two policies, first AmazonSSMManagedInstanceCore to allow us connect to our instance without SSH and AmazonElasticFileSystemClientFullAccess, to allow EC2 connect to EFS.

## Create an IAM role and attach AmazonSSMManagedInstanceCore and AmazonElasticFileSystemClientFullAccess Policy

We create an IAM Role named EC2_EFS_Role with AmazonSSMManagedInstanceCore and AmazonElasticFileSystemClientFullAccess Policy attached.

![alt text](https://adetunjiaramide.s3.amazonaws.com/images/aws/three-tier-wordpress/IAM_Role.png)




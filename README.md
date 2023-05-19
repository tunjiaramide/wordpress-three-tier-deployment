# Deploy and host a highly-available WordPress application using EC2, RDS, Route 53, Load balancer, ASG, NFS and VPC.


We will be hosting a highly available, elastic and self healing wordpress application on a three tier web application.

## VPC, Private subnets, Nat Gateways
Our Wordpress application will be deployed into a private Subnet in a Custom VPC. The application instance can't be reached directly from the internet.

We will configure nat gateways to allow the instance to connect to the internet.

### RDS and NFS
To achieve an elastic and highly available wordpress that can scale, we need to use Mysql RDS as our database and use NFS to host our wordpress assets, so if an instance is removed, it wont loose any data.


### Load balancer, ASG and Route53
For us to deploy more instances of our wordpress applications, based on load, we need to set up an Auto Scaling Group, that will increase and decrease our application.

It will be connected to a Load balancer, that will route traffic to the wordpress instances randomly.

As a final step, to access our website from a custom domain name, we will use Route53 to connect our domain name to the Load balancer
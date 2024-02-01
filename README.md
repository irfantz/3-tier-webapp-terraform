# 3-tier-webapp-terraform
AWS-3tier-Webapp-Terraform

Overview
The ec2.tf file is a Terraform configuration file primarily focused on defining AWS EC2 resources. It is part of a larger infrastructure setup and plays a key role in managing the compute aspect of the cloud environment.

Contents
This file contains definitions for various AWS resources related to Elastic Compute Cloud (EC2) and related services. Here are the key elements defined in this file:

Resources
aws_autoscaling_attachment: Manages the attachment of an EC2 autoscaling group to an AWS load balancer.
aws_autoscaling_group: Defines an EC2 autoscaling group to ensure the correct number of EC2 instances are running.
aws_launch_template: Specifies a template for launching EC2 instances, including settings like instance type and AMI.
aws_lb: Sets up an AWS Load Balancer to distribute incoming application traffic across multiple EC2 instances.
aws_lb_listener: Manages a listener for the AWS Load Balancer, handling incoming requests.
aws_lb_target_group: Defines a group of target resources, like EC2 instances, that traffic is directed to by the load balancer.
Usage
To use this file, ensure you have the necessary AWS credentials and Terraform installed. It should be part of a Terraform project where you can run terraform apply to create or update the infrastructure as per the definitions in this file.

README for iam.tf
Overview
The iam.tf file is a Terraform configuration file designed to manage AWS Identity and Access Management (IAM) resources. This file plays a crucial role in defining and controlling access to AWS services and resources in a secure manner.

Contents
This file contains Terraform definitions for various AWS IAM resources. The key elements defined in this file include:

Resources
aws_iam_instance_profile: Manages an IAM instance profile, which is a container for an IAM role that can be used to pass role information to an EC2 instance.
aws_iam_role: Defines an IAM role, specifying a set of permissions for making AWS service requests.
aws_iam_role_policy_attachment: Manages the attachment of a specific managed policy to a specified IAM role.
Usage
To use this file, you need appropriate AWS credentials and Terraform installed. It's part of a larger Terraform project and should be applied with terraform apply to manage IAM-related configurations in your AWS environment.

README for output.tf
Overview
The output.tf file is a Terraform configuration file used for defining output values in a Terraform module or root module. These outputs can be useful for displaying a subset of the resource attributes or to provide data to other Terraform modules.

Contents
This file is specifically focused on declaring output values from the resources defined in other Terraform configuration files. The key output defined in this file is:

Output
alb_dns_name: This likely represents the DNS name attribute for an Application Load Balancer (ALB) deployed within the AWS environment. It's useful for referencing the ALB's DNS name in other configurations or for external use.
Usage
Outputs in Terraform are like return values for a module. They are used to expose certain values to other parts of your Terraform configuration or to the user. To see the values of these outputs, you can run terraform output after applying your Terraform configuration. This file does not create resources but provides information about the resources created by other Terraform files in the project.

README for rds.tf
Overview
The rds.tf file is a Terraform configuration file dedicated to setting up and managing AWS Relational Database Service (RDS) resources. This file is key for creating and maintaining database instances in the cloud infrastructure.

Contents
This file contains Terraform resource definitions for AWS RDS components. The main elements defined in this file include:

Resources
aws_db_subnet_group: Configures a DB subnet group for RDS databases, which defines subnets in specific Availability Zones.
aws_rds_cluster: Manages an RDS cluster, which is a collection of DB instances that can be managed as a single unit.
aws_rds_cluster_instance: Defines individual instances within an RDS cluster. These instances are where the databases actually run.
Usage
To use this file, ensure you have AWS credentials configured and Terraform installed. It's designed to be a part of a larger Terraform project. Running terraform apply with this file in your project will set up the necessary RDS components in your AWS account.

README for testing.tfvars
Overview
The testing.tfvars file is a Terraform variable definitions file. It is used to specify values for variables that are used in Terraform configurations. This file is particularly useful for customizing Terraform configurations without altering the main configuration files.

Contents
This file contains key-value pairs defining various configuration parameters. These parameters typically correspond to variables defined in other Terraform files within the project. Key parameters defined include:

Network configurations like VPC, subnets, and CIDR blocks.
Names and identifiers for resources such as Internet Gateways, NAT Gateways, and Elastic IPs.
Some of the specific variables defined are:

VPCName: Name of the VPC.
LandmarktechvpcCIDR: CIDR block for the VPC.
PublicSubnet1_CIDR, PublicSubnet2_CIDR: CIDR blocks for public subnets.
PrivateSubnet1_CIDR to PrivateSubnet4_CIDR: CIDR blocks for private subnets.
all_IPs: CIDR block representing all IPs.
igw: Name for the Internet Gateway.
nat_gw, nat_gw2: Names for NAT Gateways.
eip, eip2: Names for Elastic IPs.
Usage
To use this file, include it in a Terraform project where these variables are referenced. When running Terraform commands, specify this variable file using the -var-file option (e.g., terraform apply -var-file="testing.tfvars"). This allows for the customization of Terraform configurations for different environments or scenarios.

README for variables.tf
Overview
The variables.tf file is a Terraform configuration file used for declaring variables. These variables are essential for making Terraform configurations more dynamic and reusable, allowing for parameterization of configuration values.

Contents
This file contains declarations for a range of variables that are likely used across various Terraform configuration files within the project. Key variables declared in this file include:

Infrastructure components such as VPC, subnets, and load balancer configurations.
AWS-specific settings like region, instance types, and credentials.
Some of the specific variables declared are:

VPCName, Landmarktechvpc, Landmarktechvpccidr: Related to VPC configuration.
PublicSubnet1_CIDR, PublicSubnet2_CIDR: CIDR blocks for public subnets.
PrivateSubnet1_CIDR to PrivateSubnet4_CIDR: CIDR blocks for private subnets.
ApplicationLoadBalancer: Configuration for an application load balancer.
access_key, secret_key: AWS credentials (usually recommended to be passed through safer means like environment variables or IAM roles).
region, instancetype: AWS region and EC2 instance type.
all_IPs, igw, eip, nat_gw: Network-related variables.
Usage
The variables declared in this file are referenced in other Terraform files. When running Terraform commands, values for these variables can be provided through .tfvars files or directly at the command line. This allows for flexibility and reusability in different deployment environments.

README for vpc.tf
Overview
The vpc.tf file is a Terraform configuration file focused on setting up and managing a Virtual Private Cloud (VPC) in AWS. This file is crucial for defining the network infrastructure in which other AWS resources like EC2 instances, RDS databases, and load balancers are deployed.

Contents
This file contains definitions for various AWS resources related to VPC configuration. The key resources defined in this file include:

Resources
aws_vpc: Establishes the VPC within which all other network-related resources are contained.
aws_subnet: Configures subnets within the VPC, which can be designated as public or private.
aws_internet_gateway: Sets up an internet gateway for the VPC, enabling communication between the VPC and the internet.
aws_route_table and aws_route_table_association: Manage routing tables and their associations with subnets.
aws_nat_gateway and aws_eip: Set up a NAT gateway (with associated Elastic IP) to allow private subnets to access the internet.
aws_security_group: Defines security groups, which act as virtual firewalls to control inbound and outbound traffic to AWS resources.
Usage
To use this file, you need to have AWS credentials and Terraform installed. This file is part of a Terraform project and is applied using the terraform apply command. This will establish the network infrastructure in your AWS account as defined in the file.

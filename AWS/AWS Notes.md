## Introduction
- Creating my Account:
	- email: Nathankarns6@gmail.com
	- username: nathankarns6
	- password: Lionsden1#
- IAM Login Info (Recommended to always use this user when logging in):
	- alias: aws-nathan-alias-v1
	- username: nathan
	- password: Lionsden1#

## What is Cloud Computing?
- A Server is composed of 5 main things:
	1.  CPU, which does the computations
	2. RAM, which is memory
	3. Storage, for data
	4. Database, to store data in a structured way
	5. Network, Routers, Switch, DNS Server
- Network: Cables, routers, servers, connected with each other.
- Router: A networking device that forwards data pockets between computer networks.
- Switch: Takes a pocket and sends it to the correct server/client on your network.
- Problems with traditional IT approach:
	- Pay for rent for data center
	- Pay for power supply
	- Scaling is limited
	- Team needed to monitor infrastructure
	- Natural disasters
- Cloud computing: On demand delivery of compute power, database storage, applications, and other IT resources. Pay as you go pricing. Can provision exactly the right type and size of computing resources you need. Has simple interface across services.
- Deployment models of the cloud:
	- Private Cloud: Cloud services used by a single organization, not exposed to the public, has complete control and security.
	- Public Cloud: Examples include Azure, AWS, GCP, AWS. Cloud services here are owned and operated by a 3rd party cloud service provider and delivered over the internet.
	- Hybrid Cloud: Keep some services on premises and extend some services to the cloud.
- 5 Characteristics of Cloud Computing:
	1. On demand self service
	2. Broad network access
	3. Multi tenancy and resource pooling
	4. Rapid elasticity and scalability
- 6 Advantages of cloud computing: 
    1. Trade capital expense for operational expense.
    2. Benefit from massive economies of scale.
    3. Stop guessing capacity.
    4. Increase speed and agility
    5. Save money running and spending on data centers
    6. Go global in minutes.
- Types of cloud computing:
	- Infrastructure as a service, ex: AWS EC2
	- Platform as a service.
	- Software as a service.
- AWS Global Infrastructure:
	- AWS Regions: Clusters of data centers. You should choose a region based on compliance, proximity, available services, pricing, etc.
	- AWS Availability zones: Usually 3 per region (max 6). These consist of 1 or more discrete data centers with redundant power, networking, and connectivity. Isolated from disasters. 
	- AWS Data Centers.
	- AWS Edge locations/Points of Presence. More than 400.

## IAM
- IAM: Identity and access management. It is a global service. A root account is created by default, it shouldn't be used or shared.
- Users/groups can be assigned JSON documents called policies.
- Principle of least privilege: Granting a system or user access to only the essential dat/resources that are required to perform a task.
- IAM Policy structure consists of:
	- Version Number (Usually 2012-10-17). Policy language version.
	- ID for policy (optional)
	- Statement: one or more individual statements.
	- Statements consist of: 
		- SID - an id for a statement (Optional)
		- Effect - Whether or not statement allows/denys access
		- Principal - Account/user/role to apply policy to
		- Action - List of actions this policy allows or denys
		- Resource - List of resources to which the actions are applied.
		- Condition - Conditions for when this policy is in effect (optional)
- IAM Users/Groups Protection consists of: 1) Password policy (min length, require specific types, allow users to change pwd, pwd expiration, prevent pwd reuse) 2) MFA (pwd + Security device, if pwd is stolen acc is not comprimised, Options include: 1) Virtual MFA Device like google auth, authy, etc and allow for multiple tokens on 1 device 2) Universal 2nd factor security key 3) hardware key fob MFA device 4) AWS GovCloud Hardware Key fob)
- How to set up a password policy: Click IAM > Account Settings > edit password policy > custom
- To access AWS you have 3 options: AWS management console, CLI (protected by access keys), SDK (protected by access keys, language specific)
- AWS CLI setup includes: Download the CLI for windows/mac > run installer > accept terms > open a command line terminal > run: aws --versiom to verify
- Creating access keys in AWS: Click IAM > users > *username* > security credentials > create access key > command line access key > create. Then, go to terminal > runs: aws configure > enter access key ID > enter secret access key > enter region name (us-east-2 for example) > enter default format. Then, run: aws iam list-users to verify.
- AWS Cloudshell: Has limited cpu, memory, and storage. It is not ideal for running large scripts, computing code, or processing data.
- IAM Roles: Used when services will need to perform actions on your behalf. The way to do this is to assign permissions to IAM services with IAM roles. Common roles include: ec2 instance roles, lambda function roles, and roles for cloudformation.
- How to create an IAM role: Click IAM > roles > create role > aws service > use case (EC2) > default EC2 type > next > attach policy (IAMReadOnlyAccess) > enter role name > create role.
- 2 main IAM security tools: 1) IAM Credentials report (at account level), this is a report that lists all your account's users and the status of their various credentials 2) IAM Access Advisor (at user level), this shows service permissions granted to a user and when those services were last used.
- How to generate a credentials report: Click IAM > credentials report > download credentials report
- How to view IAM Access Advisor: Click IAM > users > *username* > last accessed
- Shared Responsibility Model For IAM... Responsibilities handled by AWS: 1) Infrastructure (global network security), 2) Configuration & vulnerability analysis, 3) Compliance Validation. Responsibilities handled by the user, YOU: 1) users, groups, roles, policies, management and monitoring 2) Enabling MFA 3) Rotating keys often 4) Use IAM tools and apply appropriate perms 5) Analyzing access patterns and review perms.

## EC2
- How to set up a zero spend budget in AWS: Using your IAM Account go to Billing and cost management > Budgets > Then choose a zero spend budget. You can then name it and add your email for notifications.
- EC2 (Elastic Compute Cloud): Is Infrastructure as a service and consists of: Renting virtual machines (ec2), Storing data on virtual drives (EBS), Distributing load across machines (ELB), and scaling the services using auto scaling group (ASG).
- EC2 sizing and config options: 1) Operating system (linux, mac, windows), 2) How much compute power and cores (CPU), 3) How much RAM 4) How much storage space (network attached and hardware), 5) Network Card (speed of card, public IP) 6) Firewall rules (security group), 7) Bootstrap script (ec2 user data)
- EC2 user data bootstrapping: Bootstrapping means launching commands when a machine starts, the script only runs at instances first start. With bootstrapping you can automate tasks like installing updates, installing software, download common files, etc. The ec2 user data script runs as root user.
- There are 7 main different EC2 instance types. The naming convention of these types: m5.2xlarge, for example. The "m" is the instance class, the "5" refers to the generation of the instance (generation of hardware), and the "2xlarge" refers to the size within the class.
- General Purpose EC2 instance type: Is great for a diversity of workloads like web servers or code repos. They balance between compute, memory, networking.
- Compute optimized EC2 Instance Type: Great for compute intensive tasks that require high-performance processors like: batch processing workloads, media transacting, high performance web servers, high performance computing, ML, gaming servers. These instance types start with "C", like "C5", etc.
- Memory optimized EC2 instance type: Great for workloads that process large data sets in memory. Use cases include: High-performance relational/non-relational database, distributed web scale cache stores, in memory DBs optimized for BI, apps performing real-time processing of big unstructured data. These instance type's names being with "R".
- Storage optimized EC2 instance types: Great for storage intensive tasks that require high, sequential read and write access to large data sets on local storage. Use cases include: High frequency OLTP systems, Relational and NoSQL DBs, cache for in-memory DBs, data warehousing apps, and distributed file systems. 
- Security Groups: Control how traffic is allowed in or out of ec2 instances , they contain "allow" rules. Can reference by IP or by security group, they act as a firewall on EC2 instances. They regulate Access to ports, authorized IP ranges, control of inbound network, control of outbound network. Security groups can be attached to multiple instances, locked down to a region/VPC combination, live outside of the ec2 and if traffic is blocked by the group then the ec2 instance won't see it, good idea to maintain SCP security group for SSH access, If an app is not accessible then it is a security group issue, if an app gives a "connection refused" error then it is an application error or its not launched, by default all inbound traffic is blocked and all outbound traffic is allowed.
- Classic Ports to Know: 22 is for ssh, 21 is for FTP, 22 for SFTP, 80 for HTTP, 443 for HTTPS, 3389 for RDP (remote desktop protocol).
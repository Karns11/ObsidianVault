
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
- Important to keep in mind that if you try to access an ec2 instance but get a timeout, or infinite loading experience, the cause is almost certainly a security group issue.
- SSH is a command line utility that can be used on mac or linux and windows (>= version 10). Putty is the ssh alternative for windows < version 10. SSH allows you to control a remote machine using the command line.
- how to ssh into an ec2 instance initially: make sure ec2 instance is running, ssh connection is allowed with port 22, then open command line and run: ssh ec2-user@'publicEC2IP'. Use ec2-user here because aws linux 2 AMI instance type auto creates this user for you. But, you must use your key pair assigned to the instance by doing this: ssh -i "keyPairPath" ec2-user@"EC2PublicIP". You might get an error initially, so run chmod 0400 first "KeyPairPath".
- C2 Instance Connect is an alternative to sshing into the instance from your command line. It does use SSH under the hood, so keep in mind that security group rule should be enabled for port 22. Note AWS Linux 2 AMI comes equipped with aws CLI which is really helpful and allows you to run aws iam commands for example.
- How to add IAM role to ec2 instance: go to instances, in top right click actions >  security > modify IAM role > Then choose IAM rule. 
- EC2 Instance Purchasing Options: 1) On-Demand Instances, which are great for short workloads, have predictable pricing, and pay by second 2) Reserved (up to 72% discount compared to on-demad), 1 and 3 years, good for long workloads 3) Savings Plans (up to 72% discount), Commitment to an amount of usage, long workload 4) spot instances (up to 90% discount), short workloads, cheap, less reliable 5) Dedicated hosts (most expensive option useful for companies that have strong regulatory compliance needs. Offer on-demand or reserved purchasing options.), book an entire physical server, control instance placement      6) Dedicated Instances (Instance runs on hardware dedicated to you), no other customers share your hardware 7) Capacity Reservations, reserve capacity in specific Availability Zone for any duration, access it whenever you need it with no time restriction, no billing discounts and charged on-demand rate, great for short term uninterrupted workloads that need to be in a specific AZ. 
- EC2 On demand has the highest cost, but no upfront payment. Linux/Windows billing is per second, after the first minute, all other operating systems are bulled per hour. It is recommended for short term uninterrupted workloads. 
- EC2 spot instances provide the biggest discounts, are great for workloads that are resilient to failure like batch jobs, data analysis, image processing, any distributed workloads, etc. Not suited for critical jobs or databases!
- Key thing to remember about Dedicated Hosts VS Dedicated Instances: Dedicated Instances mean that you have your own instance on your own hardware. Dedicated hosts mean you get access to the physical server itself.
- Shared Responsibility Model For EC2: 1) AWS: Infrastructure, Isolation on Physical Hosts, Replacing faulty hardware, compliance validation. 2) You: Security group rules, OS patching and updates, Software and utilities installed on EC2 instance, IAM Roles & IAM user access management, Data security on your instance. 

## EC2 Instance Storage
- EBS Volume: (Elastic Block Store) is a network drive (not a physical drive) that you can attach to your instances while they run. It allows your instances to persist data even after their termination. They can only be mounted to one instance at a time and are bound to a specific AZ. Think of them as a network USB Stick. An EBS Volume can be detached from one instance and attached to another one quickly. You must provision the capacity of these (size, and IOPS), you will get billed for this as well. You can attach multiple EBS Volumes to a single EC2 instance. EBS Volumes do have a "Delete on Termination" attribute which controls the behavior of the EBS Volume when the instance terminates. Root volume of the instance is deleted on termination by default, but any other attached volume is not deleted on termination by default. A use case for this is when you want to retain data in the root volume when an instance is terminated, so you would uncheck that attribute in the console for the root volume.
- How to create an EBS Volume: Click Volumes under Elastic Block Store within EC2 > Create Volume button in top right > Select General Purpose SSD (gp3) for volume type > Seelct Size, IOPS, Throughput And the correct AZ that you instance is running in. Then, once it is created, in the Volumes console, select the volume, then actions > attach volume, then select the instance you want to attach it to.
- EBS Snapshots: Allow you to make a backup (snapshot) of you EBS Volume at any point in time. Recommended to detach your volume from your instance before snapshotting, but not required. It allows you to copy your data across AZ's or region if you want. EBS Snapshot featured include: EBS Snapshot Archive, which allows you to move a snapshot to an archive that is cheaper to store your data, but you won't be able to access it right away. Also, EBS Snapshot Recycle Bin, which allows you to save some data in a recycle bin for up to 1 year after you delete it.
- How to create a snapshot: Click on your volume you want to create a snapshot of > Actions > Create Snapshot and name it. Done. Then, you can create a volume from this snapshot by clicking your snapshot > Actions > Create Volume from Snapshot > same set up as creating a volume basically, can choose any AZ > Create. Now you will see a new volume with a snapshot ID in your volumes console.
- To Archive a snapshot, you just click the snapshot > Actions > Archive.
- To create a recycle bin retention policy for a snapshot, click recycle bin in the snapshot console > takes you to a new page where you can easily create a retention policy for snapshots, instances, etc. Now, when you delete a snapshot, it will show up here for the length you described previously when creating the policy and you have the option to easily restore it if you'd like.
- AMI: Amazon Machine Image, which are customizations of EC2 Instances where you have your own software, configuration, operating system, monitoring, etc. These allow for faster booting because all of the software, configurations, etc is pre-packaged. AMIs are built for specific regions and can be copied across them. 
- How to create an AMI: First, for example, launch an instance, you can follow the same directions from earlier... Then, once it is launched and running > right click the image > Click Image and templates > create image > Name it > Create image... Now you can see it in the AMI Console. Now you can launch instances from this AMI. Choose the AMI Just created from the AMI Selection section. The reason why someone might do this is to speed up the booting time. Because the user data script installs http already, so no need to add that to the user data script this time.
- EC2 Image builder is used to automate the creation of virtual machines or container images, and this can be run on a schedule. It is a free service, you only pay for underlying resources.
- Local EC2 Instance Stores should be used when you need a high-performance hardware disk. It has better I/O performance and is ephemeral storage. There is a risk of data loss if hardware fails. Good use cases for this include: buffer, cache, scratch data, temporary content, etc.
- EFS (Elastic File System): This is a managed NFS (Network File System) that can be mounted on 100s of EC2s. This works only with Linux EC2 instances and across multiple AZs. This is highly available, scalable, and expensive (about 3x the price of EBS volumes), you pay per use and no capacity planning. EFS is something that can be shared across multiple different instances and all those instances will see the same files, for example. This is different from EBS. EFS Also has an infrequent access storage class, which is a storage class that is optimized for files that are not accessed daily and gives you up to 92% discounts. EFS IA will automatically move your files based on their last accessed date, once you enable it.
- Shared Responsibility Model for EC2 Storage: 1) AWS: Infrastructure, Replication for data for EBS Volumes and EFS drives, Replacing faulty hardware, ensuring their employees cannot access your data. 2) You: Setting up backup/snapshot procedures, setting up data encryption, any data on the drives.
- Amazon FSx: Launches 3rd party high performance file systems on AWS, it is a fully managed service. Two main ones: 1) Amazon FSx for windows File Server, which is a network file system for windows users 2) Amazon FSx for Lustre, this is storage for high performance computing, good for ML, analytics, Video processing, financial modeling, etc. 
- EC2 Instance Storage Summary: 1) EBS Volumes are network drives attached to one EC2 instance at a time, mapped to AZ's, and you can use snapshots for backups or transferring data across AZs. 2) AMIs are ready-to-use EC2 instances with our customizations. 3) EC2 Image builders automate the building, testing, and distribution of AMIs. 4) EC2 Instance stores are high-performance hardware disks attached to our EC2 instance and are lost when the instance is stopped/terminated 5) EFS is a (SHARED) network file system that can be attached to 100s of instances in a region. 6) EFS-IA is a cost optimized storage class for infrequently accessed files 7) FSx for windows is a network file system for windows users 8) FSx for Lustre is a high performance computing linux file system.

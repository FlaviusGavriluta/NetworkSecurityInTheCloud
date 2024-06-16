# Network Security In The Cloud

## Story

Explore security groups and NACLs to see how they protect your network and resources. By blocking ssh access, using private VPCs, and nnot including any authorisation keys, your EC2 instances are well protected. But what if you need to access and run some ad-hoc commands? AWS provides a browser-based interactive shell and a CLI to manage your Windows and Linux instances.

## What are you going to learn?

- What are security groups in AWS
- What are Network Access Control Lists, NACLs in AWS
- How to add inbound and outbound rules
- How to secure your EC2 instances and other AWS resources
- How to troubleshoot network traffic

## Tasks

1. Observe behaviour when dealing with Security Groups on EC2 instances
    - Create an EC2 instance of type Amazon Linux(free-tier) with default settings
    - As soon as the IP is visible start `ping` from your machine and let it run continuously
    - In your EC2 instance, find the associated security group and enable ICMPv4 (ping) from your IP
    - While instance is up and running, disable ICMP rule from the SGs
    - Observe `ping` results. Does ping stop responding? Why such behaviour?

2. Connect securely to your EC2 instance using SSM Agent
    - - Creante an EC2 instance `my_ec2` with type Amazon Linux 2 (free-tier)
- Select an existing security group and choose `default`. Also, proceed without a key pair when prompted in the last tab
- Ensure your instance has no IAM roles or key pairs
    - - Create an IAM Role `ec2_role` (using EC2 service) and attach `AmazonSSMManagedInstanceCore` policy
- Attach `ec2_role` to your EC2 instance `my_ec2`
    - Go to Session Manager in SSM, select the new instance and hit `Start Session`

## General requirements

None

## Hints

- For continuous `ping` in Windows use `-t` parameter
- Roles can be attached to `running` ec2 instances using Actions drop-down menu, Security, Modify IAM Role
- Session Manager is available in __AWS Systems Manager__ under _Node Management_
- New instances might take several minutes to appear in the list of SSM Target instances
- Block all ssh connectivity and/or use a private VPC for your ec2 instance, SSM still works fine

## Background materials

- <i class="far fa-exclamation"></i> [Security Groups vs NACLs](https://www.fugue.co/blog/cloud-network-security-101-aws-security-groups-vs-nacls)
- <i class="far fa-video"></i> [Security Groups vs NACSs](https://www.youtube.com/watch?v=ttc0b2NZTV0)
- <i class="far fa-video"></i> [AWS Essentials: Network Access Contol List](https://www.youtube.com/watch?v=vJzHn24TNQE)
- <i class="far fa-exclamation"></i> [Install AWS SSM Agent on EC2 instances](https://aws.amazon.com/premiumsupport/knowledge-center/install-ssm-agent-ec2-linux/)

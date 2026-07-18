# AWS VPC Setup — Custom Network Architecture

## What I Built
Created a custom AWS VPC with a public subnet,
Internet Gateway, Route Table and launched an
EC2 instance inside the VPC.

## Tools Used
- AWS Console
- Google Chrome
- Claude AI (guidance)

## What I Did
- Created VPC: devops-vpc (10.0.0.0/16)
- Created Public Subnet: devops-public-subnet 
  (10.0.1.0/24)
- Created Internet Gateway: devops-igw
- Attached IGW to devops-vpc
- Created Route Table: devops-route-table
- Added route: 0.0.0.0/0 → devops-igw
- Associated subnet with route table
- Launched EC2 inside VPC: devops-vpc-server
- Confirmed public IP: 3.88.16.208
- Confirmed private IP: 10.0.1.240

## What I Learned
- A VPC is your own private network inside AWS —
  isolated from other AWS customers for security
- Subnetting = creating networks inside a network
  — each subnet is a smaller section of your VPC
- An Internet Gateway is the door between your
  VPC and the public internet
- A Route Table acts as a signpost — 0.0.0.0/0
  means "send all traffic to the internet gateway"
- Without associating the subnet to the route
  table, the subnet remains private

## Architecture
Internet → Internet Gateway (devops-igw)
  → VPC (devops-vpc) 10.0.0.0/16
    → Route Table (devops-route-table)
      → Public Subnet 10.0.1.0/24
        → EC2 Instance (devops-vpc-server)
           Private: 10.0.1.240
           Public:  3.88.16.208

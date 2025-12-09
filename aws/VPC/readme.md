VPC – Virtual Private Cloud (Simple Notes)
✅ 1. What is VPC?

<img width="800" height="636" alt="image" src="https://github.com/user-attachments/assets/631ed271-c8c2-4584-9706-ec6db83df7ad" />

VPC = your own private network in AWS.
It lets you create:

subnets

route tables

internet access

private networks

security layers

In simple words:
VPC = your own mini-data center inside AWS.

<img width="975" height="596" alt="image" src="https://github.com/user-attachments/assets/f869a8db-90c3-4e93-87be-6c519795df3a" />

✅ 2. Default VPC vs Custom VPC
Default VPC

Comes automatically

Public subnets already created

Internet available by default

Custom VPC

Created by you

You define everything manually

Used in real projects

✅ 3. VPC Components
⭐ 1. CIDR Block

The IP range of your VPC
Example:

10.0.0.0/16


This gives you 65,536 IPs.

⭐ 2. Subnets

Subnets divide your VPC into smaller networks.

Public Subnet → Connected to Internet Gateway

Private Subnet → No direct public internet

Example:

Public: 10.0.1.0/24
Private: 10.0.2.0/24

⭐ 3. Internet Gateway (IGW)

Allows public subnet to talk to the internet.

In simple words:
IGW = door to the internet.

⭐ 4. NAT Gateway

Allows private subnet instances to access internet outbound only, but they cannot be accessed from internet.

In simple words:
NAT = one-way internet for private subnet.

⭐ 5. Route Tables

Decide where traffic should go.

Examples:

For public subnet → route to IGW

For private subnet → route to NAT

⭐ 6. Security Groups

Act as firewall for EC2

Allow traffic

Deny other traffic

Works only allow rules

⭐ 7. NACL (Network ACL)

Firewall at subnet level

Allows/Deny both rules

Stateless (need return rule)

⭐ 8. DHCP Option Sets

Give DNS server details to EC2.

⭐ 9. VPC Peering

Connects two VPCs

They can communicate privately

Cannot transit through a third VPC

⭐ 10. VPC Endpoints

Connect AWS services without internet.
Two types:

Interface endpoint

Gateway endpoint (for S3/DynamoDB)

✅ 4. Public vs Private Subnet (Super Simple)
Feature	Public Subnet	Private Subnet
Internet access	Yes (IGW)	Yes (via NAT only outbound)
Can be accessed from internet?	Yes	No
Example use	Web server	DB server
✅ 5. Important Ports

22 → SSH

80 → HTTP

443 → HTTPS

3306 → MySQL (only private subnet)

✅ 6. Simplest VPC Architecture

1 VPC
→ 1 Public Subnet
→ 1 Private Subnet
→ IGW
→ NAT Gateway
→ 2 Route Tables
→ 2 Security Groups

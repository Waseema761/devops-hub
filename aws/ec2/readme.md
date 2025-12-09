
1. What is EC2?

EC2 (Elastic Compute Cloud) = AWS virtual computer                                  
You can run websites, apps, scripts, servers.


Elastic = you can increase/decrease size anytime.

✅ 2. Why EC2 is used?

To host websites

To run backend servers

To run applications

For learning Linux/Windows

For launching VMs in cloud

For scalable computing

✅ 3. EC2 Components
a) AMI (Amazon Machine Image)

It is like a template → decides OS (Linux/Windows), software, configuration.

b) Instance Type

Defines hardware power:

vCPU

RAM

Storage type

Network performance
Examples: t2.micro, t3.medium, m5.large, c5.xlarge.

c) Key Pair

A login password for Linux using SSH (.pem file).

d) Security Group

Acts like a firewall → allows/blocks traffic.
Example:

Port 22 → SSH

Port 80 → HTTP

Port 443 → HTTPS

e) EBS Volume

Hard disk of the EC2 instance.

✅ 4. Types of EC2 Instances

(Use simple words)

1. General Purpose

For normal use
(t2, t3, m5 etc.)

2. Compute Optimized

For CPU-heavy tasks
(c5, c6g)

3. Memory Optimized

For RAM-heavy apps
(r5, x1)

4. Storage Optimized

For high read/write
(i3, d2)

5. GPU Instances

For AI, ML, video rendering
(p2, g4)

✅ 5. Pricing Options
1. On-Demand

Pay per hour/second
(Most flexible)

2. Reserved Instances

1 or 3-year commitment
(Cheap but fixed)

3. Spot Instances

Super cheap (up to 90%)
But AWS can take it anytime.

4. Dedicated Host

Physical server only for you.

✅ 6. EC2 Lifecycle States

Pending → starting

Running → active

Stopping → shutting down

Stopped → halted (you pay only for EBS)

Terminated → deleted

✅ 7. Elastic IP

A permanent public IP
Even if you stop EC2, IP remains same.

✅ 8. EBS Types
1. gp2 / gp3

General purpose SSD
Best for daily use

2. io1 / io2

High IOPS SSD
For databases

3. st1

HDD for big data

4. sc1

HDD for cold data

✅ 9. EC2 Security

Use Security Groups

Do not open port 22 to everyone

Use Key Pairs to login

Enable IAM Role instead of storing access keys

Use VPC for network isolation

✅ 10. EC2 Monitoring

(Using CloudWatch)

CPU

Disk

Network

Status Checks

System Status Check

Instance Status Check

✅ 11. EC2 Load Balancing

If traffic increases → use ELB
Types:

Application LB

Network LB

Gateway LB

✅ 12. Auto Scaling

Automatically:

Increases EC2 when traffic high

Decreases EC2 when traffic low

Helps in cost saving.

✅ 13. EC2 Placement Groups

Used for network performance

Cluster → high speed inside same rack

Spread → separate racks

Partition → big data (HDFS)

✅ 14. How to Connect EC2
Linux
ssh -i mykey.pem ec2-user@public-ip

Windows

Use RDP + password.

✅ 15. Common Interview Questions

What is EC2?

Difference between AMI and Snapshot?

What is Security Group vs NACL?

What is Elastic IP?

When to use Spot Instances?

What is Auto Scaling?

What happens when EC2 stops?

What is user-data?

What are status checks?

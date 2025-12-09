CloudWatch & CloudTrail – Simple Notes (README.md)
#️⃣ CloudWatch (Monitoring Service)

<img width="604" height="385" alt="image" src="https://github.com/user-attachments/assets/45c58961-bf2d-4544-a809-35b7763f2979" />

✅ 1. What is CloudWatch?

CloudWatch is AWS’s monitoring service.
It helps you watch your AWS resources.

In simple words:
CloudWatch = CCTV camera for AWS services.

✅ 2. What CloudWatch Monitors

CPU usage

Memory (with agent)

Disk usage

Network traffic

Application logs

Status checks (EC2 health)

✅ 3. CloudWatch Alarms

Used to send alerts when something goes wrong.

Examples:

CPU > 80% → send alert

Disk 90% full → send alert

EC2 stopped → send alert

CloudWatch can send alerts to:

Email

SNS

Auto-scaling

Lambda

✅ 4. CloudWatch Logs

Stores logs from:

EC2

Lambda

VPC Flow Logs

CloudTrail logs

Custom apps

You can search logs, filter logs, and monitor them.

✅ 5. CloudWatch Metrics

Metrics = numbers generated every few seconds/minutes.
Example:

CPUUtilization

NetworkIn

DiskReadBytes

✅ 6. CloudWatch Dashboards

You can create your own monitoring dashboard with graphs.

Useful for:

DevOps

SRE

Real-time performance view

#️⃣ CloudTrail (Audit & Logging Service)

<img width="1024" height="508" alt="image" src="https://github.com/user-attachments/assets/6ef766fc-f746-40fc-b835-74a31c71fd6b" />

✅ 1. What is CloudTrail?

CloudTrail is used to track all actions done in AWS.

In simple words:
CloudTrail = CCTV camera for “who did what” in AWS.

✅ 2. What CloudTrail Records?

CloudTrail logs:

Who logged in

Who created/deleted EC2

Who changed S3 bucket policy

Who modified IAM

API calls (CLI, console, SDK)

Root user actions

Basically every activity is recorded.

✅ 3. CloudTrail Log Storage

CloudTrail saves logs to:

S3 bucket

CloudWatch Logs (optional)

✅ 4. CloudTrail Types
1. Management Events

Control plane
Examples:

Create VPC

Delete S3 bucket

Update IAM role

2. Data Events

Data plane
Examples:

GetObject from S3

PutObject

Lambda Invoke event

(Data events cost extra)

✅ 5. CloudTrail Insights

Detects unusual activity like:

sudden increase in API calls

strange IAM behavior

abnormal login attempts

✅ 6. Why CloudTrail Is Important?

Security

Auditing

Compliance

Investigating issues

Checking unauthorized access

Very useful for DevOps, Cloud Engineers, and Security teams.

🔥 CloudWatch vs CloudTrail (Very Simple Comparison)
Feature	CloudWatch	CloudTrail
Purpose	Monitoring	Auditing
Tracks	Performance	User/API activity
Data	Metrics & Logs	API calls & user actions
Alerts	Yes (Alarms)	No (but can send logs)
Stores	Metrics, logs	S3 (mainly)
Example	CPU > 80%	“Who deleted EC2?”

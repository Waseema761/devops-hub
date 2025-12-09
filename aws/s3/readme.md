1. What is S3?

S3 = Simple Storage Service
It is a storage service used to store:

files

images

videos

backups

logs

website content

S3 is used like a big online hard disk.

<img width="1431" height="754" alt="image" src="https://github.com/user-attachments/assets/91dc83a6-64cd-47fe-a982-0fb917d31393" />


 2. What is a Bucket?

A bucket = folder in AWS S3
You store your files inside a bucket.

Important:
Bucket name must be unique globally (no one else in world can have the same name).

Example bucket names:

myaws-bucket-123

waseem-devops-bucket

 3. What is an Object?

Anything you upload in S3 is an object:

file

video

image

pdf

zip

Object = data + metadata (file size, type, etc.)

4.) S3 Storage Classes

<img width="5000" height="2266" alt="image" src="https://github.com/user-attachments/assets/928dc60c-dd9f-43f4-9cc7-0ccdc7c59a4c" />

Different storage types based on cost & usage.

⭐ 1. S3 Standard

Default

Frequent access

Fastest

Most expensive (but normal cost)

⭐ 2. S3 Intelligent Tiering

Automatically moves files to cheap storage

Best for unknown access patterns

⭐ 3. S3 Standard-IA (Infrequent Access)

Cheaper

For files that you don’t open often

Retrieval fee applies

⭐ 4. S3 One Zone-IA

Stored in one AZ only

Cheaper but not highly durable

⭐ 5. S3 Glacier

Very cheap

For backups

Retrieval takes minutes to hours

⭐ 6. S3 Glacier Deep Archive

Cheapest

Retrieval takes 12 hours

For long-term storage (7–10 years)

✅ 5. S3 Features
1. Versioning

Keeps old versions of files.
Protects against accidental delete.

2. Encryption

Makes data secure.

SSE-S3 (AWS manages key)

SSE-KMS (customer key)

SSE-C (you provide key)

3. Bucket Policy

Controls what users/public can do.
Written in JSON.

4. ACL (Access Control List)

Old method — not recommended now.

5. Static Website Hosting

You can host a complete website using S3.
(Common for HTML websites)

6. Lifecycle Rules

Move objects from one storage class to another automatically.

Example:

After 30 days → move to IA

After 90 days → move to Glacier

After 365 days → delete

7. CORS

Allows other websites to access S3 files.

✅ 6. S3 URL Types
1. Object URL
https://bucketname.s3.amazonaws.com/filename.jpg

2. Website URL (when static hosting enabled)
http://bucketname.s3-website-region.amazonaws.com

✅ 7. S3 Security

Use Bucket Policies

Block Public Access (default ON)

Use IAM roles to allow EC2/Lambda to access S3

Enable Versioning for protection

Enable MFA Delete for extra security

✅ 8. S3 Replication

Copies files automatically to another bucket.

1. CRR – Cross-Region Replication

Region → Another region (for disaster recovery)

2. SRR – Same-Region Replication

Same region → another bucket (for logs, backups)

Note: Versioning must be ON.

✅ 9. S3 Performance

Supports large files (upto 5 TB)

Multipart upload for files > 100 MB

High durability: 99.999999999% (11 9’s)

✅ 10. S3 Pricing Basics

S3 charges for:

Storage

Requests (PUT/GET)

Data transfer

Replication

Management features (like Inventory)

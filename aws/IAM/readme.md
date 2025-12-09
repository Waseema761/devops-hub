IAM – Identity and Access Management (Simple Notes)
✅ 1. What is IAM?

IAM (Identity and Access Management) is the security service in AWS.
It controls who can access what.

In simple words: IAM is the security guard of AWS.

<img width="800" height="709" alt="image" src="https://github.com/user-attachments/assets/c0b49acd-7e15-40d4-9625-eda8741d4bc4" />


✅ 2. Why IAM is Used?

To create users

To give permissions

To protect AWS resources

To control access properly

To follow “least privilege” (give only required access)

✅ 3. IAM Components
1. IAM Users

A user = one person
Has:

username

password (for console login)

access keys (for CLI/SDK)

2. IAM Groups

Group = collection of users
Example groups:

Admins

Developers

Billing

You attach policies to groups, and users inherit them.

3. IAM Roles

Role = temporary access for:

EC2

Lambda

S3 jobs

Other AWS accounts

Any AWS service

Roles do not belong to people.

4. IAM Policies

Policy = permissions written in JSON.

Example:

{
  "Effect": "Allow",
  "Action": "s3:ListBucket",
  "Resource": "*"
}


A policy contains:

Effect (Allow/Deny)

Action

Resource

✅ 4. Types of Policies
AWS Managed Policies

Created by AWS
Examples:

AmazonS3FullAccess

AdministratorAccess

Customer Managed Policies

Created by you
Reusable and recommended.

Inline Policies

Attached to only one user/role
Not reusable.

✅ 5. Password Policy

You can set rules like:

Minimum length

Require uppercase/lowercase

Symbols

Password expiration

Prevent reuse

✅ 6. MFA (Multi-Factor Authentication)

Adds extra security.
User needs:

Password

OTP (authenticator app)

Important for:

Root user

Admin users

✅ 7. Best Practices

Don’t use root account for daily work

Enable MFA for root and admins

Use groups instead of giving policies directly to users

Use roles instead of access keys

Rotate access keys regularly

Follow least privilege

Turn on CloudTrail for auditing

✅ 8. Access Keys

Used for CLI, SDK, Terraform.

Consist of:

Access Key ID

Secret Access Key

Never upload keys to GitHub.

✅ 9. Permission Evaluation Logic

AWS decides access using this rule:

Explicit Deny (highest priority)

Allow

If no Allow = Implicit Deny (default)

✅ 10. IAM vs Identity Center (SSO) (Short)

Identity Center = Modern login system for organizations.
Used for:

Single Sign-On

Central user management

Access to multiple AWS accounts

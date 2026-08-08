

````md
# Amazon S3 - Basics

## 1. Introduction

Amazon S3 (Simple Storage Service) is an object storage service provided by AWS.

It is used to store and manage data such as images, videos, documents, backups, application files, logs, and static website files.

---

## 2. Why S3 is Used

S3 is used when an application needs reliable and scalable storage without maintaining physical storage infrastructure.

Common use cases:

- Application file storage
- Backup and recovery
- Static website hosting
- Image and video storage
- Log storage
- Data lake storage
- Software and file distribution

---

## 3. Basic S3 Architecture

```text
User / Application
        |
        v
    S3 Bucket
        |
        v
      Object
````

A **bucket** is the container.

An **object** is the actual file stored inside the bucket.

Example:

```text
Bucket
|
+-- index.html
+-- images/
|   +-- logo.png
|   +-- banner.jpg
|
+-- documents/
    +-- resume.pdf
```

---

## 4. Bucket

A bucket is a container used to store objects in Amazon S3.

Important points:

* Bucket names must be globally unique.
* A bucket is created in an AWS Region.
* A bucket can contain a very large number of objects.
* Bucket-level configurations control security and data management.
* Versioning, lifecycle rules, encryption, and access policies can be configured for a bucket.

Example:

```text
my-company-application-bucket
```

---

## 5. Object

An object is the actual data stored inside an S3 bucket.

Examples:

```text
index.html
logo.png
resume.pdf
backup.zip
video.mp4
```

An object contains:

* Object data
* Object key
* Metadata
* Version ID when versioning is enabled

---

## 6. Object Key

The object key identifies an object inside a bucket.

Example:

```text
images/aws-logo.png
```

Here:

```text
Bucket     : my-company-application-bucket
Object Key : images/aws-logo.png
```

S3 does not use traditional folders like a normal operating system.

The `images/` part is a prefix used to organize objects.

---

# 7. S3 Practical Implementation

## Step 1 - Open Amazon S3

1. Sign in to the AWS Management Console.
2. Search for `S3`.
3. Open **Amazon S3**.
4. Make sure the required AWS Region is selected.

### Expected Result

The S3 dashboard should be displayed.

---

## Step 2 - Create a Bucket

1. Click **Create bucket**.
2. Enter a globally unique bucket name.

Example:

```text
my-s3-learning-bucket-2026
```

3. Select the required AWS Region.
4. Review the Object Ownership settings.
5. Keep **Block Public Access** enabled for a normal private bucket.
6. Review the remaining settings.
7. Click **Create bucket**.

### Expected Result

The bucket should appear in the S3 bucket list.

---

## Step 3 - Open the Bucket

1. Click the newly created bucket.
2. Open the **Objects** tab.
3. The bucket should initially be empty.

---

## Step 4 - Upload an Object

1. Click **Upload**.
2. Click **Add files**.
3. Select a file from the local computer.
4. Review the selected file.
5. Click **Upload**.

Example file:

```text
index.html
```

### Expected Result

The uploaded object should appear inside the bucket.

---

## Step 5 - Verify the Object

Click the uploaded object.

Check:

* Object name
* Object key
* Object size
* Last modified time
* Storage class
* Encryption
* Object URL

This confirms that the object has been successfully stored in S3.

---

# 8. S3 Storage Classes

S3 provides different storage classes based on access patterns.

## S3 Standard

Used for frequently accessed data.

Examples:

* Website files
* Application assets
* Frequently accessed documents

## S3 Intelligent-Tiering

Automatically moves objects between access tiers based on changing access patterns.

Useful when access patterns are unpredictable.

## S3 Standard-IA

Used for data that is accessed less frequently but still requires quick retrieval.

## S3 One Zone-IA

Used for infrequently accessed data that can be recreated if required and does not need multi-AZ storage.

## S3 Glacier Classes

Used mainly for archival and long-term storage.

```text
Frequently Accessed
        |
        v
S3 Standard
        |
        v
S3 Standard-IA
        |
        v
S3 Glacier
        |
        v
Long-Term Archive
```

The correct storage class should be selected based on access frequency, retrieval requirements, and cost.

---

# 9. S3 Versioning - Practical

Versioning allows multiple versions of an object to be maintained.

## Enable Versioning

1. Open the S3 bucket.
2. Go to **Properties**.
3. Find **Bucket Versioning**.
4. Click **Edit**.
5. Select **Enable**.
6. Save the changes.

## Test Versioning

1. Upload an object.
2. Modify the same file.
3. Upload it again using the same object name.
4. Open the object.
5. Check the available versions.

### Result

S3 can maintain multiple versions of the same object.

This helps protect against accidental overwrites and deletions.

---

# 10. S3 Lifecycle Rule - Practical

Lifecycle rules automate object management.

Example:

```text
S3 Standard
      |
      v
S3 Standard-IA
      |
      v
S3 Glacier
      |
      v
Expiration
```

## Create a Lifecycle Rule

1. Open the S3 bucket.
2. Go to **Management**.
3. Click **Create lifecycle rule**.
4. Enter a rule name.
5. Select the required scope.
6. Configure the required transition actions.
7. Configure expiration if required.
8. Review the configuration.
9. Create the rule.

Lifecycle rules can reduce storage costs and automatically manage older data.

---

# 11. S3 Security

Important S3 security mechanisms include:

* IAM policies
* Bucket policies
* Block Public Access
* Object Ownership
* Encryption

For a private bucket, access should be granted only to the required users, roles, or AWS services.

---

# 12. S3 Encryption

S3 supports encryption for data at rest.

Common server-side encryption options include:

* SSE-S3
* SSE-KMS
* SSE-C

Encryption helps protect stored data from unauthorized access.

---

# 13. S3 CLI Commands

S3 can also be managed using AWS CLI.

## List Buckets

```bash
aws s3 ls
```

## List Objects

```bash
aws s3 ls s3://my-bucket
```

## Upload a File

```bash
aws s3 cp file.txt s3://my-bucket/
```

## Download a File

```bash
aws s3 cp s3://my-bucket/file.txt .
```

## Delete an Object

```bash
aws s3 rm s3://my-bucket/file.txt
```

## List Objects Recursively

```bash
aws s3 ls s3://my-bucket --recursive
```

---

# 14. Verification

After completing the practical, verify:

* Bucket was created successfully.
* Correct Region is selected.
* Object was uploaded successfully.
* Object can be viewed from the bucket.
* Object can be downloaded.
* Versioning works if enabled.
* Lifecycle rule is configured correctly.
* Required permissions are available.
* Encryption is enabled as required.

---

# 15. Troubleshooting

## Bucket Name Already Exists

S3 bucket names are globally unique.

Use another name.

Example:

```text
my-s3-learning-bucket-2026-001
```

## Access Denied

Check:

* IAM permissions
* Bucket policy
* Object ownership
* Block Public Access
* AWS account
* AWS Region

## Object Not Visible

Check:

* Correct bucket
* Correct Region
* Correct prefix
* Upload status
* IAM permissions

## CLI Access Denied

Check the AWS identity:

```bash
aws sts get-caller-identity
```

Then verify that the identity has the required S3 permissions.

---

# 16. Screenshots

Screenshots should be stored inside the repository `images` folder.

Recommended screenshots:

```text
images/
|
+-- s3-dashboard.png
+-- s3-create-bucket.png
+-- s3-bucket-created.png
+-- s3-object-upload.png
+-- s3-object-details.png
+-- s3-versioning.png
+-- s3-lifecycle.png
+-- s3-cli.png
```

Add screenshots using Markdown:

```md
![S3 Bucket Creation](./images/s3-create-bucket.png)
```

---

# 17. Important S3 Terms

| Term          | Meaning                                     |
| ------------- | ------------------------------------------- |
| Bucket        | Container for storing objects               |
| Object        | Actual data stored in S3                    |
| Object Key    | Identifier of an object                     |
| Region        | AWS location where the bucket is created    |
| Storage Class | Storage option based on access pattern      |
| Versioning    | Maintains multiple object versions          |
| Lifecycle     | Automates object transitions and expiration |
| Bucket Policy | Resource-based access policy                |
| IAM Policy    | Identity-based access policy                |
| Encryption    | Protects stored data                        |
| Replication   | Copies objects between buckets              |

---

# 18. Key Takeaways

* S3 is an object storage service.
* Data is stored as objects inside buckets.
* Bucket names must be globally unique.
* Objects are identified using object keys.
* Buckets are created in AWS Regions.
* Different storage classes are available for different access patterns.
* Versioning helps recover previous object versions.
* Lifecycle rules automate object management.
* IAM and bucket policies control access.
* Encryption protects data at rest.
* S3 can be managed through the AWS Console and AWS CLI.

---

# Conclusion

Amazon S3 is a fundamental AWS service for storing and managing data in the cloud.

Through this practical, the complete basic S3 workflow can be understood:

```text
Create Bucket
      |
      v
Configure Bucket
      |
      v
Upload Object
      |
      v
Verify Object
      |
      v
Manage Object
      |
      v
Configure Security
      |
      v
Enable Versioning
      |
      v
Configure Lifecycle
```


<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/22d8a591-b68e-41ee-b0b4-7bded5cda670" />

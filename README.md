# Amazon S3 – Hands-on Learning & Practical Implementation

Amazon S3 (Simple Storage Service) is an object storage service provided by AWS. It is used to store and retrieve data such as images, videos, documents, application files, backups, logs, and static website files.

This repository contains my hands-on learning and practical implementation of Amazon S3 concepts. I have documented the concepts, configurations, practical steps, and important points while learning S3.

---

## What is Amazon S3?

Amazon S3 is a highly scalable object storage service that allows data to be stored as objects inside buckets.

A simple way to understand S3:

User → S3 Bucket → Object

For example:

Bucket:
`my-project-files`

Objects:
- `index.html`
- `logo.png`
- `resume.pdf`
- `backup.zip`

---

## Key Concepts

### Bucket

A bucket is a container used to store objects in Amazon S3.

Important points:

- Bucket names must be globally unique.
- A bucket is created in a specific AWS Region.
- Objects are stored inside buckets.
- Bucket-level settings can control access, versioning, lifecycle rules, and other configurations.

### Object

An object is the actual data stored inside an S3 bucket.

An object consists of:

- Object data
- Object key
- Metadata

Example:

`images/profile.png`

Here, `images/profile.png` is the object key.

### Region

S3 buckets are created in an AWS Region.

Choosing an appropriate Region can help reduce latency and meet data residency requirements.

---

## Amazon S3 Features

- Object storage
- High scalability
- High durability
- Storage classes
- Versioning
- Lifecycle management
- Encryption
- Access control
- Static website hosting
- Object Lock
- Replication
- Event notifications
- Logging and monitoring

---

## S3 Storage Classes

Amazon S3 provides different storage classes based on access frequency and cost requirements.

| Storage Class | Typical Use |
|---|---|
| S3 Standard | Frequently accessed data |
| S3 Intelligent-Tiering | Data with changing access patterns |
| S3 Standard-IA | Infrequently accessed data |
| S3 One Zone-IA | Infrequently accessed, re-creatable data |
| S3 Glacier Instant Retrieval | Archive data requiring fast retrieval |
| S3 Glacier Flexible Retrieval | Long-term archival |
| S3 Glacier Deep Archive | Lowest-cost long-term archival |

Choosing the correct storage class helps optimize storage cost.

---

## S3 Versioning

Versioning keeps multiple versions of an object in the same bucket.

For example:

`index.html` → Version 1  
`index.html` → Version 2  
`index.html` → Version 3

If an object is accidentally overwritten or deleted, previous versions can be used for recovery.

---

## S3 Lifecycle Management

Lifecycle rules automatically manage objects based on their age or other conditions.

Example:

```text
S3 Standard
      ↓
S3 Standard-IA
      ↓
S3 Glacier
      ↓
S3 Glacier Deep Archive

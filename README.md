# LAB2

## Cloud Basics: Interacting with AWS," here’s an example structure. You can customize the content as per your specific needs.

```markdown
# Cloud Basics: Interacting with AWS

## Introduction
Cloud computing has revolutionized the way developers build and manage applications. Amazon Web Services (AWS) provides a variety of services that make it easy to interact with the cloud and manage resources efficiently. In this article, we will cover some essential AWS concepts and demonstrate how to interact with AWS services programmatically.

---

## Prerequisites

Before starting, ensure you have the following:

- An AWS account
- AWS CLI installed
- Basic knowledge of the command line and cloud computing

### Install AWS CLI
The AWS Command Line Interface (CLI) is a unified tool to manage AWS services. Follow the steps below to install it:

```bash
# macOS
brew install awscli

# Linux
sudo apt-get install awscli

# Windows
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

Once installed, verify it by running:

```bash
aws --version
```

### Configuring AWS CLI
Configure your AWS CLI by running:

```bash
aws configure
```

Provide your AWS Access Key, Secret Key, Region, and Output Format.

---

## Interacting with AWS S3

Amazon S3 (Simple Storage Service) is an object storage service that offers scalability, data availability, and security. Let’s start by creating a bucket and uploading a file.

### Create an S3 Bucket

```bash
aws s3 mb s3://my-new-bucket
```

### Upload a File to S3

```bash
aws s3 cp myfile.txt s3://my-new-bucket/
```

### List S3 Buckets

```bash
aws s3 ls
```

### Download a File from S3

```bash
aws s3 cp s3://my-new-bucket/myfile.txt ./myfile.txt
```

---

## Interacting with EC2

Amazon EC2 (Elastic Compute Cloud) allows users to rent virtual machines to run applications in the cloud.

### Launch an EC2 Instance

```bash
aws ec2 run-instances \
    --image-id ami-0123456789abcdef0 \
    --instance-type t2.micro \
    --key-name MyKeyPair
```

### List Running EC2 Instances

```bash
aws ec2 describe-instances
```

### Stop an EC2 Instance

```bash
aws ec2 stop-instances --instance-ids i-0123456789abcdef0
```

### Terminate an EC2 Instance

```bash
aws ec2 terminate-instances --instance-ids i-0123456789abcdef0
```

---

## IAM Roles and Permissions

AWS Identity and Access Management (IAM) helps you securely control access to AWS services. To interact with AWS effectively, you should set up appropriate IAM roles and permissions.

### Creating an IAM User

```bash
aws iam create-user --user-name NewUser
```

### Attaching a Policy to an IAM User

```bash
aws iam attach-user-policy --user-name NewUser \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
```

---

## Conclusion

By following the steps outlined above, you can effectively interact with various AWS services using the AWS CLI. This guide covered basic operations in S3, EC2, and IAM services, but AWS offers much more functionality that you can explore.
```

You can structure the markdown as shown here, including headings, sections, and code snippets in a simple and clear format. Feel free to add more specific content based on the services or interactions you want to focus on.

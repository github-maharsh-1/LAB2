# LAB2


# Cloud Basics: Interacting with AWS

## Tutorial on creating cloud resources using various interfaces

Photo by [Engin Akyurt](https://unsplash.com/@enginakyurt?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

There are programmatic and GUI/web-based ways of interacting with cloud providers to create and manage resources in the cloud. In this lab tutorial, we will be interacting with Amazon Web Services (AWS) APIs to create AWS EC2 instances (virtualized server) and S3 (cloud storage) using the following four methods:

1. AWS Management Console (browser)
2. AWS CLI (command-line interface)
3. IDE (interactive development environment)
4. AWS CloudFormation

Making changes via Console is fine for experimentation but not preferred beyond that. It also doesn’t support automation and version control. Infrastructure as Code (IaC) solutions such as CloudFormation should be used for anything beyond experimentation.

### Comparing Cloud API Interaction Methods

| **Method** | **Description** |
|------------|-----------------|
| Console    | Web interface for managing AWS |
| CLI        | Command-line interface for automating AWS tasks |
| IDE        | Integrated development environment with AWS support |
| CloudFormation | IaC service for automating AWS resource creation |

## Prerequisites

### AWS Setup

1. Setup a Free Tier AWS account ([link](https://aws.amazon.com/free/)).
2. Sign into your AWS Console using root user and create an IAM user. Follow the steps under “Creating IAM users (console)” in [this link](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html).
3. Create Keypair for EC2. Ensure you are in the `us-east-1` (Northern Virginia) region in AWS Console. Follow instructions under "Create a key pair using Amazon EC2" ([link](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-key-pairs.html)).
4. Install AWS CLI ([link](https://aws.amazon.com/cli/)) and configure it using the `aws configure` command:

    ```bash
    $ aws configure
    AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
    AWS Secret Access Key [None]: wJalrXUtnFEMMPLEKEY
    Default region name [None]: us-east-1
    Default output format [None]: json
    ```

5. This will be stored in the `~/.aws/credentials` file as:

    ```ini
    [default]
    aws_access_key_id = AKIAIOSFODNN7EXAMPLE
    aws_secret_access_key = wJalrXUtnFEMMPLEKEY
    region = us-east-1
    format = json
    ```

6. Test your AWS CLI credentials:

    ```bash
    $ aws sts get-caller-identity
    ```

### GitHub Account Setup & Install

1. Create a free GitHub account ([link](http://github.com/signup)).
2. Download and install Git ([here](https://git-scm.com/downloads)).
3. Configure Git with your username and email:

    ```bash
    $ git config --global user.name "Your name here"
    $ git config --global user.email "your_email@example.com"
    ```

4. Generate an SSH key on your computer:

    ```bash
    $ ssh-keygen -t rsa -C "your_email@example.com"
    ```

5. Add your SSH public key to your GitHub account ([link](https://github.com/settings/ssh)).

6. Test the connection to GitHub:

    ```bash
    $ ssh -T git@github.com
    ```

## AWS Management Console

1. Go to [AWS Console](https://aws.amazon.com/console/).
2. Ensure you are in `us-east-1` (Northern Virginia) region.
3. Launch a Windows EC2 instance using the steps in [AWS EC2 guide](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/EC2_GetStarted.html).
4. Connect to your instance using RDP and terminate the instance to avoid charges.

![Screenshot of EC2 instance](https://miro.medium.com/v2/resize:fit:875/1*Fn4ZssUzywvKbdDpJf6Jtw.png)

## AWS CLI

Launch an EC2 instance using the CLI:

```bash
$ aws ec2 run-instances --image-id ami-08e4e35cccc6189f4 --count 1 --instance-type t2.micro --key-name <Key-Pair-Name> --security-groups default
```

Make sure to terminate the instance to avoid charges.

![Screenshot of CLI output](https://miro.medium.com/v2/resize:fit:875/1*IGe8KLlPPw833d10owFeUA.png)

## Interactive Development Environment (IDE)

1. Open Visual Studio Code.
2. Open AWS Explorer and create an S3 bucket.
3. Verify the bucket creation in the AWS Console.

![Screenshot of S3 creation in VS Code](https://miro.medium.com/v2/resize:fit:875/1*Y7TzbTcoANQNqcBHR_NRew.png)

## AWS CloudFormation

Launch EC2 from a CloudFormation template:

1. Clone the repository from [GitHub](https://github.com/shrestha-ajay/cloud-basics1.git):

    ```bash
    $ git clone git@github.com:YOUR-USERNAME/YOUR-REPOSITORY.git
    $ cd YOUR-REPOSITORY-Folder
    ```

2. Deploy CloudFormation:

    ```bash
    $ aws cloudformation deploy \
      --stack-name my-cloudbasic-ec2 \
      --template-file ec2_securitygroup.template \
      --parameter-overrides KeyName=General-key-1
    ```

Replace `General-key-1` with your EC2 KeyPair name.

![Screenshot of CloudFormation Stack](https://miro.medium.com/v2/resize:fit:875/1*Nucx__KfKj8-2d0b1WayLg.png)

## Summary

In this lab, we interacted with AWS to create EC2 and S3 resources using four methods: Console, CLI, IDE, and CloudFormation.

## Clean Up

Be sure to terminate resources to avoid any charges.

## Resources

1. [AWS Free Tier](https://aws.amazon.com/free)
2. [Creating IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)
3. [EC2 Key Pairs](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-key-pairs.html)
4. [AWS CLI](https://aws.amazon.com/cli/)
5. [GitHub](http://github.com/signup)
6. [Visual Studio Code](https://code.visualstudio.com/)
7. [AWS Toolkit for VS Code](https://aws.amazon.com/visualstudiocode/)
```

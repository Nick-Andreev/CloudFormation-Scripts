### Description

This is a CloudFormation template to deploy Cloud Protection Manager (CPM) backup solution in a customer VPC. CPM instance can be deployed directly through AWS Marketplace, but will require further manual configuration.

Provided CloudFormation template in addition to deploying a CPM instance will also create a security group, elastic IP and IAM role for CPM.

Template deploys the following resources:

* CPM instance with Elastic IP address.
* Blank security group for CPM. Add inbound HTTPS access rules for management access after deployment.
* IAM role that includes permissions to backup and restore EC2 instances and RDS, as well as send notification via SNS.

### Prerequisites

* Download and install Python. Guide for Windows can be found here: https://niktips.wordpress.com/2017/09/07/python-for-windows-quick-installation/
* Download and install AWS CLI. Guide for Windows can be found here: https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-windows.html
* Configure AWS CLI by running "aws configure". Configuration guide can be found here: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

### Usage Examples

Before you can deploy CPM using CloudFormation you need to subscribe to CPM software in AWS Marketplace https://aws.amazon.com/marketplace. Find CPM version (Standard/Advanced/Enterprise) that you need in Marketplace and click Continue to Subscribe. Then on Service Catalog tab click Accept Software Terms.

Don't deploy CPM through Marketplace, but note the AMI ID for your region from the Manual Launch tab. AMI ID is one of the parameters required for CloudFormation template.

To deploy the template, use the following command and replace parameter values according to your environment:

```
> aws cloudformation deploy --stack-name cpm-stack --template-file cpm-deploy-v1.0.yaml --capabilities CAPABILITY_IAM --parameter-overrides "VPC=vpc-aa11bb22" "KeyPair=Your-Key-Pair" "CPMInstanceName=CPM01" "CPMAMIID=ami-11223344" "CPMSubnetId=subnet-cc33dd44"
```

You can check if CloudFormation template deployed successfully in CloudFormation section of AWS Management Console.

### Environment Configuration

* AWS CLI 1.14.19
* Python 2.7.10
* Darwin 16.7.0

### Author

Nick Andreev:

* https://niktips.wordpress.com
* @nick_andreev_au
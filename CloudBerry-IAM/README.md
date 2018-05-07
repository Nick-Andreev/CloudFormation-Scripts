### Description

When using CloudBerry backup, you can use Amazon S3 and Glacier as backup storage destination. CloudBerry supports two types of authentication when adding S3 and Glacier accounts - access/secret keys or IAM role.

This CloudFormation template will create an IAM role for CloudBerry with access to S3 and Glacier. In addition to that, it will create an S3 bucket for backups and lock down S3 access only to that bucket for increased security.

Creating Glacier Vaults is not supported from CloudFormation, but CloudBerry will do that for you from the GUI.

### Prerequisites

* Download and install Python. Guide for Windows can be found here: https://niktips.wordpress.com/2017/09/07/python-for-windows-quick-installation/
* Download and install AWS CLI. Guide for Windows can be found here: https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-windows.html
* Configure AWS CLI by running "aws configure". Configuration guide can be found here: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

### Usage Examples

To deploy the template, use the following command and supply a name for CloudBerry S3 bucket:

```
> aws cloudformation deploy --stack-name cloudberry-stack --template-file cloudberry-iam-v1.0.yaml --capabilities CAPABILITY_IAM --parameter-overrides "CloudBerryBucketName=your-cloudberry-bucket"
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
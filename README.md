# AWS Cloudformation for Photo-uploader

This repository contains a cloud formation infrastructure template for photo managing app which is running on top of AWS.


## Prerequisites

* AWS account
* IAM user with admin or necessary access
* EC2 key pair
* AWS CLI (Optional)

## Infrastructure deployment

Infrastructure deployment can be done through either command line ( AWS cli ) or web UI (AWS console)

For command line deployment you need to have aws-cli installed on your deployment machine. In this template there are few parameters to update when you create a stack.

- Availability zone for Subnet
- Network CIDR for VPC
- Subnet CIDR for subnet
- S3 Bucket name
- Base AMI/ image id
- EC2 instance type
- KeyPair for EC2 ssh access


```sh
$ aws cloudformation create-stack --stack-name photo-app-stack --template-body file:///home/user/photo-app.yaml --parameters  ParameterKey=NetworkCIDR,ParameterValue=10.0.0.0/16 ParameterKey=AvailabilityZoneName,ParameterValue=ap-south-1a ParameterKey=SubnetCIDR,ParameterValue=10.0.1.0/24 ParameterKey=KeyPairName,ParameterValue=MySshKey ParameterKey=InstanceType,ParameterValue=t2.micro ParameterKey=InstanceImageId,ParameterValue=ami-0e4bc04bd401729d6 ParameterKey=BucketName,ParameterValue=myphotos3bucket
```
If you are deploying the stack via AWS console please follow the below steps 

- Login to AWS console  
- Got to cloudformation and select create stack
- Under Prepare template  select “Template is ready” and “Upload a template file”
- Once you upload the template file ( either JSON or YAML formatted file ) it will promet the S3 url for stack design 
- From design dashboard you can do any modification and validate the template 
- Select “Next” and you will prompt to enter stack details. Such as stack name, parameters
- Please give the stack name, necessary parameters (As mentioned above) and Tags
- Then you will prompt review to stack settings. 
- If all good you can initiate the stack creation
- Stack creation status can be view form “Events” and AWS resources will list under “Resources”

more details : https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html


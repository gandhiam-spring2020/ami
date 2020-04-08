# ami
Amazon Machine Image is used to develop customized EC2 instances.
The project aims at developing an AMI template by installing all the necessary softwares needed for hosting the application on EC2 instance.

## Getting Started

1. The circleci build will get triggered on merge which will use packer to create AMI on AWS
2. Use this AMI to create EC2 instance and configure the security group and open port 8080 for TCP and port 80 for HTTP.

### Prerequisites

Have used hashicorp/packer:1.1.1 image for installing packer on circleci

## Packer instructions:

    packer validate \
            -var "aws_region=${AWS_REGION}" \
            -var "aws_access_key=${AWS_ACCESS_KEY_ID}" \
            -var "aws_secret_key=${AWS_SECRET_ACCESS_KEY}" \
            -var "source_ami=${SOURCE_AMI}" \
            -var "ssh_username=${SSH_USERNAME}" \
            -var "ami_users=${AMI_USERS}" \
            ubuntu-ami.json

    packer build \
            -var "aws-region=${AWS_REGION}" \
            -var "aws-access_key=${AWS_ACCESS_KEY}" \
            -var "aws-secret_key=${AWS_SECRET_KEY}" \
            -var "ssh_username=${SSH_USERNAME}" \
            -var "subnet_id=${SUBNET_ID}" \
            -var "source_ami=${SOURCE_AMI}" \
            -var "ami_users=${AMI_USERS}" \
            ubuntu-ami.json

## Ubuntu-ami json template specifications:

1. Variables block to declare the environment variables
2. Builders block to build amazon-ebs volumes using environment variables
3. Power shell provisioners block with inline script to install application related resources and services
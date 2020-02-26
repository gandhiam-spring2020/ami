# ami
Amazon Machine Image is used to deevlop cusomised EC2 instances.
The project aims at developing an AMI template by installing all the necessary softwares needed for hosting the application on EC2 instance

## Getting Started

1. add a space in README file
2. Create a Pull request with master branch of organization
3. The cricleci build will get triggered on merge which will use packer to create AMI on AWS
4. Use this AMI to create EC2 instance and configure the security group and open port 8080 for TCP and port 80 for HTTP.


### Prerequisites

1. Have used hashicorp/packer:1.1.1 image for installing packer on circleci

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

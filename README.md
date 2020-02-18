# ami

## AWS-CLI Instructions:

### Install AWS-CLI:
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

### Configure AWS-CLI:
aws configure profile <profile-name>


## Packer Instructions:

### Install Packer:
sudo apt install packer

### Validate Packer Template:
packer validate ubuntu-ami.json 


## Build AMI:
packer build -var "var-name" ubuntu-ami.json
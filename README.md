# ami

## Packer Instructions:

### Install packer:
sudo apt install packer

### Validate AMI:
packer validate ubuntu-ami.json 

### Build AMI:
packer build -var "var-name" ubuntu-ami.json
# packer-demo

## packer-demo.json file will build an EBS image.
- It uses the source AMI, region and instance type to build the image.
- Since I didn't include subnet default VPC will be used.
- Then the script will move the app directory in to /tmp/app
- Finally run 'scripts/deploy.sh'.

## app directory
- index.js will render 'Hello World!'
- package.json runs nodejs packages


## deploy.sh
- Installs nginx
- group and and user add
- Move files to /app - permission to allow moving files
- Create the nginx configuration in etc/nginx/nginx.conf
- restart nginx
- Install npm inside /app
- Enable and start the node service
- EC2 Insatnce will be created

## jenkins-terraform.sh
- This script is to run within jenkins
- ARTIFACT will Packer build, Machine-readable packer-demo.JSON, and then extract the AMI
- Also removes some information we don't need so we have the AMI ID
- echo ami id
- upload ami_id to amivar.tf
- upload the amivar.tf to s3

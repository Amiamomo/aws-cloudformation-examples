https://www.youtube.com/watch?v=8J0g_xWUzV0

1) Create a new key pair - devenv-key

2) Update yml file

3) Create stack with cli (--profile demo not used here, need aws configure, check video)
aws cloudformation create-stack --stack-name test-stage --template-body file://D:\Dev\Python\doc\aws\CloudFormation\test1\stack.yml --region eu-west-2

aws cloudformation describe-stack-resources --stack-name test-stage

chmod 400 devenv-key.pem
ssh -i devenv-key.pem ec2-user@ec2-35-176-18-42.eu-west-2.compute.amazonaws.com

aws cloudformation delete-stack  --stack-name test-stage

______________________________________________________
EC2_web_php
aws cloudformation create-stack --stack-name EC2-web-php --template-body file://D:\Dev\Python\doc\aws\CloudFormation\test1\EC2_web_php.yml --region eu-west-2
aws cloudformation describe-stack-resources --stack-name EC2-web-php
aws cloudformation delete-stack  --stack-name EC2-web-php

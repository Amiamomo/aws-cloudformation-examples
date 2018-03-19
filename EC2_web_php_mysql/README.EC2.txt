EC2_web_php
aws cloudformation create-stack --stack-name EC2-web-php --template-body file://D:\Dev\Python\doc\aws\CloudFormation\test1\EC2_web_php.yml --region eu-west-2
aws cloudformation describe-stack-resources --stack-name EC2-web-php
aws cloudformation delete-stack  --stack-name EC2-web-php


Install log in /log_alex

https://docs.aws.amazon.com/fr_fr/AWSCloudFormation/latest/UserGuide/quickref-ec2.html

AMI has been changed t oami-403e2524, free tier eligible, check if install script still ok, 
Amazon Linux AMI 2017.09.1 (HVM), SSD Volume Type - ami-403e2524
The Amazon Linux AMI is an EBS-backed, AWS-supported image. The default image includes AWS command line tools, Python, Ruby, Perl, and Java. 
The repositories include Docker, PHP, MySQL, PostgreSQL, and other packages.
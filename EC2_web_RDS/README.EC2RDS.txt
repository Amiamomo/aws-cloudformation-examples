https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-rds-database-instance.html
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/CHAP_TemplateQuickRef.html
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.Scenarios.html  DB EC2 scenarios

EC2_web_php
aws cloudformation create-stack --stack-name EC2-web-RDS --template-body file://D:\Dev\Python\doc\aws\CloudFormation\EC2_web_RDS\EC2_web_RDS.yml --region eu-west-2
aws cloudformation describe-stack-resources --stack-name EC2-web-RDS
aws cloudformation delete-stack  --stack-name EC2-web-RDS


Install log in /log_alex

Test mysql access from EC2 : 
mysql -h ed1ski317lp965.ctjcyyx0vmkw.eu-west-2.rds.amazonaws.com -P 3306 -u alex_root -p

AMI has been changed to ami-403e2524, free tier eligible, check if install script still ok, 
Amazon Linux AMI 2017.09.1 (HVM), SSD Volume Type - ami-403e2524
The Amazon Linux AMI is an EBS-backed, AWS-supported image. The default image includes AWS command line tools, Python, Ruby, Perl, and Java. 
The repositories include Docker, PHP, MySQL, PostgreSQL, and other packages.

test: manual: i-006dc9cdea52fd735 
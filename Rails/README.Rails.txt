aws cloudformation create-stack --stack-name Rails-single --template-body file://D:\Dev\Python\doc\aws\CloudFormation\Rails\Rails_single.yml --region eu-west-2
aws cloudformation describe-stack-resources --stack-name Rails-single
aws cloudformation delete-stack  --stack-name Rails-single


Test mysql access from EC2 : 
mysql -h ed1ski317lp965.ctjcyyx0vmkw.eu-west-2.rds.amazonaws.com -P 3306 -u alex_root -p

ami-403e2524
ami-403e2524
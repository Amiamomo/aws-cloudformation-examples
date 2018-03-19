https://www.youtube.com/watch?v=8J0g_xWUzV0   
https://devteds.com/episodes/
https://github.com/devteds/e7-cloudformation-docker

Create CloudFormation Stack (EC2 + RDS) & Deploy Docker App - Episode #7
Great #7

https://github.com/pgarbe/containers_on_aws

# Create VPC in 3 availability zones
aws cloudformation create-stack \
  --stack-name vpc \
  --template-body https://s3-eu-west-1.amazonaws.com/widdix-aws-cf-templates/vpc/vpc-3azs.yaml

# Create bastion host for ssh access
aws cloudformation update-stack \
  --stack-name vpc-ssh-bastion \
  --template-body https://s3-eu-west-1.amazonaws.com/widdix-aws-cf-templates/vpc/vpc-ssh-bastion.yaml \
  --capabilities CAPABILITY_IAM \
  --parameters ParameterKey=ParentVPCStack,ParameterValue=vpc ParameterKey=KeyName,ParameterValue=pgarbe

# Create NAT gateway
aws cloudformation create-stack \
  --stack-name vpc-nat-instance \
  --template-body https://s3-eu-west-1.amazonaws.com/widdix-aws-cf-templates/vpc/vpc-nat-instance.yaml \
  --capabilities CAPABILITY_IAM \
  --parameters ParameterKey=ParentVPCStack,ParameterValue=vpc \
               ParameterKey=ParentSSHBastionStack,ParameterValue=vpc-ssh-bastion \
               ParameterKey=KeyName,ParameterValue=pgarbe

Single Docker (Ubuntu)
aws cloudformation create-stack  \
  --template-body file://./ubuntu/stack.yaml \
  --stack-name docker \
  --capabilities CAPABILITY_IAM \
  --parameters ParameterKey=ParentVPCStack,ParameterValue=vpc \
               ParameterKey=ParentSSHBastionStack,ParameterValue=vpc-ssh-bastion \
               ParameterKey=KeyName,ParameterValue=pgarbe \
               ParameterKey=DockerVersion,ParameterValue=1.13.0~rc6 \
               ParameterKey=DockerPreRelease,ParameterValue=true \
               ParameterKey=DesiredInstances,ParameterValue=1

https://github.com/pgarbe/containers_on_aws/blob/master/ubuntu/stack.yaml
https://iam.cloudonaut.io/
    Complete AWS IAM Reference
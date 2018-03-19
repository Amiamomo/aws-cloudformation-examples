https://stackoverflow.com/questions/41603517/installing-mysql-client-on-ec2-via-cloudformation
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/sample-templates-applications-eu-west-2.html
https://www.youtube.com/watch?v=8J0g_xWUzV0
https://s3.amazonaws.com/cloudformation-templates-us-east-1/


To run a simple script on an EC2 instance provisioned using CloudFormation, you use the UserData property of the AWS::EC2::Instance resource.


Description: Run a bash script using the UserData property.
Mappings:
  # amzn-ami-hvm-2016.09.1.20161221-x86_64-gp2
  RegionMap:
    us-east-1:
      "64": "ami-9be6f38c"
Resources:
  Instance:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: !FindInMap [ RegionMap, !Ref "AWS::Region", 64]
      InstanceType: m3.medium
      UserData:
        "Fn::Base64":
          !Sub |
            #!/bin/bash
            # Update all packages
            yum -y update
            # Install mysql client 
            yum -y install mysql

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-rds-database-instance.html
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/CHAP_TemplateQuickRef.html
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/quickref-s3.html
https://s3.amazonaws.com/cloudformation-templates-us-east-1/

https://aws.amazon.com/blogs/security/writing-iam-policies-how-to-grant-access-to-an-amazon-s3-bucket/

------------------------------------ S3_website ------------------------------------

Creating an Amazon S3 Bucket for Website Hosting and with a DeletionPolicy
S3_basic - not bucket is NOT deleted on delete_stack

aws cloudformation create-stack --stack-name S3-website --template-body file://D:\Dev\Python\doc\aws\CloudFormation\S3\S3_website.yml --region eu-west-2
aws cloudformation describe-stack-resources --stack-name S3-website
aws cloudformation delete-stack  --stack-name S3-website

https://s3-basic-s3bucket-7ljr615353r3.s3.amazonaws.com
http://s3-basic-s3bucket-7ljr615353r3.s3-website.eu-west-2.amazonaws.com

------------------------------------ S3-home-username ------------------------------------
aws cloudformation create-stack --stack-name S3-home-username --capabilities CAPABILITY_NAMED_IAM --template-body file://D:\Dev\Python\doc\aws\CloudFormation\S3\S3_home_username.yml --region eu-west-2
aws cloudformation describe-stack-resources --stack-name S3-home-username
aws cloudformation delete-stack  --stack-name S3-home-username

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": ["s3:ListBucket"],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket"],
      "Condition": {"StringLike": {"s3:prefix": ["${aws:username}/*"]}}
    },
    {
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket/${aws:username}/*"]
    }
  ]
}

This example uses the aws:username key, which returns the user's friendly name (like "Adele" or "David"). Under some circumstances, you might want to use the aws:userid key instead, which is a globally unique value. For more information, see Unique IDs.
          Resource: !Join ['', ['arn:aws:s3:::', !Ref 'S3HomeBucket']]

----------------------------------------------------------------------------------
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-bucket.html
https://stackoverflow.com/questions/36917947/create-folder-inside-s3-bucket-using-cloudformation
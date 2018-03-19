https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html
The following policy might be used for an IAM group. It gives users in that group the ability to create, use, and delete queues that have their names and that are in the us-east-2 region.

{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "sqs:*",
    "Resource": "arn:aws:sqs:us-east-2:*:${aws:username}-queue"
  }]
}
# aws-billing-emailer

# Solution Overview

This solution is designed to take an AWS Bill when it is generated and distributed it to an end user via AWS SNS, using a presigned URL from S3.

The solution diagram is attached, and works as follows:

![Slide1.JPG](https://github.com/jacklavelle286/aws-billing-emailer/assets/78485499/d000a023-b6c8-449c-b0ef-98530558a5a0)

1. An Eventbridge Rule triggers when a bill is created within the Billing console.

2. This triggers a lambda function (within a VPC for added security) which grabs the Billing statement and stores it in S3.

3. This S3 bucket has an event notification which triggers another lambda function which generates the pre-signed URL and shares it via Amazon SNS.
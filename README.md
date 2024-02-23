# aws-billing-emailer

# Solution Overview

This solution is designed to take an AWS Bill when it is generated and distributed it to an end user via AWS SNS, using a presigned URL from S3.

The solution diagram is attached, and works as follows:


![Slide1](https://github.com/jacklavelle286/aws-billing-emailer/assets/78485499/1465df88-5b40-40b8-94c4-a538feab0e5b)


1. An Eventbridge Rule triggers on a monthly basis.

2. This triggers a lambda function (within a VPC for added security) which grabs the top 10 services spend statement using the Cost Explorer APi, and stores it in S3 using CSV format.

3. This S3 bucket has an event notification which triggers another lambda function which generates the pre-signed URL and shares it via Amazon SNS.

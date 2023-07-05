# AWS Lambda

AWS Lambda is the Amazon serverless service. It can integrate with other AWS services, such as AWS IAM for managing permissions to AWS Lambda, Amazon CloudWatch for monitoring AWS Lambda, and Amazon S3 and Amazon EFS for persistent storage.

## Configuring IAM

AWS IAM is the supported service for managing permissions to AWS Lambda.

* [Identity-based IAM policies for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/access-control-identity-based.html)
* [Security best practices](https://docs.aws.amazon.com/whitepapers/latest/serverless-architectures-lambda/security-best-practices.html)
* [Encrypting Lambda environment variables](https://docs.aws.amazon.com/whitepapers/latest/kms-best-practices/encrypting-lambda-environment-variables.html)
* [serverless-puresec-cli](https://github.com/puresec/serverless-puresec-cli)

### Best practices

* Grant minimal IAM permissions for any newly created AWS Lambda function (for running tasks, accessing S3 buckets, monitoring using CloudWatch Events, and so on) – match a specific IAM role to any newly created AWS Lambda function.
* Use open source tools such as serverless-puresec-cli to generate IAM roles for your function.
* Avoid storing credentials inside AWS Lambda code.
* If you need to store sensitive data (such as credentials), use AWS Secrets Manager.
* For better protection of your Lamba functions, configure AWS Lambda behind Amazon API Gateway.
* For sensitive environments, encrypt Lambda environment variables using CMK management (as explained in Chapter 7, Applying Encryption in Cloud Services).
* Use TLS 1.2 to encrypt sensitive data over the network.
* Enforce MFA for end users who have access to the AWS API (console, CLI, and SDK) and perform privileged actions such as managing the Lambda service.


## Network access to AWS Lambda

AWS Lambda can be deployed either as an external resource outside a VPC or inside a VPC => it is important to plan before deploying each Lambda function.

* [Data protection in AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/security-dataprotection.html)
* [AWS Lambda now supports AWS PrivateLink](https://aws.amazon.com/about-aws/whats-new/2020/10/aws-lambda-now-supports-aws-privatelink/)
* [Configuring a Lambda function to access resources in a VPC](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html)
* [How do I give internet access to a Lambda function that's connected to an Amazon VPC?](https://aws.amazon.com/premiumsupport/knowledge-center/internet-access-lambda-function/)

### Best practices

* Use Amazon API Gateway to restrict access to your Lambda function, from a specific IP address or CIDR.
* If your Lambda function is located outside a VPC, and the Lambda function needs access to resources inside your VPC, use AWS PrivateLink, which avoids sending network traffic outside your VPC, through a secure channel, using an interface VPC endpoint.
* If your Lambda function is located inside your VPC, and the Lambda function needs access to external resources on the internet, use the NAT gateway to give your Lambda function the required access, without exposing Lambda to the internet directly.
* Use TLS 1.2 to encrypt traffic to and from your Lambda functions.

## Conducting auditing and monitoring

AWS allows you to enable auditing using the AWS CloudTrail service.

* [Using AWS Lambda with AWS CloudTrail](https://docs.aws.amazon.com/lambda/latest/dg/with-cloudtrail.html)
* [Using AWS Lambda with Amazon CloudWatch Events](https://docs.aws.amazon.com/lambda/latest/dg/services-cloudwatchevents.html)

### Best practices

* Enable enhanced monitoring of your Lambda functions.
* Use Amazon CloudWatch to detect spikes in Lambda usage.
* Use AWS CloudTrail to monitor API activities related to your Lambda function.

## Conducting compliance, configuration change, and secure coding

As a customer, you cannot control the underlying infrastructure => invest in secure coding to avoid attackers breaking into your application and causing harm that AWS cannot protect.

* [Using AWS Lambda with AWS Config](https://docs.aws.amazon.com/lambda/latest/dg/services-config.html)
* [Lambda function versions](https://docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html)
* [Use API Gateway Lambda authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html)
* [Setting up automatic assessment runs through a Lambda function](https://docs.aws.amazon.com/inspector/latest/userguide/inspector_assessments.html#assessment_runs-schedule)
* [Configuring code signing for AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/configuration-codesigning.html)
* [OWASP Serverless Top 10](https://owasp.org/www-project-serverless-top-10/)

### Best practices

* Follow the OWASP Serverless Top 10 project documentation when writing your Lambda function code.
* Enable versions in your Lambda functions, to be able to roll back to previous code.
* Use AWS Signer to sign your Lambda function code and make sure you only run signed code.
* If you use Amazon API Gateway in front of your Lambda functions, use the API Gateway Lambda authorizer as an extra layer of protection for authorizing access to your Lambda functions.
* Use AWS Config to check for changes in your Lambda functions.
* Use Amazon Inspector assessment templates to detect non-compliance or the use of old versions of a runtime in your Lambda functions.

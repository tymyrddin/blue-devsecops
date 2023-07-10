# Elastic Container Service (ECS)

ECS is the Amazon-managed container orchestration service. It can integrate with other AWS services such as Amazon Elastic Container Registry (ECR) for storing containers, AWS IAM for managing permissions to ECS, and Amazon CloudWatch for monitoring ECS.

## Configuring IAM

AWS IAM is the supported service for managing permissions to access and run containers through Amazon ECS.

* [Amazon ECS container instance IAM role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/instance_IAM_role.html).
* [IAM roles for tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html).
* [authorisation based on Amazon ECS tags](https://docs.aws.amazon.com/AmazonECS/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-tags).
* [Using IAM to control filesystem data access](https://docs.aws.amazon.com/efs/latest/ug/iam-access-control-nfs-efs.html).
* [Amazon ECS task and container security](https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/security-tasks-containers.html).

### Best practices

* Grant minimal IAM permissions for the Amazon ECS service.
* If you are managing multiple AWS accounts, use temporary credentials (using AWS Security Token Service or the AssumeRole capability) to manage ECS on the target AWS account with credentials from a source AWS account.
* Use service roles to allow the ECS service to assume your role and access resources such as S3 buckets, RDS databases, and so on.
* Use IAM roles to control access to Amazon Elastic File System (EFS) from ECS.
* Enforce multifactor authentication (MFA) for end users who have access to the AWS console and perform privileged actions such as managing the ECS service.
* Enforce policy conditions such as requiring end users to connect to the ECS service using a secured channel (SSL/TLS), connecting using MFA, log in at specific hours of the day, etc.
* Store your container images inside Amazon ECR and grant minimal IAM permissions for accessing and managing Amazon ECR.

## Network access

Since Amazon ECS is a managed service, it is located outside the customer's VPC. An alternative to secure access from a VPC to the managed ECS environment is to use [AWS PrivateLink](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/vpc-endpoints.html), which avoids sending network traffic outside your VPC, through a secure channel, using an interface VPC endpoint.

### Best practices

* Use a secured channel (TLS 1.2) to control Amazon ECS using API calls.
* Use VPC security groups to allow access from your VPC to the Amazon ECS VPC endpoint.
* If you use AWS Secrets Manager to store sensitive data (such as credentials) from Amazon ECS, use a Secrets Manager VPC endpoint when configuring security groups.
* If you use AWS Systems Manager to remotely execute commands on Amazon ECS, use Systems Manager VPC endpoints when configuring security groups.
* Store container images inside Amazon ECR and for non-sensitive environments, encrypt your container images inside Amazon ECR using AWS KMS.
* For sensitive environments, encrypt container images inside Amazon ECR using CMK management.
* If you use Amazon ECR to store container images, use VPC security groups to allow access from your VPC to the Amazon ECR interface's VPC endpoint.

## Conducting auditing and monitoring

As with any other managed service, AWS allows you to enable logging and auditing using Amazon CloudWatch and AWS CloudTrail:

* [Logging and monitoring in Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs-logging-monitoring.html).
* [Logging Amazon ECS API calls with AWS CloudTrail](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/logging-using-cloudtrail.html).

### Best practices

* Enable Amazon CloudWatch alarms for high-performance usage (which may indicate an anomaly in the ECS cluster behaviour).
* Enable AWS CloudTrail for any action performed on the ECS cluster.
* Limit the access to the CloudTrail logs to the minimum number of employees – preferably in an AWS management account, outside the scope of your end users
(including outside the scope of your ECS cluster administrators), to avoid possible deletion or changes to the audit logs.

## Enabling compliance

### Best practices

* Use only trusted image containers and store them inside [Amazon ECR – a private repository](https://docs.aws.amazon.com/AmazonECR/latest/userguide/Repositories.html) for storing your organisational images.
* Run the [Docker Bench for Security](https://github.com/docker/docker-bench-security) tool on a regular basis to check for compliance with CIS Benchmarks for Docker containers.
* Build your container images from scratch (to avoid malicious code in preconfigured third-party images).
* Scan your container images for vulnerabilities in libraries and binaries and update your images on a regular basis.
* Configure your images with a read-only root filesystem to avoid unintended upload of malicious code into your images.

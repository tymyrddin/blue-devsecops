# Elastic Kubernetes Service (EKS)

EKS is the Amazon-managed Kubernetes orchestration service. It can integrate with other AWS services, such as Amazon ECR for storing containers, AWS IAM for managing permissions to EKS, and Amazon CloudWatch for monitoring EKS.

## Configuring IAM

AWS IAM is the supported service for managing permissions to access and run containers through Amazon EKS.

* [How Amazon EKS works with IAM](https://docs.aws.amazon.com/eks/latest/userguide/security_iam_service-with-iam.html)
* [IAM roles for service accounts](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html)
* [IAM Controlling Access to EKS Clusters](https://aws.github.io/aws-eks-best-practices/security/docs/iam/)

### Best practices

* Grant minimal IAM permissions for accessing and managing Amazon EKS.
* If you are managing multiple AWS accounts, use temporary credentials (using AWS Security Token Service or the AssumeRole capability) to manage EKS on the target AWS account with credentials from a source AWS account.
* Use service roles to allow the EKS service to assume your role and access resources such as S3 buckets and RDS databases.
* For authentication purposes, avoid using service account tokens.
* Create an IAM role for each newly created EKS cluster.
* Create a service account for each newly created application.
* Always run applications using a non-root user.
* Use IAM roles to control access to storage services (such as Amazon EBS, Amazon EFS, and Amazon FSx for Lustre) from EKS.
* Enforce MFA for end users who have access to the AWS console and perform privileged actions such as managing the EKS service.
* Store your container images inside Amazon ECR and grant minimal IAM permissions for accessing and managing Amazon ECR.

## Network access

Amazon EKS is a managed service, and located outside the customer's VPC. An alternative to secure access from a VPC to the managed EKS environment is to use AWS PrivateLink, which avoids sending network traffic outside your VPC, through a secure channel, using an interface VPC endpoint.

* [Network security](https://aws.github.io/aws-eks-best-practices/security/docs/network)
* [Amazon EKS networking](https://docs.aws.amazon.com/eks/latest/userguide/eks-networking.html)
* [Introducing security groups for Pods](https://aws.amazon.com/blogs/containers/introducing-security-groups-for-pods/)
* [EKS best practice guides](https://aws.github.io/aws-eks-best-practices/)

### Best practices

* Use TLS 1.2 to control Amazon EKS using API calls.
* Use TLS 1.2 when configuring Amazon EKS behind AWS Application Load Balancer or AWS Network Load Balancer.
* Use TLS 1.2 between your EKS control plane and the EKS cluster's worker nodes.
* Use VPC security groups to allow access from your VPC to the Amazon EKS VPC endpoint.
* Use VPC security groups between your EKS control plane and the EKS cluster's worker nodes.
* Use VPC security groups to protect access to your EKS Pods.
* Disable public access to your EKS API server – either use an EC2 instance (or bastion host) to manage the EKS cluster remotely or create a VPN tunnel from your remote machine to your EKS cluster.
* If you use AWS Secrets Manager to store sensitive data (such as credentials) from Amazon EKS, use a Secrets Manager VPC endpoint when configuring security groups.
* Store your container images inside Amazon ECR, and for non-sensitive environments, encrypt your container images inside Amazon ECR using AWS KMS.
* For sensitive environments, encrypt your container images inside Amazon ECR using CMK management.
* If you use Amazon ECR to store your container images, use VPC security groups to allow access from your VPC to the Amazon ECR interface VPC endpoint.

## Conducting auditing and monitoring

AWS allows for logging and auditing using CloudWatch and AWS CloudTrail.

* [Amazon EKS control plane logging](https://docs.aws.amazon.com/eks/latest/userguide/control-plane-logs.html)
* [Auditing and logging](https://aws.github.io/aws-eks-best-practices/security/docs/detective/)

### Best practices

* Enable the Amazon EKS control plane when logging in to Amazon CloudWatch – this allows you to log API calls, audit, and authentication information from the EKS cluster.
* Enable AWS CloudTrail for any action performed on the EKS cluster.
* Limit the access to the CloudTrail logs to the minimum number of employees – preferably in an AWS management account, outside the scope of your end users (including outside the scope of your EKS cluster administrators), to avoid possible deletion or changes to the audit logs.

## Enabling compliance

* [Configuration and vulnerability analysis in Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/configuration-vulnerability-analysis.html)
* [Introducing the CIS Amazon EKS Benchmark](https://aws.amazon.com/blogs/containers/introducing-cis-amazon-eks-benchmark/)
* [Compliance](https://aws.github.io/aws-eks-best-practices/security/docs/compliance/)
* [Image security](https://aws.github.io/aws-eks-best-practices/security/docs/image/)
* [Pod security](https://aws.github.io/aws-eks-best-practices/security/docs/pods/)
* [kube-bench](https://github.com/aquasecurity/kube-bench)
* [Docker Bench for Security](https://github.com/docker/docker-bench-security)
* [Amazon ECR private repositories](https://docs.aws.amazon.com/AmazonECR/latest/userguide/Repositories.html)

### Best practices

* Use only trusted image containers and store them inside Amazon ECR – a private repository for storing your organizational images.
* Run the kube-bench tool on a regular basis to check for compliance with CIS Benchmarks for Kubernetes.
* Run the Docker Bench for Security tool on a regular basis to check for compliance with CIS Benchmarks for Docker containers.
* Build your container images from scratch (to avoid malicious code in preconfigured third-party images).
* Scan your container images for vulnerabilities in libraries and binaries and update your images on a regular basis.
* Configure your images with a read-only root filesystem to avoid unintended upload of malicious code into your images.

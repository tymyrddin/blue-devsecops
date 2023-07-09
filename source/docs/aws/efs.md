# Elastic File System (EFS)

Amazon Elastic File System (Amazon EFS) is based on the NFS protocol.

## Authentication and authorisation

* [Identity and access management for Amazon EFS](https://docs.aws.amazon.com/efs/latest/ug/auth-and-access-control.html)
* [Working with users, groups, and permissions at the Network File System (NFS) Level](https://docs.aws.amazon.com/efs/latest/ug/accessing-fs-nfs-permissions.html)
* [AWS managed policies for Amazon EFS](https://docs.aws.amazon.com/efs/latest/ug/security-iam-awsmanpol.html)
* [Security in Amazon EFS](https://docs.aws.amazon.com/efs/latest/ug/security-considerations.html)
* [Overview of managing access permissions to your Amazon EFS resources](https://docs.aws.amazon.com/efs/latest/ug/access-control-overview.html)

### Best practices

* Avoid using the AWS root account to access AWS resources such as Amazon EFS.
* Create an IAM group, add users to the IAM group, and then grant the required permissions on the target Amazon EFS to the target IAM group.
* Use IAM roles for federated users, AWS services, or applications that need access to Amazon EFS.
* Use IAM policies to grant the minimal required permissions to create EFS volumes or access and use Amazon EFS.
* When using IAM policies, specify conditions (such as the source IP) and what actions an end user can, along with the mentioned condition, take on the target filesystem.
* Use resource-based policies to configure who can access the EFS volume and what actions this end user can take on the filesystem (for example, mount, read, write,
and more).

## Network access

Amazon EFS is a managed service and located outside the customer's VPC. Protect access to the Amazon EFS service.

* [Controlling network access to Amazon EFS file systems for NFS clients](https://docs.aws.amazon.com/efs/latest/ug/NFS-access-control-efs.html)
* [Working with Amazon EFS Access Points](https://docs.aws.amazon.com/efs/latest/ug/efs-access-points.html)
* [Amazon Elastic File System Network Isolation](https://docs.aws.amazon.com/efs/latest/ug/network-isolation.html)
* [Data encryption in Amazon EFS](https://docs.aws.amazon.com/efs/latest/ug/encryption.html)
* [Using IAM to enforce creating encrypted file systems](https://docs.aws.amazon.com/efs/latest/ug/using-iam-to-enforce-encryption-at-rest.html)

### Best practices

* Keep Amazon EFS (that is, all storage classes) private.
* Use VPC security groups to control the access between your Amazon EC2 machines and the Amazon EFS mount volumes.
* To secure access from your VPC to the Amazon EFS, use AWS PrivateLink, which avoids sending network traffic outside your VPC, through a secure channel, using an interface's VPC endpoint.
* Use Amazon EFS access points to manage application access to the EFS volume.
* Use STS to allow temporary access to Amazon EFS.
* Use an IAM policy to enforce encryption at rest for Amazon EFS filesystems. You can do this by setting the value of elasticfilesystem:Encrypted to True inside the IAM policy condition.
* For sensitive environments, use the EFS mount helper to enforce the use of encryption in transit using TLS version 1.2 when mounting an EFS volume.
* Encrypt data at rest using AWS-managed CMK for Amazon EFS.
* For sensitive environments, encrypt data at rest using a CMK.

## Conducting auditing and monitoring

AWS allows enabling logging and auditing using Amazon CloudWatch and AWS CloudTrail.

* [Logging and Monitoring in Amazon EFS](https://docs.aws.amazon.com/efs/latest/ug/logging-monitoring.html)

### Best practices

* Enable Amazon CloudWatch alarms for excessive Amazon EFS usage (for example, a high volume of store or delete operations on a specific EFS volume).
* Enable the use of AWS CloudTrail for any EFS volume to log any activity performed on the Amazon EFS API, including any activity conducted by a user, role, or AWS service.
* Create a trail, using AWS CloudTrail, on any EFS volume to log events, such as a requested action, date, and time, requested parameters, and more, for access to objects stored inside AWS EFS.
* Limit the access to the CloudTrail logs to a minimum number of employees, preferably those with an AWS management account, outside the scope of your end users (including outside the scope of your users), to avoid possible deletion or changes to the audit logs.

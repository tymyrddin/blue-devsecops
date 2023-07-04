# RDS for MySQL

## Configuring IAM

MySQL supports the following types of authentication methods:

* Local username/password authentication against MySQL's built-in authentication mechanism.
* AWS IAM database authentication.
* AWS Directory Service for Microsoft AD authentication.

### Best practices

* For the local MySQL default user, create a strong and complex password, and keep the password in a secured location.
* For end users who need direct access to the managed database, the preferred method is to use the AWS IAM service.
* If you manage user identities using AWS Directory Service for Microsoft AD (AWS-managed Microsoft AD), use it to authenticate end users using the [Kerberos protocol](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/mysql-kerberos.html).

## Securing network access

Access to a managed MySQL database service is controlled via database security groups, which are equivalent to security groups and the on-premises layer 4 network firewall or access control mechanism.

### Best practices

* Managed databases must never be accessible from the internet or a publicly accessible subnet – always use private subnets to deploy databases.
* [Configure security groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html) for web or application servers and set the security group as target CIDR when creating a database security group.
* If you need to manage the MySQL database service, either use an EC2 instance (or bastion host) to manage the MySQL database remotely or create a VPN tunnel from your remote machine to the managed MySQL database.
* Since Amazon RDS is a managed service, it is located outside the customer's VPC. An alternative to secure access from your VPC to the managed RDS environment is to use [AWS PrivateLink](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/vpc-interface-endpoints.html), which avoids sending network traffic outside your VPC, through a secure channel, using an interface VPC endpoint.
* Set names and descriptions for the database security groups to allow a better understanding of the database security group's purpose.
* Use tagging (labelling) for database security groups to allow a better understanding of which database security group belongs to which AWS resources.

## Stored data

To protect customers' data, encrypt data both in transport and at rest.

### Best practices

* Enable [SSL/TLS 1.2](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/ssl-certificate-rotation-mysql.html) transport layer encryption to the database.
* [Select the right encryption oprions](https://aws.amazon.com/blogs/database/selecting-the-right-encryption-options-for-amazon-rds-and-amazon-aurora-database-engines/):
  * For non-sensitive environments, encrypt data at rest using AWS KMS.
  * For sensitive environments, encrypt data at rest using [customer master key (CMK)](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.Encryption.Keys.html) management.

## Conducting auditing and monitoring

As with any other managed service, AWS allows for logging and auditing using two built-in services:

* Amazon CloudWatch: A service that allows logging database activities and [raise an alarm](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Events.html) according to predefined thresholds.
* [AWS CloudTrail](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/logging-using-cloudtrail.html): A service that allows monitoring API activities (any action performed as part of the AWS RDS API).

### Best practices

* Enable Amazon CloudWatch alarms for high-performance usage (which may indicate anomalies in the database behavior).
* Enable AWS CloudTrail for any database, to log any activity performed on the database by any user, role, or AWS service.
* Limit access to the CloudTrail logs to the minimum number of people – preferably in an AWS management account, outside the scope of your end users (including outside the scope of your database administrators), to avoid possible deletion or changes to the audit logs.

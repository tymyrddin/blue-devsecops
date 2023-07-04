# Elastic Compute Cloud (EC2)

* Use only [trusted AMI](https://docs.aws.amazon.com/marketplace/latest/userguide/best-practices-for-building-your-amis.html) when deploying EC2 instances.
* Use a minimal number of packages inside an AMI, to lower the attack surface.
* Use Amazon built-in agents for EC2 instances (backup, patch management, hardening, monitoring, and others).
* Use the new generation of EC2 instances, based on the [AWS Nitro System](https://aws.amazon.com/ec2/nitro/).

## Authenticating to an instance

AWS does not have access to customers' VMs. When running the ***EC2 launch deployment*** wizard, you must choose either an existing key pair or create a new key. This set of private/public keys is generated at the client browser – AWS does not have any access to these keys, and therefore cannot log in to your EC2 instance.

For Linux instances, the key pair is used for [logging in to the machine via the SSH protocol](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html). For Windows instances, the key pair is used to [retrieve the built-in administrator's password](https://docs.amazonaws.cn/en_us/AWSEC2/latest/WindowsGuide/ec2-windows-passwords.html)

### Best practices

* Keep the private keys in a secured location. An alternative for storing and retrieving SSH keys is to use [AWS Secrets Manager](https://aws.amazon.com/blogs/security/how-to-use-aws-secrets-manager-securely-store-rotate-ssh-key-pairs/).
* Avoid storing private keys on a bastion host or any instance directly exposed to the internet. An alternative to logging in using SSH, without an SSH key, is to use AWS Systems Manager, through [Session Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-getting-started-enable-ssh-connections.html).
* [Join Windows](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/launching_instance.html) or [join Linux](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/seamlessly_join_linux_instance.html) instances to an Active Directory (AD) domain and use AD credentials to log in to the EC2 instances (and avoid using local credentials or SSH keys completely).

## Network access to an instance

Access to AWS resources and services such as EC2 instances is controlled via [security groups (at the EC2 instance level)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) or a network access control list (NACL) (at the subnet level), equivalent to the on-premises layer 4 network firewall or access control mechanism. Parameters such as source IP (or CIDR), destination IP (or CIDR), destination port (or predefined protocol), and whether the port is TCP or UDP, can be configured. It is also possible to use another security group as either the source or destination in a security group.

### Best practices

* For remote access protocols (SSH/RDP), limit the source IP (or CIDR) to well-known addresses. Good alternatives for allowing remote access protocols to an EC2 instance are to use a VPN tunnel, a bastion host, or [AWS Systems Manager Session Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html).
* For file sharing protocols (CIFS/SMB/FTP), limit the source IP (or CIDR) to well-known addresses.
* Set names and descriptions for security groups to allow a better understanding of the security group's purpose.
* Use tagging (labelling) for security groups to allow a better understanding of which security group belongs to which AWS resources.
* Limit the number of ports allowed in a security group to the minimum required ports for allowing your service or application to function.

## Instance metadata

An example of metadata about a running instance can be retrieved from within an instance, by opening a browser from within the operating system or by using the command line, to a URL such as `http://<IP address>/latest/meta-data/`. The IP address is an internal IP and cannot be accessed from outside the instance, but the information, by default, can be retrieved locally without authentication.

[Instance Metadata Service Version 2 (IMDSv2)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-service.html) allows for enforcing authenticated or session-oriented requests to the instance metadata:

```text
aws ec2 modify-instance-metadata-options \
    --instance-id <INSTANCE-ID> \
    --http-endpoint enabled --http-tokens required
```

## Serial console connection

For troubleshooting purposes, you can connect using a serial console to resolve network or operating system problems when SSH or RDP connections are not available:

```text
aws ec2 enable-serial-console-access --region <Region_Code>
```

This exposes the EC2 instance, so [configure access to the EC2 serial console](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configure-access-to-serial-console.html):

### Best practices

* Limit access to the EC2 serial console to the group of individuals using identity and access management (IAM) roles.
* Only allow access to EC2 serial console when required.
* Set a user password on an instance before allowing the EC2 serial console.

## Patch management

To deploy security patches for either Windows or Linux-based instances in a standard manner, use the [AWS Systems Manager](https://aws.amazon.com/blogs/mt/software-patching-with-aws-systems-manager/):

1. Configure the patch baseline.
2. Scan the EC2 instances for deviation from the patch baseline at a scheduled interval.
3. Install missing security patches on your EC2 instances.
4. Review the Patch Manager reports.

### Best practices

* Use AWS Systems Manager Compliance to make sure all your EC2 instances are up to date.
* Create a group with minimal IAM privileges to allow only relevant team members to conduct patch deployment.
* Use tagging (labelling) for your EC2 instances to allow patch deployment groups per tag (for example, production versus development environments).
* For stateless EC2 instances (where no user session data is stored inside an EC2 instance), replace an existing EC2 instance with a new instance, created from an up-to-date operating system image.

## Backups

The [AWS Backup](https://aws.amazon.com/blogs/storage/protecting-your-data-with-aws-backup/) service encrypts backups in transit and at rest using AWS encryption keys, stored in AWS Key Management Service (KMS), as an extra layer of security, independent of Elastic Block Store (EBS) volume or snapshot encryption keys.

### Best practices

* Configure the AWS Backup service with an IAM role to allow access to the encryption keys stored inside AWS KMS.
* Configure the AWS Backup service with an IAM role to allow access to your backup vault.
* Use tagging (labelling) for backups to allow a better understanding of which backup belongs to which EC2 instance.
* Consider [replicating backups to another region](https://docs.aws.amazon.com/aws-backup/latest/devguide/cross-region-backup.html).

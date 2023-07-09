# Site-to-Site VPN

AWS Site-to-Site VPN is a managed service connecting corporate networks to the AWS environment in a secure IPsec channel.

## Best practices

* Restrict access to AWS resources inside your AWS environment using Amazon VPC security groups and authorization rules.
* For non-sensitive environments, use pre-shared keys to authenticate to the site-to-site VPN tunnel.
* For highly sensitive environments, use a private certificate from the AWS Certificate Manager (ACM) Private Certificate Authority (CA) service.
* Create an IAM group, add users to the group, and grant the required permissions on the AWS Site-to-Site VPN connection for the target group an example of an IAM role would be the ability to invoke an API action through the VPN).
* It is recommended to schedule a maintenance window and rotate the pre-shared keys or the certificate for the AWS Site-to-Site VPN connection once a year, to avoid potential compromise.
* Use Amazon CloudWatch to monitor the VPN tunnels (for example, it could send an alarm when the amount of traffic in bytes is above a pre-defined threshold).
* Use AWS CloudTrail to monitor users' activity on the AWS VPN service.

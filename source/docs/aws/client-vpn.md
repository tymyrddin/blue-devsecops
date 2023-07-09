# Client VPN

AWS Client VPN allows you to connect to the AWS environment from anywhere on the internet using an OpenVPN client in a secure TLS channel.

## Best practices

* Restrict access to AWS resources inside your AWS environment using VPC security groups and authorization rules.
* If you are managing your user identities with AWS Directory Service, use AWS Client VPN Active Directory authentication.
* If you are using the SAML 2.0 federated authentication service, use AWS Client VPN single sign-on authentication (SAML authentication).
* For highly sensitive environments, use AWS Client VPN certificate-based authentication using the ACM service.
* If you are using AWS Client VPN certificate-based authentication, use client certificate revocation lists to revoke access to employees who have left the organization or do not need access through the VPN.
* Use Amazon CloudWatch to monitor the VPN tunnels (for example, it could send an alarm when the amount of traffic in bytes is above a pre-defined threshold).
* Use AWS CloudTrail to monitor users' activity on the AWS VPN service.

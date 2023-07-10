# Shield

AWS Shield is the Amazon managed DDoS protection service and comes in two price models:

* AWS Shield Standard: This is the default and free Layer 7 DDoS protection (HTTP/HTTPS), provided for all customers. 
* AWS Shield Advanced: This offers Layers 3/4 (Network layer) and Layer 7
(Application layer) DDoS protection, with additional protection for AWS services
such as DNS (Route 53), CDN (CloudFront), Elastic Load Balancing (ELB), and
virtual machine (EC2) services. This price tier also offers support from the AWS
DDoS response team.

## Best practices

* Use AWS Shield Standard for any web-based production environment you expose to the internet.
* Use AWS Shield Advanced for large-scale production environments you expose to the internet for better insights into the attacks.
* When using AWS Shield Advanced, register an Elastic IP (EIP) address as a protected source to allow quicker detection of attacks.
* When using AWS Shield Advanced, you can generate near real-time reports about attacks on resources in your AWS account(s).
* When combining AWS Shield and the AWS WAF service, use Amazon CloudWatch to monitor incoming requests and alert you when there is a spike in incoming requests, to have preliminary alerts on incoming DDoS attacks.
* Use AWS Identity and Access Management (IAM) to limit the permissions to the AWS Shield Console.
* Use AWS CloudTrail to log actions in the AWS Shield Console.


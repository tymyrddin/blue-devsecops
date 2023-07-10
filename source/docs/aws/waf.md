# AWS WAF

AWS WAF offers protection against the following types of attacks:

* Layer 7 DDoS attacks (when combined with AWS Shield)
* Common web application attacks
* Bots (non-human generated traffic)

AWS WAF also allows you to protect the following Amazon services:

* Amazon CloudFront: The Amazon managed CDN service
* Amazon API Gateway: The Amazon managed API gateway service
* Amazon ALB: The Amazon managed Application Load Balancer service (Layer 7 load balancer)

## Best practices

* To protect an external web resource, create web ACLs, with either allow or block actions.
* When creating a new web ACL rule, change the default CloudWatch metric name to an informative name that will allow you to detect it later when reviewing the CloudWatch logs.
* Use Amazon CloudWatch to monitor your web ACL rule activity.
* For protection against non-standard types of web application attacks, create your own custom rules.
* For better protection, subscribe to the rules available on the AWS Marketplace (created by security vendors).
* For large-scale environments with multiple AWS accounts, use AWS Firewall Manager to centrally create and enforce WAF rules.
* Send AWS WAF logs to the Amazon Kinesis Data Firehose service to review near real-time logs of attacks.
* Use AWS Config to enable logging for every newly created web ACL.
* Use AWS IAM to limit the permissions to the AWS WAF Console.
* Use AWS CloudTrail to log actions in the AWS WAF Console.


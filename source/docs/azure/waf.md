# WAF

Azure WAF is integrated with and can be deployed as part of:

* Azure Application Gateway: A Layer 7 load balancer service
* Azure Front Door: A global web application threat protection service
* Azure CDN: A managed CDN

## Best practices

* Deploy Azure WAF v2 license on any newly exposed web application.
* For large-scale environments with multiple Azure subscriptions and multiple
web applications, use Azure WAF with Azure Front Door to protect your
web applications.
* After learning the traffic for your production web application (running WAF in
learning mode), configure Azure WAF in prevention mode.
* For protection against non-standard types of web application attacks, create your
own custom rules.
* Create custom rules to block traffic originating from known malicious IP addresses.
* Use Azure activity logs as part of the Azure Monitor service to monitor changes in
Azure WAF rules.
* Send Azure WAF logs to Azure Sentinel to detect and remediate web-based attacks.
* Use Azure Active Directory to limit the permissions to the Azure WAF console.

# DDoS Protection

Azure DDoS Protection is the Azure managed DDoS protection service.

It comes in two price models:

* Azure DDoS Protection Basic: This provides Layers 3/4 (Network layer) and Layer 7 DDoS protection (HTTP/HTTPS), offered at no cost.
* Azure DDoS Protection Standard: This provides Layers 3/4 (Network layer) and Layer 7 DDoS protection (HTTP/HTTPS), with additional protection at the [VNet](vnet.md) level, with extra logging and alerting capability.

## Best practices

* Enable Azure DDoS Protection Basic for any production environment you expose to the internet.
* Use Azure DDoS Protection Standard for large-scale production environments you expose to the internet for better insights into attacks.
* When using Azure DDoS Protection Standard, enable resource logs for public IP addresses to have quicker detection of attacks.
* When combining Azure Application Gateway with a WAF, you add protection against web application attacks.
* Use Azure Monitor to monitor and alert you when there is a spike in incoming requests to have a preliminary alert on incoming DoS attacks.
* Send Azure DDoS Protection logs to Azure Sentinel for further analysis of DDoS attacks.
* Use Azure Active Directory to limit the permissions to the Azure DDoS Protection Console.
* When using Azure DDoS Protection Standard, you can conduct simulations of DDoS attacks against your Azure staging or production Azure environments (at non-peak hours) by using a third-party solution from BreakingPoint Cloud. Simulations will allow you to have a better understanding of how effective the DDoS Protection plans are and help to train your teams.

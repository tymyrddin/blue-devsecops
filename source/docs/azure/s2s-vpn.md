# Site-to-Site VPN

Azure VPN Gateway (Site-to-Site) is a managed service that allows connecting corporate networks to the Azure environment in a secure channel.

## Best practices

* Restrict access to Azure resources inside your Azure environment using NSGs.
* Use the GCMAES256 algorithm for both encryption of the IPsec tunnel and ensuring the integrity of the traffic passing through the tunnel.
* Use pre-shared keys to authenticate to the site-to-site VPN tunnel.
* For large-scale environments with multiple Azure subscriptions and multiple site-to-site VPN gateways, use Azure Firewall to centrally create, enforce, and log network policies across multiple subscriptions.
* Use Azure Monitor to monitor the VPN tunnels (for example, it could send alerts when the amount of traffic in bytes is above a pre-defined threshold).
* Enable Azure DDoS Protection to protect your VPN gateway from DDoS attacks.

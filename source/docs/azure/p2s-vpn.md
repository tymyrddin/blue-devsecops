# Point-to-Site VPN

Azure VPN Gateway (Point-to-Site) allows connection from anywhere on the internet to the Azure environment in a secure channel using an OpenVPN client, Secure Socket Tunneling Protocol (SSTP), or Internet Key Exchange version 2 (IKEv2) VPN client.

## Best practices

* If you are managing user identities inside Azure Active Directory, use Azure Active Directory to authenticate users to the VPN gateway, combined with Azure RBACs to provide minimal access to resources on your Azure environment.
* If authenticating users through Azure Active Directory, enforce MFA for your end users.
* For highly sensitive environments, use certificates to authenticate to the point-to-site VPN tunnel.
* Restrict access to Azure resources inside your Azure environment using NSGs.
* Use the GCMAES256 algorithm for both encryption of the IPSec tunnel and ensuring the integrity of the traffic passing through the tunnel.
* Use Azure Monitor to monitor the VPN tunnels (for example, it could send alerts when the amount of traffic in bytes is above a pre-defined threshold) and to log audit-related events (an example of suspicious behaviour could be a user attempting to log-in in the middle of the night for the first time).
* Enable Azure DDoS Protection to protect your VPN gateway from DDoS attacks.
* Use Azure Advanced Threat Protection to identify anomalous behaviour of users connecting through the point-to-site VPN tunnel.
* Use Azure Security Center to detect security-related events through the VPN gateway.

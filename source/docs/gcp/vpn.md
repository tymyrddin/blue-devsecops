# Managed VPN

Google Cloud VPN is a managed service that allows one to connect a corporate network to the GCP environment in a secure channel (using an IPSec tunnel).

## Best practices

* Restrict access to GCP resources inside your Google Cloud VPC using VPC firewall rules.
* Use the AES-GCM-16-256 algorithm for both encryption of the IPSec tunnel and ensuring the integrity of the traffic passing through the tunnel.
* Use a strong, 32-character, pre-shared key to authenticate to the Google Cloud VPN tunnel.
* Create an IAM group, add users to the group, and grant the required permissions on the Google Cloud VPN connection for the target group.
* Use Google Cloud Logging to monitor activity on the Google Cloud VPN service.

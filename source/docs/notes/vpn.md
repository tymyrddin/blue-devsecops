# Securing VPN services

Each cloud provider has its own implementation of a VPN service. VPNs allow network-based access to private resources over untrusted networks.

* Combined with a firewall, a VPN allows organizations to access and manage their
internal resources (both sides of the VPN tunnel) in a secure manner.
* A VPN allows corporate users to connect to their organization's cloud environment
from either the corporate network or from home.
* The connection between the VPN and the cloud environment is encrypted.
* The connection to the cloud environment is transparent (that is, the same as
working locally from the corporate network).
* The VPN can enforce the use of multifactor authentication (MFA) for end users
connecting using a client VPN.

## Best practices

* [AWS Site-to-Site VPN](../aws/s2s-vpn.md)
* [AWS Client VPN](../aws/client-vpn.md)
* [Azure VPN Gateway (Site-to-Site)](../azure/s2s-vpn.md)
* [Azure VPN Gateway (Point-to-Site)](../azure/p2s-vpn.md)
* [Google Cloud VPN](../gcp/vpn.md)
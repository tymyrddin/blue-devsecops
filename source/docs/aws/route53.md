# Route 53

## Best practices

* Create an Identity and Access Management (IAM) group, add users to the group, and grant the required permissions on the Route 53 service for the target group.
* Enable Domain Name System Security Extensions (DNSSEC signing) on any public-hosted zone to protect against DNS spoofing attacks.
* Use a new customer master key (CMK) to sign any newly created public-hosted zone.
* Make sure privacy protection is enabled for any domain you manage using Route 53 to protect the privacy of domain owners' contact information.
* Enable the Route 53 domain transfer lock to prevent your domains from being transferred to another registrar.
* Create a sender policy framework (SPF) record on your Route 53 hosted domain to publicly specify which mail servers are authorized to send emails on behalf of your email domain.
* Use the Route 53 Resolver DNS Firewall to block DNS-level threats originating from your VPC.
* Remove unassigned DNS records from your hosted zones (records of resources such as IP addresses that connected to a resource that was removed).
* Use private hosted zones to manage DNS records for internal resources (such as resources located inside private subnets).
* Enable public DNS query logging to be able to analyze which public DNS queries were submitted to Route 53 about your domains.
* Enable Resolver query logging to be able to analyze information such as the Route 53 Resolver DNS Firewall block rules.
* Enable Amazon GuardDuty to analyze DNS logs and raise alerts about suspicious activity, such as C&C activity, Bitcoin mining, and more.
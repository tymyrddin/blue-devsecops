# Managed DNS

## Best practices

* Create an IAM group, add users to the group, and grant the required permissions on the Google Cloud DNS service for the target group.
* Enable DNSSEC signing on any public-hosted zone to protect against DNS spoofing attacks.
* Remove unassigned DNS records from your hosted zones (records of resources such as IP addresses that connected to a resource that was removed).
* Use Google Cloud DNS private zones to manage DNS records for internal resources (such as resources located inside private subnets).
* Enable Google Cloud DNS audit logs to monitor DNS activity.
* Note that admin activity audit logs are enabled by default and cannot be disabled.
* Explicitly enable data access audit logs to log activities in Google Cloud DNS.
* Limit access to audit logs to the minimum number of employees to avoid unwanted changes to the audit logs.
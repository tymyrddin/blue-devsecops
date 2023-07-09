# Managed DNS

## Best practices

* Grant minimal permissions for accessing and managing the Azure DNS using Azure role-based access controls (RBACs).
* Remove unassigned DNS records from your hosted zones (records of resources such as IP addresses that connected to a resource that was removed).
* Enable the ReadOnly lock for any hosted zone you manage using Azure DNS to protect from accidental changes to DNS records.
* Use private DNS zones to manage DNS records for internal resources (such as resources located inside private subnets).
* Use Azure Defender for DNS to detect and send alerts about suspicious DNS-related activities.
* Enable DNS logging and forward the logs to Azure Sentinel to detect suspicious behaviour on the Azure DNS service.
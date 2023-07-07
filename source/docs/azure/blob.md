# Blob storage

## Authentication and authorization

Azure controls authorization for Blob storage using Azure Active Directory. For temporary access to Azure Blob storage (that is, for an application or a non-human
interaction), use shared access signatures (SAS).

* [Authorize access to blobs using Azure Active Directory](https://docs.microsoft.com/en-us/azure/storage/common/storage-auth-aad)
* [Prevent Shared Key authorization for an Azure Storage account](https://docs.microsoft.com/en-us/azure/storage/common/shared-key-authorization-prevent?tabs=portal)
* [Grant limited access to Azure Storage resources using shared access signatures (SAS)](https://docs.microsoft.com/en-us/azure/storage/common/storage-sas-overview)
* [Security recommendations for Blob storage](https://docs.microsoft.com/en-us/azure/storage/blobs/security-recommendations)

### Best practices

* Create an Azure AD group, add users to the AD group, and then grant the required permissions on the target Blob storage to the target AD group.
* Use shared key authorization (SAS) to allow applications temporary access to Blob storage.
* Grant minimal permissions to Azure Blob storage.
* For data that you need to retain for long periods (due to regulatory requirements), use an immutable Blob storage lock to protect the data from accidental deletion.

## Network access

Because Azure Blob storage is a managed service, and located outside the customer's Virtual Network (VNet). It is important to protect access to the Azure Blob storage service.

* [Configure Azure Storage firewalls and virtual networks](https://docs.microsoft.com/en-us/azure/storage/common/storage-network-security?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&tabs=azure-portal)
* [Tutorial: Connect to a storage account using an Azure Private Endpoint](https://docs.microsoft.com/en-us/azure/private-link/tutorial-private-endpoint-storage-portal)
* [Require secure transfer to ensure secure connections](https://docs.microsoft.com/en-us/azure/storage/common/storage-require-secure-transfer)
* [Enforce a minimum required version of Transport Layer Security (TLS) for requests to a storage account](https://docs.microsoft.com/en-us/azure/storage/common/transport-layer-security-configure-minimum-version?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&tabs=portal)
* [Azure Storage encryption for data at rest](https://docs.microsoft.com/en-us/azure/storage/common/storage-service-encryption?toc=/azure/storage/blobs/toc.json)
* [Customer-managed keys for Azure Storage encryption](https://docs.microsoft.com/en-us/azure/storage/common/customer-managed-keys-overview?toc=/azure/storage/blobs/toc.json)

### Best practices

* Keep all Azure Blob storage (that is, all tiers) private.
* To secure access from your VNet to the Azure Blob storage, use an Azure private endpoint, which avoids sending network traffic outside your VNet through a secure channel.
* Unforce the use of transport encryption (HTTPS only) for all Azure Blob storage.
* For sensitive environments, require a minimum of TLS version 1.2 for Azure Blob storage.
* Deny default network access to the Azure storage account and only allow access from predefined conditions such as the setting up of IP addresses.
* Encrypt data at rest using Azure Key Vault.
* For sensitive environments (for example, which contain PII, credit card details, healthcare data, and more), encrypt data at rest using customer-managed keys (CMKs) stored inside Azure Key Vault.

## Auditing and monitoring

Azure allows you to monitor blob storage using Azure Monitor and Azure Security Center.

* [Monitoring Azure Blob storage](https://docs.microsoft.com/en-us/azure/storage/blobs/monitor-blob-storage?tabs=azure-portal)
* [Azure Storage analytics logging](https://docs.microsoft.com/en-us/azure/storage/common/storage-analytics-logging)
* [Log alerts in Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-unified-log)

### Best practices

* Enable log alerts using the Azure Monitor service to track access to the Azure Blob storage and raise alerts (such as multiple failed access attempts to Blob storage in a short period of time).
* Enable Azure storage logging to audit all authorization events for access to the Azure Blob storage.
* Log anonymous successful access attempts to locate an unauthorized access attempt to the Azure Blob storage.
* Enable Azure Defender for Storage to receive security alerts in the Azure Security Center console.

# Files

Azure Files is an Azure file storage service based on the SMB protocol.

## Authentication and authorization

Azure supports Active Directory Domain Services (AD DS) and Azure Active Directory Domain Services (Azure AD DS), an add-on service to Azure AD, which allows for authenticating to legacy services (SMB in the case of Azure Files) and protocols (Kerberos in the case of Azure Files).

* [Overview of Azure Files identity-based authentication options for SMB access](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-active-directory-overview)
* [Planning for an Azure Files deployment](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-planning)

### Best practices

* Use identity-based authentication to grant minimal permissions for sharing, directory, or file level access on the Azure Files service.
* For a cloud-native environment in Azure (with no on-premises VMs), make sure all VMs are joined to an Azure AD domain and that all VMs are connected to the same VNet as Azure AD DS.
* Enable Active Directory authentication over SMB to allow domain joined VMsaccess to Azure Files.
* Avoid using storage account keys for authenticating to Azure Files.

## Network access

Azure Files is a managed service, and located outside the customer's VNet.  Protect access to the Azure Files service.

* [Azure Files networking considerations](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-networking-overview)
* [Prevent accidental deletion of Azure file shares](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-prevent-file-share-deletion)
* [Require secure transfer to ensure secure connections](https://docs.microsoft.com/en-us/azure/storage/common/storage-require-secure-transfer?toc=/azure/storage/files/toc.json)
* [Enforce a minimum required version of Transport Layer Security (TLS) for requests to a storage account](https://docs.microsoft.com/en-us/azure/storage/common/transport-layer-security-configure-minimum-version?toc=%2Fazure%2Fstorage%2Ffiles%2Ftoc.json&tabs=portal)
* [Azure Storage encryption for data at rest](https://docs.microsoft.com/en-us/azure/storage/common/storage-service-encryption?toc=/azure/storage/files/toc.json)
* [Customer-managed keys for Azure Storage encryption](https://docs.microsoft.com/en-us/azure/storage/common/customer-managed-keys-overview?toc=/azure/storage/files/toc.json)

### Best practices

* Since SMB is considered a non-secure protocol, make sure all access to Azure Files services from the on-premises network pass through a secured channel such as a VPN tunnel or an ExpressRoute service.
* To secure access from your VNet to Azure Files, use an Azure private endpoint, which avoids sending network traffic outside your VNet, through a secure channel.
* Remove the need for the use of transport encryption (HTTPS only) for all Azure Files shares.
* For sensitive environments, require a minimum TLS version of 1.2 for Azure Blob storage.
* Deny default network access to the Azure storage account and only allow access from a predefined set of IP addresses.
* For data that you need to retain for long periods (due to regulatory requirements), enable the Azure Files soft delete feature to protect the data from accidental deletion.
* Encrypt data at rest using Azure Key Vault.
* For sensitive environments, encrypt data at rest using customer-managed keys stored inside Azure Key Vault.

## Auditing and monitoring 

Azure allows monitoring Azure Files using Azure Monitor and Advanced Threat Protection for Azure Storage.

* [Requests logged in logging](https://docs.microsoft.com/en-us/azure/storage/common/storage-analytics-logging?toc=/azure/storage/files/toc.json)
* [Monitoring Azure Files](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-monitoring?tabs=azure-portal)

### Best practices

* Enable log alerts using the Azure Monitor service to track access to Azure Files and raise alerts (such as multiple failed access attempts to Azure Files in a short period of time).
* Enable Azure Defender for Storage to receive security alerts inside the Azure Security Center console.
* Enable Azure storage logging to audit all authorization events for access to the Azure storage.

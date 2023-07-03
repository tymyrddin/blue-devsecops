# Virtual Machines

* Use only [trusted images](https://docs.microsoft.com/en-us/azure/virtual-machines/image-builder-overview) when deploying Azure Virtual Machines.
* Use a minimal number of packages inside an image, to lower the attack surface.
* Use Azure built-in agents for Azure Virtual Machines (backup, patch management, hardening, monitoring, and others).
* For highly sensitive environments, use [Azure confidential computing images](https://learn.microsoft.com/en-us/azure/confidential-computing/overview#using-azure-for-cloud-based-confidential-computing-), to ensure security and isolation of customers' data.

## Authenticating to a VM

Microsoft does not have access to customers' VMs. By running the ***create a virtual machine*** wizard you must choose either an existing key pair or create a new key pair. This set of private/public keys is generated at the client side – Azure does not have any access to these keys, and therefore cannot log in to your VM. 

For Linux instances, the key pair is used for [logging in to the machine via the SSH protocol](https://docs.microsoft.com/en-us/azure/virtual-machines/ssh-keys-portal). For [Windows machines](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal#create-virtual-machine), you are asked to specify your own administrator account and password to log in to the machine via the RDP protocol.

### Best practices

* Keep credentials in a secured location.
* Avoid storing private keys on a [bastion host](https://azure.microsoft.com/en-us/services/azure-bastion) (VMs directly exposed to the internet).
* [Join Windows](https://docs.microsoft.com/en-us/azure/active-directory-domain-services/join-windows-vm-template) or [join Linux](https://docs.microsoft.com/en-us/azure/active-directory-domain-services/join-rhel-linux-vm) instances to an AD domain and use your AD credentials to log in to the VMs (avoiding using local credentials or SSH keys completely).

## Network access to a VM

Access to Azure resources and services such as VMs is controlled via [network security groups](https://docs.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview), which are equivalent to the on-premises layer 4 network firewall or access control mechanism. [Filter network traffic with a network security group using the Azure portal](https://learn.microsoft.com/en-us/azure/virtual-network/tutorial-filter-network-traffic).

### Best practices

* For remote access protocols (SSH/RDP), limit the source IP (or CIDR) to well-known addresses. Good alternatives for allowing remote access protocols to an Azure VM is to use a VPN tunnel, use [Azure Bastion](https://azure.microsoft.com/en-us/services/azure-bastion), or use [Azure Privileged Identity Management (PIM)](https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-configure) to allow just-in-time access to a remote VM.
* For file sharing protocols (CIFS/SMB/FTP), limit the source IP (or CIDR) to well-known addresses.
* Set names for network security groups to allow a better understanding of the security group's purpose.
* Use tagging (that is, labeling) for network security groups to allow a better understanding of which network security group belongs to which Azure resources.
* Limit the number of ports allowed in a network security group to the minimum required ports for allowing a service or application to function. 

## Serial console connection

For troubleshooting purposes, you can connect using a serial console ([Azure Serial Console for Linux](https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-machines/serial-console-linux) and [Azure serial console for Windows](https://docs.microsoft.com/en-us/troubleshoot/azure/virtual-machines/serial-console-windows)) to resolve network or operating system problems when SSH or RDP connections are not available. The following commands use the Azure CLI tool to allow serial access for the entire Azure subscription level:

```text
subscriptionId=$(az account show --output=json | jq -r .id)

az resource invoke-action --action enableConsole \
    --ids "/subscriptions/$subscriptionId/providers/Microsoft.SerialConsole/consoleServices/default" --api-version="2018-05-01"
```

This exposes the VM instance. 

### Best practices

* Access to the serial console should be limited to the group of individuals with the Virtual Machine Contributor role for the VM and the Boot diagnostics storage account.
* Always set a user password on the target VM before allowing access to the serial console.

## Patch management

To deploy security patches for either Windows or Linux-based instances in a standard manner, it is recommended to use [Azure Automation Update Management](https://docs.microsoft.com/en-us/azure/architecture/hybrid/azure-update-mgmt):

1. Create an automation account.
2. Enable [Update Management for all Windows and Linux machines](https://docs.microsoft.com/en-us/azure/automation/update-management/manage-updates-for-vm).
3. Configure the schedule settings and reboot options.
4. Install missing security patches on your VMs.
5. Review the deployment status.

### Best practices

* Use [minimal privileges for the account using Update Management](https://docs.microsoft.com/en-us/azure/automation/automation-role-based-access-control#update-management-permissions) to deploy security patches.
* Use update classifications to define which security patches to deploy.
* When using an Azure Automation account, encrypt sensitive data (such as variable assets).
* When using an Azure Automation account, use private endpoints to disable public network access.
* Use tagging (that is, labeling) for your VMs to allow defining dynamic groups of VMs (for example, prod versus dev environments).
* For stateless VMs (where no user session data is stored inside an Azure VM), replace an existing Azure VM with a new instance, created from an up-to-date operating system image.

## Backups

The [Azure Backup service](https://learn.microsoft.com/en-us/azure/backup/backup-azure-security-feature) encrypts backups in transit and at rest using Azure Key Vault.

### Best practices

* Use [Azure role-based access control (RBAC)](https://docs.microsoft.com/en-us/azure/backup/backup-rbac-rs-vault) to configure Azure Backup to have minimal access to your backups.
* For sensitive environments, encrypt data at rest using customer-managed keys.
* Use private endpoints to secure access between your data and the recovery service vault.
* If you need your backups to be compliant with a regulatory standard, use [Regulatory Compliance in Azure Policy](https://docs.microsoft.com/en-us/azure/backup/security-controls-policy).
* Use Azure security baselines for Azure Backup (Azure Security Benchmark).
* Enable the [soft delete feature](https://docs.microsoft.com/en-us/azure/backup/backup-azure-security-feature-cloud) to protect your backups from accidental deletion.
* Consider [replicating your backups to another region](https://azure.microsoft.com/en-us/blog/cross-region-restore-crr-for-azure-virtual-machines-using-azure-backup/).

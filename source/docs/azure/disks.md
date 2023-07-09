# Managed disks

Azure-managed disks are Azure managed block level storage. It is common when working with VMs, to attach an additional volume to store data (separately from the operating system volume). This is also known as block storage.

To encrypt a specific VM, in a specific resource group, using a unique customer key vault:

```text
az vm encryption enable -g MyResourceGroup --name MyVM --disk-
encryption-keyvault myKV
```

To show the encryption status of a specific VM in a specific resource group:

    az vm encryption show --name "myVM" -g "MyResourceGroup"

## Best practices

* Create encryption keys (inside the Azure Key Vault service) for each region you are planning to deploy VMs in.
* For Windows machines, encrypt your data using BitLocker technology.
* For Linux machines, encrypt your data using dm-crypt technology.
* Encrypt both the OS and data volumes.
* Encrypt each data volume at creation time.
* Encrypt the VM snapshots.
* Use an Azure private link service to restrict the export and import of managed disks to the Azure network.
* For highly sensitive environments, encrypt data volumes using a CMK.
* Set names for the Azure disk volumes to allow a better understanding of which disk volume belongs to which VM.
* Use tagging (labelling) for disk volumes to allow a better understanding of which disk volume belongs to which VM.

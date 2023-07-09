# Container Storage Interface (CSI)

Azure Kubernetes Service (AKS) has a CSI driver for the following storage types:

* Block storage: Azure Disk
* Managed SMB and NFS: Azure Files

## Best practices

* Always use the latest CSI version for your chosen storage type.
* Use Azure Key Vault with the secret store CSI driver to store and retrieve secrets (such as tokens, SSH authentication keys, Docker configuration files, and more) to/from AKS pods.
* Use a private endpoint to connect your AKS cluster to Azure Files.
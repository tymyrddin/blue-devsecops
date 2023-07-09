# Container Storage Interface (CSI)

Google Kubernetes Engine has a CSI driver for the following storage types:

* Block storage: Google Compute Engine Persistent Disk
* Object storage: Google Cloud Storage
* Managed NFS: Google Cloud Filestore

## Best practices

* Always use the latest CSI version for your chosen storage type.
* When using the CSI driver for Google Persistent Disk, specify (in the YAML file) the disk-encryption-kms-key key to allow the CSI driver to use a customer-managed encryption key from Google Cloud KMS.
* Use Cloud IAM roles to restrict access from your GKE cluster to Google Cloud Filestore.
* Use Google Secret Manager with the Secret Store CSI driver to store and retrieve secrets (such as tokens, SSH authentication keys, Docker configuration files, and more) to/from your GKE pods.
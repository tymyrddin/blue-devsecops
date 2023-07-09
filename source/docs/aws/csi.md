# Container Storage Interface (CSI)

Amazon Elastic Kubernetes Service (EKS) has a CSI driver for the following storage types:

* Block storage: EBS
* Managed NFS: EFS
* Parallel filesystem (for HPC workloads): Amazon FSx for Lustre

## Best practices

* When creating an IAM policy to connect to a CSI driver, specify the storage resource name instead of using wildcard.
* Use IAM roles for service accounts to restrict access to your pod.
* Always use the latest CSI version for your chosen storage type.
* When using the CSI driver for EBS and its snapshots, always set (in the YAML configuration file) the value of encrypted to True and specify the Amazon KMS key ID (KmsKeyId). This allows the CSI driver to use a key from Amazon KMS.
* When using the CSI driver for EFS, always set (in the YAML configuration file) the value of encryptInTransit to True.
* Use Amazon Secrets Manager with the secret store CSI driver to store and retrieve secrets (such as tokens, SSH authentication keys, Docker configuration files, and more) to/from your EKS pods.

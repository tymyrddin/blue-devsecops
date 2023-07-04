# Compute Engine (GCE) and VM instances

* Use only [trusted images](https://cloud.google.com/compute/docs/images) when deploying Google VMs.
* Use a minimal number of packages inside an image, to lower the attack surface.
* Use GCP built-in agents for Google VMs (patch management, hardening, monitoring, and so on).
* For highly sensitive environments, use [Google Confidential Computing images](https://cloud.google.com/confidential-computing), to ensure security and isolation of customers' data.

## Authenticating to a VM instance

Google does not have access to customers' VM instances. When you run the ***create instance*** wizard, no credentials are generated.

For Linux instances, you can [choose from several access methods](https://cloud.google.com/compute/docs/instances/access-overview). Windows virtual machine (VM) instances [authenticate by using a username and a password instead of by using SSH](https://cloud.google.com/compute/docs/instances/windows/generating-credentials). You can [enable SSH](https://cloud.google.com/compute/docs/connect/windows-ssh). 

### Best practices

* Keep private keys in a secured location.
* Avoid storing private keys on a bastion host (machine instances directly exposed to the internet).
* Periodically rotate SSH keys used to access compute instances.
* Periodically review public keys inside the compute instance or GCP project-level SSH key metadata and remove unneeded public keys.
* [Join Windows](https://cloud.google.com/managed-microsoft-ad/docs/quickstart-domain-join-windows) or [join Linux](https://cloud.google.com/managed-microsoft-ad/docs/quickstart-domain-join-linux) instances to an AD domain and use your AD credentials to log in to the VMs (and avoid using local credentials or SSH keys completely).

## Network access to a VM instance

Access to GCP resources and services such as VM instances is controlled via [VPC firewall rules](https://cloud.google.com/architecture/best-practices-vpc-design#fewer-firewall-rules), which are equivalent to the on-premises layer 4 network firewall or access control mechanism.

### Best practices

* For remote access protocols (SSH/RDP), limit the source IP (or CIDR) to well-known addresses.
* For file sharing protocols (CIFS/SMB/FTP), limit the source IP (or CIDR) to well-known addresses.
* Set names and descriptions for firewall rules to allow a better understanding of the security group's purpose.
* Use tagging (labelling) for firewall rules to allow a better understanding of which firewall rule belongs to which GCP resources.
* Limit the number of ports allowed in a firewall rule to the minimum required ports for allowing your service or application to function.

## Serial console connection

For troubleshooting purposes, you can [connect using a serial console](https://cloud.google.com/compute/docs/troubleshooting/troubleshooting-using-serial-console) to resolve network or operating system problems when SSH or RDP connections are not available. To allow serial access on the entire GCP project (using the Google Cloud SDK):

```text
gcloud compute project-info add-metadata \
    --metadata serial-port-enable=TRUE
```

This exposes the VM instance. 

### Best practices

* Configure password-based login to allow users access to the serial console.
* Disable interactive serial console login per compute instance when not required.
* Enable disconnection when the serial console connection is idle.
* Access to the serial console should be limited to the required group of individuals using Google Cloud IAM roles.
* Always set a user password on the target VM instance before allowing access to the serial console.

## Patch management

To deploy security patches for either Windows- or Linux-based instances, in a standard manner, it is recommended to use [Google operating system patch management](https://cloud.google.com/compute/docs/os-patch-management):

1. Deploy the operating system config agent on the target instances.
2. [Create a patch job](https://cloud.google.com/compute/docs/os-patch-management/create-patch-job).
3. Run patch deployment.
4. Schedule patch deployment.
5. Review the deployment status inside the operating system patch management dashboard.

### Best practices

* Use minimal privileges for the accounts using operating system patch management to deploy security patches, according to Google Cloud IAM roles.
* [Gradually deploy security patches zone by zone and region by region](https://cloud.google.com/blog/products/management-tools/best-practices-for-os-patch-management-on-compute-engine).
* Use tagging (labeling) for VM instances to allow defining groups of VM instances (for example, production versus development environments).
* For stateless VMs (where no user session data is stored inside a Google VM), replace an existing Google VM with a new instance, created from an up-to-date operating system image.



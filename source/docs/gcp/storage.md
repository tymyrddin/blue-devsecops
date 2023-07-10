# Storage

Google Cloud Storage is the GCP object storage service.

## Authentication and authorisation

Access can be controlled at the entire bucket level (including all objects inside this bucket) or on a specific object level (for example, suppose you would like to share a specific file with several of your colleagues).

* [Identity and Access Management](https://cloud.google.com/storage/docs/access-control/iam)
* [Cloud Storage authentication](https://cloud.google.com/storage/docs/authentication)
* [Access control lists (ACLs)](https://cloud.google.com/storage/docs/access-control/lists)
* [Retention policies and retention policy locks](https://cloud.google.com/storage/docs/bucket-lock)
* [Security Token Service API](https://cloud.google.com/iam/docs/reference/sts/rest)
* [HMAC keys](https://cloud.google.com/storage/docs/authentication/hmackeys)
* [Signed URLs](https://cloud.google.com/storage/docs/access-control/signed-urls)
* [4 best practices for ensuring privacy and security of your data in Cloud Storage](https://cloud.google.com/blog/products/storage-data-transfer/google-cloud-storage-best-practices-to-help-ensure-data-privacy-and-security)

### Best practices

* Create an IAM group, add users to the IAM group, and then grant the required permissions on the target cloud storage bucket to the target IAM group.
* Use IAM policies for applications that require access to cloud storage buckets.
* Grant minimal permissions to cloud storage buckets.
* Use Security Token Service (STS) to allow temporary access to cloud storage.
* Use HMAC keys to allow the service account temporary access to cloud storage.
* Use signed URLs to allow an external user temporary access to cloud storage.
* For data that you need to retain for long periods (due to regulatory requirements), use the bucket lock feature to protect the data from accidental deletion.

## Network access

Because Google Cloud Storage is a managed service, it is located outside the customer's VPC. It is important to protect access to Google Cloud Storage.

* [Security, ACLs, and access control](https://cloud.google.com/storage/docs/best-practices#security)
* [The security benefits of VPC Service Controls](https://cloud.google.com/vpc-service-controls/docs/overview)
* [Enabling VPC accessible services](https://cloud.google.com/vpc-service-controls/docs/manage-service-perimeters#add_a_service_to_the_vpc_accessible_services)
* [Customer-supplied encryption keys](https://cloud.google.com/storage/docs/encryption/customer-supplied-keys)
* [Customer-managed encryption keys](https://cloud.google.com/storage/docs/encryption/customer-managed-keys)

### Best practices

* Use TLS for transport encryption (HTTPS only).
* Keep all cloud storage buckets (all tiers) private.
* Use VPC Service Controls to allow access from your VPC to Google Cloud Storage.
* Encrypt cloud storage buckets using Google-managed encryption keys inside Google Cloud KMS.
* For sensitive environments (for example, which contain PII, credit card information, healthcare data, and more), encrypt cloud storage buckets using a CMK inside Google Cloud KMS.

## Auditing and monitoring

GCP allows you to enable logging and auditing using Google Cloud Audit Logs.

* [Cloud Audit Logs with Cloud Storage](https://cloud.google.com/storage/docs/audit-logging)
* [Usage logs & storage logs](https://cloud.google.com/storage/docs/access-logs)

### Best practices

* Admin activity audit logs are enabled by default and cannot be disabled.
* Explicitly enable Data Access audit logs to log activities performed on Google Cloud Storage.
* Limit the access to audit logs to a minimum number of employees to avoid possible deletion or any changes made to the audit logs.

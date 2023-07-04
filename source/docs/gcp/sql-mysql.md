# SQL for MySQL

## Configuring IAM

MySQL supports the following types of authentication methods:

* Local username/password authentication against the MySQL [built-in authentication mechanism](https://cloud.google.com/sql/docs/mysql/create-manage-users).
* [Google Cloud IAM authentication](https://cloud.google.com/sql/docs/mysql/roles-and-permissions).

### Best practices

* For the local MySQL default user, create a strong and complex password, and keep the password in a secured location.
* For end users who need direct access to the managed database, the preferred method is to use Google Cloud IAM authentication.

## Network access

Access to a managed MySQL database service is controlled via one of the following options:

* [Authorized networks](https://cloud.google.com/sql/docs/mysql/authorize-networks): Allows you to configure which IP addresses (or CIDR) are allowed to access your managed MySQL database.
* [Cloud SQL Auth proxy](https://cloud.google.com/sql/docs/mysql/connect-admin-proxy): Client installed on your application side, which handles authentication to the Cloud SQL for MySQL database in a secure and encrypted tunnel.

### Best practices

* Managed databases must never be accessible from the internet or a publicly accessible subnet – always use private subnets to deploy your databases.
* If possible, the preferred option is to use the [Cloud SQL Auth proxy](https://cloud.google.com/sql/docs/mysql/connect-admin-proxy).
* Configure authorized networks for your web or application servers to allow access to your Cloud SQL for MySQL.
* If you need to manage the MySQL database service, use either a GCE VM instance to manage the MySQL database remotely or a [Cloud VPN](https://cloud.google.com/network-connectivity/docs/vpn/concepts/overview) (configures an IPSec tunnel to a VPN gateway device).

## Stored data

To protect customers' data, encrypt data both in transport and at rest.

### Best practices

* [Enforce TLS 1.2](https://cloud.google.com/sql/docs/mysql/configure-ssl-instance#enforce-ssl) transport layer encryption on your database.
* For sensitive environments, encrypt data at rest using [customer-managed encryption keys (CMEKs)](https://cloud.google.com/sql/docs/mysql/cmek) stored inside the Google Cloud KMS service.
* When [using CMEKs](https://cloud.google.com/sql/docs/mysql/configure-cmek46), create a dedicated service account, and grant permission to the customers to access the encryption keys inside Google Cloud KMS.
* Enable auditing on all activities related to encryption keys.

## Conducting auditing and monitoring

As with any other managed service, GCP allows for logging and auditing using [Google Cloud Audit Logs](https://cloud.google.com/logging/docs/audit).

### Best practices

* [Admin activity audit logs](https://cloud.google.com/sql/docs/mysql/audit-logging) are enabled by default and cannot be disabled.
* Explicitly enable [data access audit logs](https://cloud.google.com/logging/docs/audit/configure-data-access) to log activities performed on the database.
* [Limit the access to audit logs](https://cloud.google.com/logging/docs/access-control#permissions_and_roles) to the minimum number of employees to avoid possible deletion or changes to the audit logs.

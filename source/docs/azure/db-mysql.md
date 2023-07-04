# Database for MySQL

## Configuring IAM

MySQL supports the following types of [authentication](https://docs.microsoft.com/en-us/azure/mysql/concepts-azure-ad-authentication) methods:

* Local username/password authentication against the MySQL built-in authentication mechanism
* Azure AD authentication

### Best practices

* For the local MySQL default user, create a strong and complex password, and keep the password in a secured location.
* For end users who need direct access to the managed database, the preferred method is to use [Azure AD authentication](https://docs.microsoft.com/en-us/azure/mysql/howto-configure-sign-in-azure-ad-authentication).

## Network access to a managed MySQL

Access to a managed MySQL database service is controlled via [firewall rules](https://docs.microsoft.com/en-us/azure/mysql/concepts-firewall-rules), which allows you to configure which IP addresses (or CIDR) are allowed to access your managed MySQL database.

### Best practices

* Managed databases must never be accessible from the internet or a publicly accessible subnet – always use private subnets to deploy your databases.
* Configure the start IP and end IP of your web or application servers, to limit access to the managed database.
* If you need to manage the MySQL database service, either use an Azure VM (or bastion host) to manage the MySQL database remotely or create a VPN tunnel from your remote machine to the managed MySQL database.
* Since Azure Database for MySQL is a managed service, it is located outside the customer's virtual network (VNet). An alternative to secure access from your VNet to Azure Database for MySQL is to use a [VNet service endpoint](https://docs.microsoft.com/en-us/azure/mysql/concepts-data-access-and-security-vnet), which avoids sending network traffic outside your VNet, through a secure channel.

## Stored data 

To protect customers' data, encrypt data both in transport and at rest.

### Best practices

* [Security baseline](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/mysql-security-baseline).
* Enable TLS 1.2 transport layer encryption to your database.
* For sensitive environments, [encrypt data at rest using customer-managed keys](https://docs.microsoft.com/en-us/azure/mysql/concepts-data-encryption-mysql) stored inside the Azure Key Vault service.
* Keep your customer-managed keys in a secured location for backup purposes.
* Enable the soft delete and purge protection features on Azure Key Vault to avoid accidental key deletion (which will harm your ability to access your encrypted data).
* Enable auditing on all activities related to encryption keys.

## Conducting auditing and monitoring

As with any other managed service, Azure allows for logging and auditing using built-in services:

* Built-in Azure Database for MySQL audit logs
* Azure Monitor logs

### Best practices

* Enable [audit logs for MySQL](https://docs.microsoft.com/en-us/azure/mysql/concepts-audit-logs).
* [Configure and access audit logs for Azure Database for MySQL in the Azure portal](https://docs.microsoft.com/en-us/azure/mysql/howto-configure-audit-logs-portal).
* Use the [Azure Monitor service to detect failed connections](https://azure.microsoft.com/en-us/blog/best-practices-for-alerting-on-metrics-with-azure-database-for-mysql-monitoring/).
* [Limit access to the Azure Monitor service data](https://docs.microsoft.com/en-us/azure/azure-monitor/roles-permissions-security#security-considerations-for-monitoring-data) to the minimum number of people to avoid possible deletion or changes to the audit logs.
* Use Advanced Threat Protection for Azure Database for MySQL to detect anomalies or unusual activity in the MySQL database.

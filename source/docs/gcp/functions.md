# Functions

Google Cloud Functions is the GCP function as a service. It can integrate with other GCP services, such as Google Cloud IAM for managing permissions to Google Cloud Functions, Google Cloud Audit Logs for monitoring Google Cloud Functions, and Google Cloud Storage for persistent storage.

## Configuring IAM

Google Cloud IAM is the supported service for managing permissions on Google Cloud Functions.

* [Authorizing access via IAM](https://cloud.google.com/functions/docs/securing/managing-access-iam)
* [Authenticating for invocation](https://cloud.google.com/functions/docs/securing/authenticating)
* [Securing access with identity](https://cloud.google.com/functions/docs/securing#identity)

### Best practices

* Use Google Cloud IAM to manage permissions to your Google Cloud functions.
* Grant minimal permissions for accessing and managing the Google Cloud IAM service.
* Create a unique service account for each newly created Google Cloud function with minimal permissions using the Google Cloud IAM service.

## Data and network access

Google Cloud Functions can access resources in your GCP project => it is important to plan before deploying an Google Cloud function.

* [Configuring network settings](https://cloud.google.com/functions/docs/networking/network-settings)
* [Connecting to a VPC network](https://cloud.google.com/functions/docs/networking/connecting-vpc)
* [Configuring serverless VPC access](https://cloud.google.com/vpc/docs/configure-serverless-vpc-access)
* [Using VPC service controls](https://cloud.google.com/functions/docs/securing/using-vpc-service-controls)
* [Managing secrets](https://cloud.google.com/functions/docs/env-var#managing_secrets)

### Best practices

* Use Google Cloud Functions ingress settings to control which IP address (or CIDR) can access your Google Cloud function.
* If you need your Google Cloud function to have access to resources inside your VPC, use serverless VPC access to restrict access to your VPC.
* If your Google Cloud function is connected to your VPC and needs access to external resources, use Google Cloud Functions egress settings to control outbound destinations.
* If your Google Cloud function needs to have direct inbound access from the internet, use VPC service controls as an extra layer of protection to secure your perimeter from data leakage.
* For sensitive environments, encrypt Google Cloud Functions environment variables using CMEK management.
* Use TLS 1.2 to encrypt sensitive data over the network.

## Conducting auditing and monitoring

Google allows you to enable logging and auditing using the Google Cloud Audit Logs service.

* [Using Cloud audit logging with Cloud Functions](https://cloud.google.com/functions/docs/monitoring/audit-logging)

### Best practices

* Admin activity audit logs are enabled by default and cannot be disabled.
* Explicitly enable data access audit logs to log activities performed on the database.
* Limit the access to audit logs to the minimum number of employees to avoid possible deletion or changes to the audit logs.

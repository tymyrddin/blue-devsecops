# Filestore

Google Filestore is a GCP file storage service based on the NFS protocol.

## Authentication and authorisation

Google Cloud IAM is the supported service in which to manage permissions to access Google Filestore.

* [Security for server client libraries](https://cloud.google.com/firestore/docs/security/iam)
* [Get started with Cloud Firestore Security Rules](https://firebase.google.com/docs/firestore/security/get-started)
* [Writing conditions for Cloud Firestore Security Rules](https://firebase.google.com/docs/firestore/security/rules-conditions)

### Best practices

* Keep your Google Filestore instances private.
* Create an IAM group, add users to the IAM group, and then grant the required permissions on the target Google Filestore instance to the target IAM group.
* Use IAM roles to configure minimal permissions to any Google Filestore instance.
* Use Cloud Firestore Security Rules to allow mobile clients, web clients, or serverless authentication to Google Filestore.

## Network access

Google Filestore is a managed service, and is located outside the customer's VPC. Protect access to Google Filestore.

* [Architecture](https://cloud.google.com/filestore/docs/architecture)
* [Access Control](https://cloud.google.com/filestore/docs/access-control)
* [Configuring IP-based access control](https://cloud.google.com/filestore/docs/creating-instances#configuring_ip-based_access_control)
* [Configuring Firewall Rules](https://cloud.google.com/filestore/docs/configuring-firewall)

### Best practices

* Use IP-based access control to restrict access to Google Filestore.
* Create a Google Filestore instance on the same VPC as your clients.
* If the Google Filestore instance is located outside your VPC, use VPC firewall rules to restrict access between your VPC and Google Filestore.

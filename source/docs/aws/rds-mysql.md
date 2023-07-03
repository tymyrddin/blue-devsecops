# RDS for MySQL

## Configuring IAM for a managed MySQL database service

MySQL supports the following types of authentication methods:

* Local username/password authentication against MySQL's built-in authentication mechanism.
* AWS IAM database authentication.
* AWS Directory Service for Microsoft AD authentication.

### Best practices

* For the local MySQL master user, create a strong and complex password (at least 15 characters, made up of lowercase and uppercase letters, numbers, and special characters), and keep the password in a secured location.
* For end users who need direct access to the managed database, the preferred method is to use the AWS IAM service.
* If you manage your user identities using AWS Directory Service for Microsoft AD (AWS-managed Microsoft AD), use this service to authenticate end users using the [Kerberos protocol](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/mysql-kerberos.html).

## Securing network access to a managed MySQL database service


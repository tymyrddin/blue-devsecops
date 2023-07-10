# Google Cloud IAM

## Google Cloud IAM terminology

* Member: This is a Google account (for example, a user), a service account (for
applications and virtual machines), or Cloud Identity with access to GCP resources.
* User: This is a person or application (a service account) with permissions to access
GCP resources. A user has credentials (such as a password and MFA).
* Group: This is a group of users to make the permissions management task easier.
* Role: This refers to a collection of permissions to access resources.
* Service account: This is a special type of IAM user to allow applications access
to resources.
* IAM policy: This is a JSON-based definition that sets the permissions for accessing GCP resources.

## GCP policy evaluation

* No organization policy set: The default access to resources is enforced.
* Inheritance: If a resource node has set inheritFromParent = true, then the effective policy of the parent resource is inherited.
* Disallow inheritance: If a resource hierarchy node has a policy that includes inheritFromParent = false, it doesn't inherit the organization policy from its parent.
* Reconciling policy conflicts: By default, policies are inherited and merged; but DENY values always take precedence.

## Best practices securing cloud IAM

* Use Google Workspace to create and manage user accounts.
* Configure a password policy (which includes the minimum and maximum password
age, the minimum password length, and enforces the use of password history and
complex passwords) from within your Google Workspace admin console.
* Enable MFA for any user with high privileges in your Google Cloud (such as the
GCP project owner role).
* Create IAM groups, assign permissions to the groups, and add users to those groups
for easier account and permission management.
* Use service accounts to grant applications minimal access to Google Cloud resources.
* Create a dedicated service account for each application.
* For scenarios where you only need an application to access resources for a short
amount of time, use short-lived service account credentials.
* Disable unused service accounts.
* Use Google Managed Service accounts for services (such as Google Compute
Engine) that require access to Google resources (such as Google Cloud Storage).
* Use role recommendations using IAM Recommender to enforce minimal
permissions to Google resources.
* Limit the use of service account keys, or avoid them completely, to avoid having to
expose access to your Google Cloud resources from outside your GCP environment.
* Use IAM conditions to enforce the location from which a user can access resources
in your Google Cloud environment (such as your office network).
* Use the policy simulator to determine the effect of a policy on your users.

## Best practices auditing cloud IAM

* Enable Cloud IAM audit logs for further log analysis, such as tracking failed Active
Directory logins.
* Admin activity audit logs are enabled by default and cannot be disabled.
* Explicitly enable Data access audit logs to log activities performed on Google
Cloud IAM.
* Limit the level of access to the audit logs to a minimum number of employees, to
avoid possible deletion or changes to the audit logs using IAM roles.
* Use Policy Analyzer to determine which identity (for example, a user or a service
account) has access to which Google Cloud resource and the type of access.
* Use service account insights to identify unused service accounts and service
account keys.


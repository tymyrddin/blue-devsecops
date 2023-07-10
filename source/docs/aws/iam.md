# AWS IAM

## AWS IAM terminology:
* IAM user: This is a person or application with permission to access AWS resources.
An IAM user has credentials (such as a password, access keys, and MFA).
* IAM group: This refers to a group of IAM users to make the permissions
management task easier.
* IAM role: This indicates an identity that has permission to access resources without
any credentials. Usually, you assign an IAM role to an IAM group, IAM user, or a
service account that requires temporary permissions.
* Service account: This refers to a special type of IAM user, and its purpose is to
allow applications to have access to resources.
* IAM policy: This is a JSON-based definition that sets the permissions for accessing
AWS resources. There are two types of IAM policies:
    * Identity-based policies: This is attached to a user, group, or role.
    * Resource-based policies: This is attached to the AWS resource (for example, the
Amazon S3 bucket).
* Identity provider: This refers to the ability to manage identities outside of AWS
while still being able to grant access to AWS resources to the external identities
(such as a federation between AWS and Azure AD).

## AWS IAM policy evaluation logic

* Identity-based policies with resource-based policies: The result of both policies is the total permissions for both policies.
* Identity-based policies with permissions boundaries: The result of identity-based policies with the restrictions from permissions boundaries becomes the effective permissions.
* Identity-based policies with AWS Organizations service control policies: The result of both policies (for the account member of the organization) becomes the effective permissions.

## Best practices securing AWS IAM

* Disable and remove all access keys and secret access keys from the AWS account
root user.
* Configure a strong password for the AWS account root user.
* Enable MFA for the AWS account root user.
* Avoid using the AWS account root user. Instead, create a random password for the
AWS root account, and in the rare scenarios where a root account is required, reset
the root account password.
* Create an IAM user with a full IAM admin role to only the AWS console, to manage
the AWS account.
* Enable MFA for any IAM user with a full IAM admin role.
* Avoid creating access keys and secret access keys for an IAM user with a full IAM
admin role.
* Create IAM users with IAM policies according to the principle of least privilege.
* Create IAM groups, assign permissions to the groups, and add IAM users to those
groups for easier account and permission management.
* For limited user access, create custom-managed policies and assign the custom
policies to a group of users.
* Configure a password policy (which includes the minimum and maximum
password age, the minimum password length, and enforces the use of password
history and complex passwords).
* Use IAM roles to allow applications that are deploying on EC2 instances access to
AWS resources.
* Use IAM roles instead of creating access keys and secret access keys to allow
temporary access to resources rather than permanent access.
* Avoid embedding access keys and secret access keys inside your code. Instead, use
secret management solutions such as AWS Secrets Manager to store and retrieve
access keys.
* Rotate access keys periodically to avoid key abuse by malicious internal or
external users.
* For highly sensitive environments or resources, set an IAM policy to restrict access
based on conditions such as data, time, MFA, and more.
* For highly sensitive environments or resources, set an IAM policy to only allow
access to users with MFA enabled.
* Use the AWS IAM AssumeRole capability to switch between multiple AWS
accounts using the same IAM identity.
* Use IAM permissions boundaries to restrict IAM user access to specific
AWS resources.

## Best practices auditing AWS IAM

* Enable AWS CloudTrail on all AWS regions.
* Limit the level of access to the CloudTrail logs to a minimum number of employees
– preferably to those with an AWS management account, outside the scope of
your end users (including outside the scope of your IAM users), to avoid possible
deletion or changes to the audit logs.
* Use Amazon GuardDuty to audit the AWS account root user activity.
* Use AWS CloudTrail to audit IAM user activities.
* Use IAM credential reports to locate users that haven't logged in for a long period
of time.
* Use an IAM policy simulator to check what the effective permissions for a specific
IAM user are (that is, whether they are allowed or denied access to resources).
* Use AWS IAM Access Analyzer to detect unused permissions (from both your AWS
account and cross-accounts) and fine-tune the permissions to your AWS resources.
* Use AWS IAM Access Analyzer to detect secrets that can be accessed from outside
your AWS account and are stored inside the AWS Secrets Manager service.
* Use the IAMCTL tool to compare IAM policies between IAM user accounts to
detect any changes (for example, by comparing template IAM user policies with one
of your other IAM users).



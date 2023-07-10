# Azure AD

Azure AD supports the following types of identity models:
* Cloud-only identity: The user account is created inside the Azure AD tenant and
only exists in the cloud (where access to on-premises is not required).
* Hybrid identity: The user account exists in both the Azure AD tenant and
on-premises.

## Azure AD terminology

• User: This is a person or application with permission to access Azure resources. A
user has credentials (such as a password or MFA).
• Group: This is a group of users to make the permissions management task easier.
• Azure role-based access control (RBAC): This is an authorization system with
built-in permissions to access Azure resources (for example, Owner, Contributor,
Reader, and more).

## Best practices securing Azure AD

• Configure a strong password for the original Azure AD global administrator account.
• Enable MFA for the original Azure AD global administrator account.
• Avoid using the original Azure AD global administrator account – keep the user's
password in a secured location.
• Create an Azure AD user with a global administrator role for the purpose of
managing the Azure AD.
• Enable MFA for any user in your Azure AD (such as a global administrator role).
• Limit the number of global administrators to less than five.
• Use Azure RBAC to grant minimal permissions required for users to be able to
access and use Azure resources.
• Enable the Azure AD Privileged Identity Management (PIM) service in your
Azure AD to control just-in-time access to manage Azure AD resources.
• Create Azure AD groups, assign permissions to the groups, and add users to those
groups for easier account and permission management.
• Configure a password policy (which includes the minimum and maximum
password age, the minimum password length, and enforces the use of password
history and complex passwords).
• Create an emergency account (these are special user accounts that shouldn't be used
daily, have MFA enabled, and are a member of the global administrator role) to
avoid getting locked out of your Azure AD.
• Use a conditional access policy to enforce the use of MFA and enforce the location
from which a global administrator can have access to log in and manage your Azure
AD (such as your office network).

## Best practices auditing Azure AD

• Use Azure AD Identity Protection to detect any potential vulnerability activities of
your Azure AD users and send the audit logs to your SIEM system.
• Use Azure AD reports to detect risky users or risky sign-in events.
• Use Azure AD audit logs to review and detect events in your Azure AD (such as
changes to users or groups, sign-in events, and more).
• Send your Azure AD activity logs to the Azure Monitor service for further analysis.
• Limit the level of access to Azure Monitor service data to a minimum number of
employees, to avoid possible deletion or changes to the audit logs.
• If you use the Azure AD PIM service in your Azure AD, create access reviews to
detect who used PIM to request high privilege to carry out actions.
• For hybrid environments (that is, an on-premises Active Directory connected to
Azure AD), use Microsoft Defender for Identity to detect suspicious activities in
your on-premises Active Directory.




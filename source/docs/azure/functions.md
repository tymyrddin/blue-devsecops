# Functions

Azure Functions is the Azure function as a service. It can integrate with other Azure services, such as Azure AD for managing permissions to Azure Functions, Azure Monitor Application Insights for monitoring Azure Functions, and Azure Blob storage for persistent storage.

## Configuring IAM

Azure AD is the supported service for managing permissions to your Azure Functions.

* [How to use managed identities for App Service and Azure Functions](https://docs.microsoft.com/en-us/azure/app-service/overview-managed-identity?toc=/azure/azure-functions/toc.json)
* [Azure Functions authorisations](https://docs.microsoft.com/en-us/azure/api-management/import-function-app-as-api#authorization)
* [Use Key Vault references for App Service and Azure Functions](https://docs.microsoft.com/en-us/azure/app-service/app-service-key-vault-references)

### Best practices

* Enable Azure AD authentication for any newly created Azure function by turning on Azure App Service authentication.
* Avoid allowing anonymous access to your Azure function – require clients to authenticate before using Azure Functions.
* Grant minimal permissions for any newly created Azure function using Azure RBAC.
* Prefer to use temporary credentials to your Azure function – use Shared Access Signature (SAS) tokens to achieve this task.
* Where possible, prefer to use client certificates to authenticate clients to your Azure functions.
* To allow your Azure functions access to Azure resources, use a system-assigned managed identity from Azure AD.
* If you need to store sensitive data (such as credentials), use Azure Key Vault.
* For sensitive environments, encrypt the Azure Functions application settings using customer-managed key management inside Azure Key Vault.

## Data and network access

Azure Functions can access resources in your Azure subscription – It is important to plan before deploying an Azure function.

* [Azure Functions networking options](https://docs.microsoft.com/en-us/azure/azure-functions/functions-networking-options)
* [Secure an HTTP endpoint in production](https://docs.microsoft.com/en-us/azure/azure-functions/functions-bindings-http-webhook-trigger?tabs=csharp#secure-an-http-endpoint-in-production)
* [IP address restrictions](https://docs.microsoft.com/en-us/azure/azure-functions/ip-addresses#ip-address-restrictions)
* [Azure Functions and FTP](https://docs.microsoft.com/en-us/azure/azure-functions/functions-deployment-technologies#ftp)
* [Protect your web apps and APIs](https://docs.microsoft.com/en-us/azure/security-center/defender-for-app-service-introduction)

### Best practices

* For better protection of your Azure functions, configure the Azure function behind Azure API Gateway.
* Use TLS 1.2 to encrypt sensitive data over the network.
* Create a separate Azure storage account for any newly created Azure function.
* Use Azure network security groups to block outbound traffic from your Azure functions (when internet access is not required).
* Use the Azure VNet service endpoint to control access to your Azure functions.
* Use Azure App Service static IP restrictions to control access to your Azure functions.
* Use either an Azure App Service Standard plan or an Azure App Service Premium plan to configure network isolations of your Azure functions.
* Use Azure Defender for App Service as an extra layer of protection for your Azure functions that have inbound access from the internet.
* Use Azure Web Application Firewall as an extra layer of protection for your Azure functions that have inbound access from the internet.
* Disable and block the use of the FTP protocol with your Azure functions.

## Conducting auditing and monitoring

Azure allows you to enable logging and auditing using the Azure Monitor service.

* [Logging and threat detection](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/functions-security-baseline#logging-and-threat-detection)
* [Azure security baseline for Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/security-baseline#logging-and-monitoring)

### Best practices

* Use the Azure Monitor service to log authentication-related activities of your Azure functions.
* Use the Security Center threat detection capability (Azure Defender).

## Conducting compliance, configuration change, and secure coding

Serverless, or function as a service, is mainly code running inside a closed, managed environment. As a customer, you cannot control the underlying infrastructure => invest in secure coding to avoid attackers breaking into your application and causing harm that Azure cannot protect against.

* [Azure security baseline for Azure Functions](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/functions-security-baseline)
* [Posture and vulnerability management](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/functions-security-baseline#posture-and-vulnerability-management)
* [OWASP Serverless Top 10](https://owasp.org/www-project-serverless-top-10/)

### Best practices

* Follow the OWASP Serverless Top 10 project documentation when writing your Azure Functions code.
* Use the Azure security baseline for Azure Functions (Azure Security Benchmark).
* Use the Security Center threat detection capability (Azure Defender).

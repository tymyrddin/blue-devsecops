# Container Instances (ACI)

ACI is the Azure-managed container orchestration service. It can integrate with other Azure services, such as Azure Container Registry (ACR) for storing containers, Azure AD for managing permissions to ACI, Azure Files for persistent storage, and Azure Monitor.

## Configuring IAM for ACI

ACI does not have its own authentication mechanism, and it is recommended to use ACR to store container images in a private registry.

* [Authenticate with ACR](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-authentication)
* [ACR roles and permissions](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-roles)
* [Encrypt a registry using a customer-managed key](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-customer-managed-keys)

### Best practices

* Grant minimal permissions for accessing and managing ACR, using Azure RBAC.
* When passing sensitive information (such as credential secrets), make sure the traffic is encrypted in transit through a secure channel (TLS).
* If you need to store sensitive information (such as credentials), store it inside the Azure Key Vault service.
* For sensitive environments, encrypt information (such as credentials) using customer-managed keys, stored inside the Azure Key Vault service.
* Disable the ACR built-in admin user.

## Conducting auditing and monitoring

Azure allows you to enable logging and auditing using Azure Monitor for containers – a service that allows you to log container-related activities and raise an alarm according to predefined thresholds (for example, low memory resources or high CPU, which requires up-scaling the container environment).

* [Container insights overview](https://docs.microsoft.com/en-us/azure/azure-monitor/containers/container-insights-overview)
* [Container monitoring solution in Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/containers/containers)

### Best practices

* Enable audit logging for Azure resources, using Azure Monitor, to log authentication-related activities of your ACR.
* Limit the access to the Azure Monitor logs to the minimum number of employees to avoid possible deletion or changes to the audit logs.

## Enabling compliance

* [Azure security baseline for ACI](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/container-instances-security-baseline)
* [Azure security baseline for ACR](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/container-registry-security-baseline)
Security considerations for ACI](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-image-security)
* [Introduction to private Docker container registries in Azure](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro)

### Best practices

* Use only trusted image containers and store them inside ACR – a private repository for storing your organizational images.
* Integrate ACR with Azure Security Center, to detect non-compliant images (from the CIS standard).
* Build your container images from scratch (to avoid malicious code in preconfigured third-party images).
* Scan your container images for vulnerabilities in libraries and binaries and update your images on a regular basis.

# Kubernetes Service (AKS)

AKS is the Azure-managed Kubernetes orchestration service. It can integrate with other Azure services, such as ACR for storing containers, Azure AD for managing permissions to AKS, Azure Files for persistent storage, and Azure Monitor.

## Configuring IAM

Azure AD is the supported service for managing permissions to access and run containers through Azure AKS.

* [AKS-managed Azure AD integration](https://docs.microsoft.com/en-us/azure/aks/managed-aad)
* [Best practices for authentication and authorisation in AKS](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-identity)

### Best practices

* Enable Azure AD integration for any newly created AKS cluster.
* Grant minimal permissions for accessing and managing AKS, using Azure RBAC.
* Grant minimal permissions for accessing and managing ACR, using Azure RBAC.
* Create a unique service principal for each newly created AKS cluster.
* When passing sensitive information (such as credential secrets), make sure the traffic is encrypted in transit through a secure channel (TLS).
* If you need to store sensitive information (such as credentials), store it inside the Azure Key Vault service.
* For sensitive environments, encrypt information (such as credentials) using customer-managed keys, stored inside the Azure Key Vault service.

## Network access

Azure AKS exposes services to the internet – it is important to plan before deploying an Azure AKS cluster.

* [Best practices for network connectivity and security in AKS](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-network)
* [Best practices for cluster isolation in AKS](https://docs.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-isolation)
* [Create a private AKS cluster](https://docs.microsoft.com/en-us/azure/aks/private-clusters)

### Best practices

* Avoid exposing the AKS cluster control plane (API server) to the public internet – create a private cluster with an internal IP address and use authorised IP ranges to define which IPs can access your API server.
* Use the Azure Firewall service to restrict outbound traffic from AKS cluster nodes to external DNS addresses (for example, software updates from external sources).
* Use TLS 1.2 to control Azure AKS using API calls.
* Use TLS 1.2 when configuring Azure AKS behind Azure Load Balancer.
* Use TLS 1.2 between your AKS control plane and the AKS cluster's nodes.
* For small AKS deployments, use the kubenet plugin to implement network policies and protect the AKS cluster.
* For large production deployments, use the Azure CNI Kubernetes plugin to implement network policies and protect the AKS cluster.
* Use Azure network security groups to block SSH traffic to the AKS cluster nodes, from the AKS subnets only.
* Use network policies to protect the access between the Kubernetes Pods.
* Disable public access to your AKS API server – either use an Azure VM (or Azure Bastion) to manage the AKS cluster remotely or create a VPN tunnel from the remote machine to the AKS cluster.
* Disable or remove the HTTP application routing add-on.
* If you need to store sensitive information (such as credentials), store it inside the Azure Key Vault service.
* For sensitive environments, encrypt information (such as credentials) using customer-managed keys, stored inside the Azure Key Vault service.

## Conducting auditing and monitoring

Azure allows you to enable logging and auditing using Azure Monitor for containers.

* [ACI overview](https://docs.microsoft.com/en-us/azure/azure-monitor/containers/container-insights-overview)
* [Container monitoring solution in Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/containers/containers)

### Best practices

* Enable audit logging for Azure resources, using Azure Monitor, to log authentication-related activities of your ACR.
* Limit the access to the Azure Monitor logs to the minimum number of employees to avoid possible deletion or changes to the audit logs.

## Enabling compliance

* [Introduction to Azure Defender for Kubernetes](https://docs.microsoft.com/en-us/azure/security-center/defender-for-kubernetes-introduction)
* [Use Azure Defender for container registries to scan your images for vulnerabilities](https://docs.microsoft.com/en-us/azure/security-center/defender-for-container-registries-usage)
* [Azure security baseline for ACI](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/container-instances-security-baseline)
* [Azure security baseline for ACR](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/container-registry-security-baseline)
* [Security considerations for ACI](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-image-security)
* [Introduction to private Docker container registries in Azure](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro)

### Best practices

* Use only trusted image containers and store them inside ACR – a private repository for storing your organizational images.
* Use Azure Defender for Kubernetes to protect Kubernetes clusters from vulnerabilities.
* Use Azure Defender for container registries to detect and remediate vulnerabilities in container images.
* Integrated Azure Container Registry with Azure Security Center to detect non-compliant images (from the CIS standard).
* Build your container images from scratch (to avoid malicious code in preconfigured third-party images).
* Scan your container images for vulnerabilities in libraries and binaries and update your images on a regular basis.

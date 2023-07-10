# Kubernetes Engine (GKE)

GKE is the Google-managed Kubernetes orchestration service. It can integrate with other GCP services, such as Google Container Registry for storing containers, Google Cloud IAM for managing permissions to GKE, Google Filestore for persistent storage, and Google Cloud operations for monitoring.

## Configuring IAM

Google Cloud IAM is the supported service for managing permissions to access and run containers through GKE.

* [Creating IAM policies](https://cloud.google.com/kubernetes-engine/docs/how-to/iam)
* [Configuring RBAC](https://cloud.google.com/kubernetes-engine/docs/how-to/role-based-access-control)
* [Enforce least privilege with recommendations](https://cloud.google.com/iam/docs/recommender-overview)
* [Use least privilege Google service accounts](https://cloud.google.com/kubernetes-engine/docs/how-to/hardening-your-cluster#permissions)
* [Secret management](https://cloud.google.com/kubernetes-engine/docs/how-to/hardening-your-cluster#secret_management)

### Best practices

* Grant minimal permissions for accessing and managing the Google Cloud IAM service, using Kubernetes RBAC.
* Use Google Groups to manage permissions to your GKE cluster.
* Use the Google IAM recommender to set the minimal permissions for your GKE cluster.
* Create a unique service account with minimal permissions for any newly created GKE cluster.
* Enforce the use of MFA for any user who needs access to manage your GKE cluster.
* If you need to store sensitive information (such as credentials), store it inside the Google Cloud KMS service.
* For sensitive environments, encrypt information (such as credentials) using CMEKs stored inside the Google Cloud KMS service.

## Network access

GKE exposes services to the internet => it is important to plan before deploying a GKE cluster.

* [Creating a private cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/private-clusters)
* [Restrict network access to the control plane and nodes](https://cloud.google.com/kubernetes-engine/docs/how-to/hardening-your-cluster#restrict_network_access_to_the_control_plane_and_nodes)
* [Restrict traffic among Pods with a network policy](https://cloud.google.com/kubernetes-engine/docs/how-to/hardening-your-cluster#restrict_with_network_policy)
* [Network security](https://cloud.google.com/kubernetes-engine/docs/concepts/security-overview#network_security)
* [Harden workload isolation with a GKE sandbox](https://cloud.google.com/kubernetes-engine/docs/how-to/sandbox-pods)

### Best practices

* Create private GKE clusters to avoid exposing the GKE cluster control plane (API server) to the public internet – use alias IP ranges to configure which IPs can access the GKE cluster.
* Use authorised networks to configure who can access your GKE cluster control plane.
* Use VPC-native networking to protect the access between the Kubernetes Pods.
* Use network policies for Kubernetes to protect the access between the Kubernetes Pods.
* Use shielded GKE nodes as an additional layer of protection to your GKE cluster nodes.
* Create separate namespaces for your applications, according to RBAC requirements.
* Enable a GKE sandbox to achieve better isolation of your GKE cluster Pods.
* Use TLS 1.2 to control your GKE cluster using API calls.
* Use TLS 1.2 between your GKE control plane and the GKE cluster's nodes.
* Use TLS 1.2 when configuring the GKE cluster behind Google Load Balancer.
* Disable public access to your GKE cluster API server – use a Google VM (or a Bastion host) to manage the GKE cluster remotely.

## Conducting auditing and monitoring

Google allows you to enable logging and auditing using the Google Cloud Logging service – a service that allows you to audit container-related activities.

* [Audit policy](https://cloud.google.com/kubernetes-engine/docs/concepts/audit-policy)
* [Overview of Google Cloud's operations suite for GKE](https://cloud.google.com/stackdriver/docs/solutions/gke)
* [Remediating security health analytics findings](https://cloud.google.com/security-command-center/docs/how-to-remediate-security-health-analytics-findings#container_vulnerability_findings)

### Best practices

* Enable logging for any newly created GKE cluster and integrate the item with the Google Cloud Logging service, to log all audit activities related to your GKE cluster.
* When using a container-optimised operating system image, make sure you send its Linux audit logs to the Google Cloud Logging service.
* Limit the access to the Google Cloud Logging service logs to the minimum number of employees to avoid possible deletion or changes to the audit logs.

## Enabling compliance

* [Container threat detection conceptual overview](https://cloud.google.com/security-command-center/docs/concepts-container-threat-detection-overview)
* [GKE CIS 1.1.0 Benchmark Inspec Profile](https://github.com/GoogleCloudPlatform/inspec-gke-cis-benchmark)
* [GKE auditor](https://github.com/google/gke-auditor)
* [Node images](https://cloud.google.com/kubernetes-engine/docs/concepts/node-images#containerd_node_images)
* [Binary authorisation](https://cloud.google.com/binary-authorization)
* [Container Registry](https://cloud.google.com/container-registry)

### Best practices

* Use only trusted image containers and store them inside Google Container Registry – a private repository for storing your organizational images.
* Always use the latest build of Kubernetes on both your GKE cluster and cluster nodes.
* Use the GKE auditor to detect GKE misconfigurations.
* Use container-optimised operating systems when creating new container images, for better security.
* Build your container images from scratch (to avoid malicious code in preconfigured third-party images).
* Scan your container images for vulnerabilities in libraries and binaries and update your images on a regular basis.
* Use Google Binary authorisation to make sure you use only signed container images from trusted authorities.
* Use container threat detection to detect attacks against your container images in real time.

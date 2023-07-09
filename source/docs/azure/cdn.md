# Content delivery network (CDN)

## Best practices

* Restrict access to origin servers (where your original content is stored) from CDN
segments only (allow traffic only from the CDN segments towards servers or
services that store content).
* Prefer sharing content via the HTTPS protocol to preserve the confidentiality of the
content and to ensure the authenticity of the content.
* When distributing content over HTTPS, prefer using TLS 1.2 over older protocols
such as SSL v3.
* Enable Azure CDN logs for audit logging purposes. Forward the logs to Azure
Security Center for further investigation.
* Forward Azure CDN logs to Azure Sentinel (the Azure managed SIEM service) for
threat detection.


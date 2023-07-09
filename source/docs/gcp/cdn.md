# Content delivery network (CDN)

## Best practices

* Restrict access to origin servers (where your original content is stored) from CDN
segments only (allow traffic only from CDN segments towards servers or services
that store content).
* Share content via HTTPS protocol to preserve the confidentiality of the content and
to assure the authenticity of the content.
* When distributing content over HTTPS, use TLS 1.2 over older protocols such as
SSL v3.
* If you have a requirement to distribute content such as individual files for a short
period of time, use signed URLs.
* Enable Google Cloud CDN audit logs to monitor CDN activity.
* Note that admin activity audit logs are enabled by default and cannot be disabled.
* Explicitly enable data access audit logs to log activities in Google Cloud CDN.
* Limit access to audit logs to the minimum number of employees to avoid unwanted
changes to the audit logs.
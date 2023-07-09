# CloudFront

## Best practices

* Restrict access to origin servers (where your original content is stored) from CDN
segments only (allow traffic only from the CDN segments towards servers or
services that store content).
* Share content via the HTTPS protocol to preserve the confidentiality of the content
and to assure the authenticity of the content.
* When distributing content over HTTPS, use TLS 1.2 over older protocols, such as
SSL v3.
* If you have a requirement to distribute private content, use CloudFront
signed URLs.
* If you have a requirement to distribute sensitive content, use field-level encryption
as an extra protection layer.
* Use AWS Web Application Firewall (WAF) to protect content on Amazon
CloudFront from application-layer attacks (such as detecting and blocking bot
traffic, OWASP Top 10 application attacks, and more).
* Enable CloudFront standard logs for audit logging purposes. Store the logs in a
dedicated Amazon S3 bucket, with strict access controls, to avoid log tampering.
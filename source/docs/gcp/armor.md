# Armor

Google Cloud Armor is the Google managed DDoS protection and Web Application Firewall (WAF) service.

It comes in two price models:

* Google Cloud Armor Standard: This provides protection against volumetric DDoS attacks and includes preconfigured WAF rules.
* Managed Protection Plus: This provides protection against volumetric DDoS attacks, includes preconfigured WAF rules, and includes an adaptive protection mechanism. This price tier also offers support from the Google DDoS response team. 

Cloud Armor protects applications located behind an external Google Cloud load balancer, which is based on HTTP/HTTPS and TCP/SSL proxy load balancers.

## Best practices

* Create an IAM group, add users to the group, and grant the required permissions on the Cloud Armor for the target group.
* Note that Cloud Armor contains pre-configured protection rules against common web application attacks.
* If you need to configure your own rules to match your application, create custom Cloud Armor security policies to allow or deny traffic to your applications behind an external Google Cloud load balancer.
* Enable Cloud Armor logs for any backend service to detect allowed or denied HTTP/HTTPS requests.
* For critical production applications, it is recommended to subscribe to the Managed Protection Plus service.
* For critical production applications, it is recommended to enable the Cloud Armor Adaptive Protection Mechanism to detect anomalous activity and generate a custom signature for blocking application attacks using WAF rules (for application attacks).
* For scenarios where you would like to allow access to your production applications for third-party partners without them having to specify their external IP address or IP range, use Cloud Armor named IP address lists to configure a whitelist of allowed sources.
* Use the Google Security Command Center service to detect anomalous behaviour in the Cloud Armor traffic activity (such as spikes in traffic).
# UC4 - Federating API Functionality

This use-case demands federated _serviceability_ at all federated-gateways.

Problem Statement
---
Given: A cluster of two or more federated gateways [_**G1, G2, ..., Gn**_]

When: An API-client tries to consume endpoint **En** hosted by **Gn**, through any gateway in the cluster 

Then: To gain a seamless consumer experience, the client is not redirected, and instead can get the request served through any gateway in the cluster

Sample Business Case
---

1. Org. XYZ has an API-endpoint serving production requests: __/v1/sample-endpoint__
   
   Number of consumers: Being a B2C player, clients are in the high-millions (e.g. an app on mobile devices)
   
2. Org. XYZ now undergoes policy changes that demands a shift away from its existing gateway
   ( for sample reasons: inadequate security-implementation, license-exhaustion, government-policies, etc.)
   
3. A new gateway is introduced to host and manage new APIs, but will be kept federated with the old gateway, until the time a successful migration of all old APIs is done to the new gateway.

4. Either/all of:
- More business features are added to the current mobile-app that use new APIs, but through the old gateway as the app still points there.

- Existing business features don't break if the app is forced to consume old APIs through the new gateway.

5. Org. XYZ carries out a successful migration of all APIs to the new gateway, with zero consumer downtime.

Considerations:
- API policies (for e.g. rate-limiting) at each gateway must still apply when accessing through the federated cluster.

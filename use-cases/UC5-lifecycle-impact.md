# UC5 - Federated Lifecycle Reflection


This use-case demands unanimous life-cycle reflection at all gateways in a federated cluster.

Problem Statement
-----------------

Given: A cluster of federated gateways [_**G1,G2, ..., Gn**_]

When: An API at **_Gn_** undergoes a lifecycle change

Then: The impact of the change is reflected at all gateways in the cluster.


Sample Business Case
--------------------

- Clients use gateway **_G1_** for service discovery, which helps them know about services at **_Gn_**.
- A product-decision deprecates / sunsets the API **sample-api** at **_Gn_**
- Clients can no longer discover **sample-api** through **_G1_**

# UC8 - Propagate End-User identity

This use-case aims at propagating end-user identity 'transparently' between API Gateways.

![propagate-end-user-identity](/media/propagate-end-user-identity.png)   <br>  
<p align="center">
<i>
Propagate End User Identity
<br/>
</i>


Problem Statement
-----------------

Given: Multiple API Gateways [_**G1,G2, ..., Gn**_] are involved in handling a single request from API Consumer  
Given: End-User is involved in the authorization process **_3-Legged OAuth flows like Authorization Code, Implicit etc_**  

When: An API is invoked by API Client 

Then: The front-ending API Gateway does not propagate end-user identity to other participating / downstream API Gateways in a standardized manner, causing additional development effort (managing keys, tokens etc) for every new downstream API Gateway endpoint.


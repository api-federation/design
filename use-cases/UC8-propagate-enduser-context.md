# UC8 - Propagate End-User context

This use-case aims at transparently propagating end-user context between API Gateways.

![propagate-end-user-context](/media/api-federation-runtime-big-picture.png)   <br>  
<p align="center">
<i>
Figure 3 - Propagate End User Identity
<br/>
</i>


Problem Statement
-----------------

Given: Multiple API Gateways [_**G1,G2, ..., Gn**_] are involved in handling a single request from API Consumer  
Given: End-User is involved in the authorization process **_3-Legged OAuth flows like Authorization Code, Implicit etc_**  

When: An API is invoked by API Client

Then: The front-ending API Gateway does not allow automatic propagation of end-user context to other participating / downstream API Gateways, causing additional development effort (managing keys, tokens etc) for every new downstream API Gateway endpoint participating in handling the original request.  

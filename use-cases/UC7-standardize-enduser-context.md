# UC7 - Standardize End-User context

This use-case aims at standardizing generation and transmission of end-user context by API Gateway.


Problem Statement
-----------------

Given: Heterogenous API Gateways [_**G1,G2, ..., Gn**_] are involved   
Given: End-User is involved in the authorization process **_3-Legged OAuth flows like Authorization Code, Implicit etc_**  

When: An API is invoked by API Client  

Then: API Gateways are generating and transmitting the end-user context in a vendor-specific manner, hence reusing it for further downstream invocations is cumbersome and often involves writing additional logic on API Backends.    

# Overview
This repository contains requirements and design documents for API Federation.

API Federation involves creating systems where API consumers and API producers are not directly connected and do not  need to directly trust each other.

The aim of this group is to create vendor-neutral open specifications that enable API federation across two schemes.  


## Designtime Federation  

Allows federation to a heterogenous collection of API Gateways in a uniform manner to discover and gather API Metadata (data about APIs).   

_Typical Use Case: To create a unified marketplace of APIs running on a heterogenous collection of API Gateways._   

![api-federation-design](/media/api-federation-designtime-big-picture.png)  <br>
<p align="center">
<i>
Figure 1 - Designtime Federation / The Big Picture
<br/>
</i>


## Runtime Federation

Allows federation of end-user context at runtime (during API invocation) from the API consumer to heterogenous collection of API Gateways en route.   

_Typical Use Case: API Mashups involving heterogenous API Gateways._  

![api-federation-design](/media/api-federation-runtime-big-picture.png)  <br>
<p align="center">
<i>
Figure 2 - Runtime Federation / The Big Picture
<br/>
</i>

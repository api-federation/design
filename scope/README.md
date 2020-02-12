# Overview
This document describes the scope of the API Federation project.

## Mission Statement
To create a specification that enables creating a unified marketplace of APIs running on a heterogenous collection of API Gateways.

## Scope

The following use cases under In-scope and Out-of-scope are derived from the use cases described in [use-cases](use-cases).
### In-scope
* UC-1 - Building a unified portal (catalogue) of APIs deployed on a heterogeneous collection of API gateway vendors. Subscriptions to any API should be facilitated from the unified portal.
* UC-3 - Industry marketplace. 
    - Yellow pages like functionality where a central entity has a catalogue of all APIs. 
    - Central catalogue of APIs grouped by functionality (tags) to that developers on the portal can easily find APIs related to a particular functionality. 
    - The central entity is capable of managing the developer credentials and application credentials of users and app that consume APIs.
* UC-6 - The ability for an organization to bring its own users. The specification should facilitate a mechanism where developers, by browsing the portal can figure out how they can federate their own IDP or add their users to the pool of approved users to authenticate to an API.


### Out-of-scope
* UC-2 - Having a single publisher to deploy/manage APIs on multiple API gateway vendors. 
    - Many organizations have their own processes (CI/CD) for deploying APIs to gateways. Organizations would prefer to use their own processes and tools for the purpose of deploying and managing APIs instead of buying into a new generic tool.
    - An API consists of policies that need to be deployed on gateways. It would be practically hard to create a generic specification for policies since the polices of various API gateway vendors vary significantly.
* UC-4 - Federating functionality of APIs. Ex: Functionality of a given API are distributed across two or more API gateway vendors. An application would be accessing only one API gateway. Any given gateway should be able to serve all functionalities of an API even though it itself might not be hosting a particular functionality of an API. It should be able to federate itself with whatever the gateway that hosts any missing functionality and serve customer requests.
    - This particular functionality that is expected is more of a gateway runtime requirement than what could be achieved through a specification. And hence considered out-of-scope.
* UC-5 - Reflection of API lifecycle changes across all API gateways.
    - Since UC-2 is out-of-scope, UC-5 too goes out-of-scope since it expects a central management of APIs across heterogenous API gateways. However the fact that an API requires a lifecycle notation in the specification is considered.



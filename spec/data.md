# Overview
This document explains the data to be included in the specification. The specification should be an extension of the Open API Specification. Following would be the data points required to be introduced on top of the Open API Specification for the API Federation specification.

* Service Provider - The specification should include details of the service provider offering the API. Details could be
    - Service provider name - Ex: WSO2 Inc, Apigee - Google Cloud
    - URL of service (already covered in OAS)

* Identity provider of the API - The specification should include details about the Identity provider of the particular API. The details of the identity provider are useful to the central developer portal. Assuming the central portal will be used by developers to consume an API, a developer needs to use the central portal to register application keys (client-id and secret) against the IDP. The developer would also need to information about how to
    - Onboard his/her users to be able to authenticate to the API (bring your own user-store)
    - How a user can obtain a token (already covered in OAS)

* API State - The central portal needs to know the state of an API on a gateway. Some examples of states would be (Under Development, Testing, Live, Deprecated)

* Rate Limits of APIs - Consumers interested in using an API would need to know the rate limits at which they are allowed to consume the API.

* Billing Information - Consumers would want to know the available billing plans for each API.

* Sandbox URL - API consumers would want to test the API for mocked business functionality. For this purpose a sandbox URL should be made available.


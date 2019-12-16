Assume a company/government with different departments that use different API Management solutions (because there was no rule to use a single API Management solution initially or the disparity was the result of a company merger). 
E.g. Department A uses WSO2 API Manager, Department B uses Apigee and Department C uses Kong. 

They want to allow internal and external application developers to discover the APIs via a unified store. This can be looked at in two ways:

- Allow the unified store to only have a listing of all company-wide APIs (like a yellow pages listing). 
- Allow users to also subscribe to the APIs via the unified store. To unify a single portal that can work across multiple gateways of different vendors, a common API format is required - most of this can be achieved with Swagger/OAS 3.0. What is needed is a single point of discovery for APIs.
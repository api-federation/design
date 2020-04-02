# API Federation Specification

## Introduction

The idea of this specification is to come up with a set of standards that should be adhered to by API Gateways that enable building federated Developer Portals for API Users.  
  
The following sections outline the standards that need to adhered to by API gateways to cater different requirements needed by API user portals. Although these sections may mention that these have to be provided by API Gateways themselves, they maybe provided through control/management planes that govern the respective API gateway runtimes.  
  
### 1. Discover service for APIs   
API user portals need to list APIs available on an API Gateways. The following service needs to be available on API gateways to cater this requirement.  
````
GET /apis?
state=<state_filter>&
tenant=<tenant_identifier>&limit=<limit_per_page>&page=<page_number>
````

The 'state', 'tenant', 'limit' and 'page' are optional query parameters that help with filtering APIs to make it easier to filter APIs on a portal.    
  
A request to the above endpoint would result in a response that contains an array of API objects as shown below.  

````
{
	"apis": [{
		"id": "sju8-siu-nju",
		"name": "Foo",
		"version": "v1.0.4",
                "state": "live"
	}]
}
````

### 2. Get API Meta-Data  

To get details of a particular API, the follow resource needs to be made available on the API gateway.  

````
GET /apis/{api_id}
````  
Returns details of a given API identified by the given id. Ex:  

````
{
	"api_id": "sju8-siu-nju",
	"api_name": "Foo",
	"api_version": "v1.0.4",
 	"spec_type": "oas",
	"state": "live",
  	"provider": "Foo Inc.",
  	"provider_contact": "https://foo.com",
	"subscription_policies": ["p1", "p2"],
  	"production_url": "https://example.com/apis/foo",
  	"sandbox_url": "https://test.example.com/apis/foo"
}
````
  
### 3. Get API Specification  
API user portal would require an API specification document such as an OpenAPI document for various purposes such as documentation, SDK, test tools, etc. This needs to be provided by the gateway. The spec type of a given API can be identified by the API details retrieved through the endpoint discussed under (2) above. Example types of specs could be 'oas', 'graphql', 'asyncapi', etc. Following is a structure of an endpoint.  
````
GET /apis/{api_id}/spec/{type}
````

### 4. API Subscription Endpoint  

Whenever an API user subscribes an application to an API on the user portal it needs to notify the gateway regarding the new subscription. This helps API gateways validate requests to check if they are being received by applications that have a valid subscription to use an API. The gateway needs to have a subscription endpoint available to make this possible. Following is its structure.  

````
POST /subscriptions  
api_id  
    REQUIRED - The identifier of the API being subscribed to. 
api_tenant  
    OPTIONAL - For multi tenant API gateways the tenant identifier is used to uniquely identify the API.  
client_identifier  
    REQUIRED - A unique identifier of the client (application) that subscribes to the API.  
subscription_policy_id  
    OPTIONAL - To identify policy under which this subscription is made. Ex p1 (The policy identified by p1 tells the gateway not to allow more than 100 req/sec for this application that subscribed to the API)  
````

On a successful subscription this will result in a 201 success response as shown below  
````
201 Success

Content-Type: application/json

{
  "id": "dhsu72-akk8",
  "api_id": "sje-kas8",
  "api_tenant": "finance",
  "client_identifier": "foo-android",
  "subscription_policy_id": "p1"
}
````  

### 5. Subscription removal endpoint  

When a subscription is removed from a API user portal the gateway needs to be notified through an endpoint which has the following structure.  
````
DELETE /subscriptions/{subscription_id}
````  

Upon successful removal this will return a 200 OK response.  
  
### 6. Discovering policies available for subscriptions  

When an API user subscribes to an API, he/she may be required to subscribe through a selected policy. To cater this requirement the API gateway needs to expose an endpoint that makes it possible for API user portals to discover what type of policies are available for subscription. A policy may be used to represent access quotas and other similar governance rules on using the API. Following is the structure of the endpoint that makes subscription policies discoverable on API gateways.  
````
GET /subscription-policies?tenant=<tenant_identifier>
````  

This would return a list of policies as shown below.  
````
{
	"subs-policies": [{
		"id": "p1",
		"name": "Gold",
		"description": "Allows 1000 request per minute at a charge of 100$ a month"
	}]
}
````
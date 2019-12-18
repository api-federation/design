# Extending OAS Definition to add response cashing for an API

## Metadata

|Tag |Value |
|---- | ---------------- |
|Proposal |[001]()|
|Authors|[Vimukthi Mayadunne](https://github.com/VimukthiMayadunne), [Author 2](https://github.com/{author2})|
|Review Manager |TBD |
|Status |Proposal|



## Change Log

|Date |Responsible Party |Description |
|---- | ---------------- | ---------- |

## Introduction
This  feature can be used to define caching responses received from a backend in the api-gateway. 

## Motivation
This feature will help the API developers to provide the necessary configurations required for apply response chasing functionalities to an api-gateway and to invoke response cashing just by providing that in the swagger/OAS definition   rather than  applying response cashing  to  an API in the gateway via API gateway -UI  (AKA Publisher U.I.) or other methods .This will make response chasing configurations more human readable as well.  

## Proposed solution
Proposed solution is to add an extension to the OAS spec where that extension describes the following attributes

Cache Time out : how long to cache a response




## Detailed design

### Schema
```
x-global-cache: { 
    Data type      : number 
    Required       : true
    Description   :  how long to cache a response
    }
```
Under this schema x-global-cache will has and only one property which will define the  cache time out time if this property is present APi gateway should chase the responses for given amount of time
```
Ex-
x-global-spec:
    x-global-cache:300
```

## Alternatives considered

#### Alternative -1
Alternative schema : Under this If an api developer add the below schema  to an OAS definition under the heading x-global-spec an API-gateway should be able to apply response chasing to that particular API for the given amount of time. In this schema it provides extra clarity to weather to apply or not the response chasing. 

#### Alternative-Schema
```
x-global-spec:
    x-global-cache:
       cacheEnabled : {
            Data type          : boolean    
            Required           : true
            Description        : Weather to enable or disable response caching
            },
        cacheTimeOut : { 
            Data type      : number 
            Required       : true
            Default        : 300
            Description    :  how long to cache a response
            }
```

If an api developer add the above to an OAS definition under the heading x-global-spec an API-gateway should be able to apply response chasing to that particular API for the given amount of time.

Ex:-

```
x-global-spec:
    x-global-cache:
        isEnabled         : true
        cacheTimeOut      : 200
```

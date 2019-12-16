# Extending OAS Definition to add rate limiting for an API


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


# Extending OAS Definition to add rate limiting for an API

###  Introduction

This  feature can be used to define how to limit the  incoming traffic to an api-gateway 

###  Motivation

This feature will help the API developers to provide the necessary configurations required for apply rate-limiting functionalities to api-gateway and this function will help the API developers to apply rate limiting to  an API in the gateway without working to configure it on the API gateway -UI (AKA Publisher U.I.)

###  Proposed solution

Proposed solution is to add an extension to the OAS spec where that extension describes the following attributes 

'Time Interval: What is the time interval to be used'
'Time unit: What is the unit of time used to measure API requests'
'Accepted quota: How many API calls to be accepted'  


###  Detailed design

####   Schema
```
        x-global-rateLimiting:{
             interval : { 
                Data type      : number 
                Required       : false
                Default          : 1
                Description   : time interval
                }, 
             timeunit: {
                Data type           : string    
                Required            : false
                Default               : Seconds
                Description        : time unit  
                allowed values  : year , month , day ,hour, minute , seconds
                },
             quota :{ 
                Data type     :  number 
                Required    :  true
                Description    :  how many requests per the time interval 
                }
            }

```

Rate limiting will be applied in two major levels
  1.API level rate-limiting - Applies to the entire API 
  2.Resource level (operational level) rate-limiting  - Applies to a particular resource of an API

#### API level rate limits
To enable API level rate limits a developer should add the specification under the heading x-global-spec-rateLimiting under the heading x-global-spec if this heading is present API gateway should apply to the entire API as a whole. 

Example:
```
x-global-spec :
      x-global-rateLimiting:
             Interval    : 1
             timeunit   : minute
             quota      : 50000
```

#### Per resource rate limits

To enable rate limits at resource/path levels a user should add the specification under paths of the  OAS definition with the hedding named x-global-spec if  is present a gateway should be able to add totaling at each resource level.
If API level rate limiting is defined this should override that configuration and apply rate-limiting as defined in the resource /path level. 

Example:
```
paths:
    /weather:
        get:
          responses:
               "200":
                     description: weather of The Given City ID
           parameters:
                - name: id
                    in: query
                  required: false
                    description: ID of the City
                    schema:
                type: number
          x-global-spec-rateLimiting  :
                        interval    :  1
                        timeUnit    : hour
                        quota       :  1000
```

#### Special Use cases:

#####  x-global-spec-rateLimiting  not present in niter API level no Resource level
This means API rate-limiting  is disabled and  API-gateway should not add any rate limiting policies to the API it should allow an unlimited amount of
request to pass through the gateway.

#####  x-global-spec-rateLimiting  not present in both  API level and Resource level
In this scenario Resource level definition should supersedes the  API level rate-limiting 

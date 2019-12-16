# Extending OAS Definition to apply  CORS to an API

## Metadata

|Tag |Value |
|---- | ---------------- |
|Proposal |[002]()|
|Authors|[Vimukthi Mayadunne](https://github.com/VimukthiMayadunne), [Author 2](https://github.com/{author2})|
|Review Manager |TBD |
|Status |Proposal|
|Implementations |[Click Here]|
|Issues |[{issueid}]|
|Previous Revisions |[{revid}] |

## Change Log

|Date |Responsible Party |Description |
|---- | ---------------- | ---------- |

## Introduction
This  feature can be used to define caching responses received from a backend in the api-gateway. 

## Motivation
This feature will help the API developers to provide the necessary configurations required for apply CORS-Configuration  to an api-gateway and to invoke response cashing just by providing that in the swagger/OAS definition   rather than  applying response cashing  to  an API in the gateway via API gateway -UI  (AKA Publisher U.I.) or other methods .This will make CORS configurations more human readable as well.  

## Proposed solution
Proposed solution is to add an extension to the OAS spec where that extension describes the following attributes 
```
corsConfigurationEnabled
accessControlAllowOrigins
accessControlAllowCredentials
accessControlAllowHeaders
accessControlAllowMethods
```


## Detailed design

###  Schema

```
x-global-cors:
       corsConfigurationEnabled : {
                    Data type           : boolean    
                    Required            : true
                    Description        : Weather to enable or disable CORS
                    },
        accessControlAllowOrigins : { 
                    Data type          : array
                    Required           :  optional 
                    Default              : [*]
                    Description       :  List of allowed domains for the Access-Control-Allow-Origin header.
                    },
        accessControlAllowCredentials :{
                    Data type     :  boolean
                    Required    :  optional
                    Default     :  false
                    Description    :  Flag to determine whether the Access-Control-Allow-Credentials header should be sent with true as the value.
                    },
        accessControlAllowHeaders  :{
                    Data type          :  string
                    Required           :  optional 
                    Default              : Value of the Access-Control-Request-Headers request header
                    Description       :  Value for the Access-Control-Allow-Headers header
                    },
        accessControlAllowMethods : {
                    Data type          :  array
                    Required           :  optional 
                    Default              :  [ GET, HEAD, PUT, PATCH, POST ]
                    Description       :  Value for the Access-Control-Allow-Methods header
                    }
        }

```


If an API developer add the above to an OAS definition under the heading x-global-spec an API-gateway should be able to apply CORS configuration settings  to that particular API  whit the given setting or if those settings are  not provided it should use the default values for the configuration provided by the schema.

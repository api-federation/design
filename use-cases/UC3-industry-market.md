# UC3 - Industry MarketPlace
Assume a set of companies that work in the same industry (eg: banks).
Often there's a central entity that regulates the industry. It can also provide IT services to the industry.
As different companies will provide different services this entity can work as an entry point for developers that want to consume the APIs.

This can be achieved by having the having the companies services hosted centrally with different levels of integration:

### 1. Yellow Pages
-------------
The central entity shall have a list of APIs, providing a yellow pages kind of functionality.
This means the catalogue will have all the APIs from all companies, duplicating them in case of repeated functionality. It shall be clear that each API belong to a specific player. When looking for details the developer is redirected to the developer portal of the API provider.

#### Search Scenario
| Search | Result |
| ------------- | ------------- |
| Developer searches for a specific bank. (eg: HSBC) | The result will have all APIs belonging to the bank.  |
| Developer searches for a specific functionality (eg: Balance) | The result will have all APIs from all banks which have a balance service  |

### 2. Central Catalogue
-------------
The central entity shall have a list of APIs, grouped by functionality.
Similar/Standar APIs that are provided by several providers are logically grouped so that only one is shown to the developer.
For the developer it shall be clear which providers are behind that specific service. When looking for more information the Developer shall be redirected to the Developer Portal belonging to the provider of interest.
For specific APIs, that are provided only by one provider, the behaviour shall be the same as in (1.).

#### Search Scenario
| Search | Result |
| ------------- | ------------- |
| Developer searches for a specific bank. (eg: HSBC) | The result will have all APIs belonging to the bank.  |
| Developer searches for a specific functionality (eg: Balance) | The result will have only one API but it will clearly mention which banks provide the serice (eg: HSBC + Deutsche Bank) |

### 3. Customer Management
-------------
Building on (2.) and (3.), instead of redirecting to the Developer Portal of the Bank, it's possible the central entity can manage the Developers.
In this case it will manage the credentials of the client application (eg: key and secret), "injecting" them in the service providers' systems.
The actual consumption of the APIs shall still be done directly against the API gateways of the service providers.


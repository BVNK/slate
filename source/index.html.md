---
title: BVNK API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - go
  - java
  - javascript
  - python

toc_footers:
  - <a href='https://bvnk.co/contact' target='_blank'>Contact</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors
  - api/user-creation/index
  - api/authorization/index
  - api/accounts/index
  - api/transactions/index
  - api/cards/index
  - api/beneficiaries/index
  - api/kyc/index
  - api/merchants/index
  - api/exchange/index
  - api/notifications/index
  - api/integrations/index

search: true
---

# Introduction

> All calls result in either success `200` or failure `400`. On success, the response follows the following structure:

```json
{
    "response": ""
}
```

> On failure, the response follows the following structure:


```json
{
    "error": ""
}
```

Welcome to the BVNK API. We believe banking should be a concentration of elegant and effective functions rather than the complex, bloated and expensive system it is today.

Our API driven banking infrastructure can allow anyone to create new products, or to expand on their existing offering. We enable innovation through providing a platform.

Find out more about [BVNK on our website](https://bvnk.co).

# Defaults

System wide defaults are followed for consistency. 

In the case of the demo installation, no API key is required. For all custom deploys or the production deploy, API keys will be issued for developers to test against.
These API keys will need to be included on each and every request to the API using the header value `X-Api-Key` and `X-Api-Secret`.

## Basic Auth

Some requests are limited to admins of the installation. In these cases, the routes are secured through Basic Auth. Usernames and passwords will be issued to developers 
on request, and for private installations given to the relevant parties.

# Contact

For more information please reach out to us on [BVNK](https://bvnk.co/contact)

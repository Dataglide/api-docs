# Dataglide API

## Overview

This repository is intended for developers who want to write applications that interact with Dataglide. It contains documents that explain the basic concepts of Dataglide and of the API itself. It also provides an overview of the different functions that the API supports. Currently the Dataglide API only allows read access to data.

## Accessing the API

The Dataglide API is available at ```https://api.{environment}.dataglide.co/{version}/{endpoint}``` where {version} is the version of the API that you wish to access (currently v1.0). Access to the API must be made using TLS1.2 (less secure versions of TLS are not supported).

Access to the Production environment is available at: ```https://api.dataglide.co/{version}/{endpoint}```.

Access to the Parallel environment is available at: ```https://api.parallel.dataglide.co/{version}/{endpoint}```

## Authorisation

In order to use the Dataglide API your application will need to fetch an authorisation token. This token can then be used to access other resources in the Dataglide API. Dataglide authorisation tokens are standard JWT tokens that are very widely supported with libraries available for most modern programming languages. More information on JWT tokens can be found [here](https://en.wikipedia.org/wiki/JSON_Web_Token).

To fetch an authorisation token POST your credentials to this endpoint:

```[POST] /auth/token```

```
{
  "apiId": "string",
  "apiSecretKey": "string"
}
```
A typical response will look like this:
```
{
  "result": "Success",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
  "expiry": "2023-04-23T18:25:43.511Z"
}
```

The authorisation token should then be used in subsequent calls to the API by providing it in the ```Authorization``` header in the format: ```Bearer {token}```. For security reasons, all authorisation tokens have an expiry date/time, typically 30-60 minutes after they are issued. Both secret keys and authorisation tokens should be held securely.

If you want to refresh your token with a new token you can call:

```[GET] /auth/token```

This will return you a new token with an extended expiry date/time.

Endpoints will return a ```401``` status code if the authorisation token provided is missing, invalid or expired. If you application runs for an extended period then you should regularly refresh your access token. If your application receives a 401 response then you should re-authenticate to fetch a new valid token - it is not possible to refresh an expired token. 

# Endpoints

| Subject | Description |
| ------- | ----------- |
| [Asset managers](asset-managers.md) | List of asset managers that you have access to |
| [NAVs](navs.md) | Allows access to NAV values |
| [Related documents](related-documents.md) | Documents related to a share class, fund, sub-fund or asset manager |

# Paging

Some endpoints can return large quantities of data and employ paging to reduce the size of individual API calls. If an endpoint returns a URL in the ```links.next``` field then the data has been paged and you should use the URL to fetch the next page of data. Repeat this until ```links.next``` is null or empty.

# Format of JSON from the API

Most of the API endpoints return data in a reduced [JSON:API](https://jsonapi.org/) format. 

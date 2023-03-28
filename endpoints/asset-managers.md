# Asset managers

```[GET] /AssetManagers/```

Returns a list of the asset managers which you have access to. A typical response will be:

```
{
  "data": [
    {
      "type": "assetmanagers",
      "id": "287543a5-7657-422b-946f-c412dd718682",
      "attributes": {
        "name": "1741 Fund Solutions AG"
      }
    },
    {
      "type": "assetmanagers",
      "id": "eb5f4d08-3871-48a1-98db-a293fb61d9fb",
      "attributes": {
        "name": "Aachener Grundvermögen KAG mbH"
      }
    },
    ....
```

The ```id``` provided can be used to access other endpoints related to the asset manager - for examples NAVs, share classes etc.

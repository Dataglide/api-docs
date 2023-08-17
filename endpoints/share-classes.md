# Share classes

## Getting a share class from a specified ISIN

The following endpoint returns data about the share class with the specified ISIN

```[GET]/ShareClasses/ByISIN/{ISIN}```

Where {ISIN} is the ISIN of the target share class.

## Get a share class from a share class Id

```[GET]/ShareClasses/{shareClassId}/```

## Typical ShareClass response

A typical response will look like this:

```
{
    "data": {
        "type": "shareclasses",
        "id": "95c78688-d21f-ee11-8646-000d3a2055d4",
        "attributes": {
            "currency": "EUR",
            "isin": "LU2461279213",
            "extended": {
                "brl_is_lmtcptloss": "Neutral",
                "eet_geninf_reporting_name": "Private Equity (Lux) Evergreen Secondary Fund EUR D-acc",
                "eet_prddscl_lngs": "EN",
                "val_vevref": "0.117387"
                ....
            }
        },
        "relationships": {
            "navs": {
                "links": {
                    "related": "/api/v1.0/ShareClasses/95c78688-d21f-ee11-8646-000d3a2055d4/NAVs"
                },
                "data": {
                    "type": "Navs"
                }
            },
            "subFund": {
                "links": {
                    "related": "/api/v1.0/SubFunds/70540a47-2199-ed11-994b-0022488776d0"
                },
                "data": {
                    "type": "SubFunds",
                    "id": "70540a47-2199-ed11-994b-0022488776d0"
                }
            }
        }
    }
}
 ```

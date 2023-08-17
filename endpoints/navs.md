# NAVs

# Getting recent NAVs for an asset manager

The following endpoint returns a list of NAVs that have been added or modified since the specified date/time. The date/time can only be 14 days in the past.

```[GET]/AssetManagers/{assetManagerId}/NAVs/ModifiedSince/{date}/```

A typical response will look like this:

```
{
    "links": {
        "next": "<url to next results page>"
    },
    "data": [
        {
            "type": "navs",
            "id": "<id for this nav>",
            "attributes": {
                "effectiveDate": "2021-12-02T00:00:00",
                "currency": "CHF",
                "isin": "CH0038724750",
                "modifiedOn": "2023-03-11T09:14:25.73",
                "extended": {
                    "ancdat": "2021-12-02",
                    "inst_wal": "50",
                    "inst_wam": "50",
                    "msr_yld": "-0.0097",
                    "msr_yld30dc": "-0.00818640841",
                    "msr_yld30de": "-0.0088",
                    "msr_yld7dc": "-0.0087",
                    "msr_yld7de": "-0.0093",
                    "val_nav_date": "2021-12-02"
                }
            }
        },
        ....
 ```

# Get all NAVs for a specific share class

```[GET]/ShareClasses/{shareClassId}/NAVs```

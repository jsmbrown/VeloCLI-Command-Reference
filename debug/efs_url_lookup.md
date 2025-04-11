#	--efs_url_lookup [destination URL]

##	Description
Fetch Web Reputation & category for a given URL

##  Arguments (optional)
| Argument | Description |
|---|---|
| <destination URL> | URL for which to fetch the web reputation & category from the edge URL filtering engine |

##  Example usage
```
example_com:velocli> debug --efs_url_lookup velocloud.com
URL: velocloud.com
Lookup Result: Retrieved value from Local DB
Category: Business and Economy
Reputation: 88
```

##  Field descriptions
| Row | Description |
|---|---|
| URL | URL upon which the lookup was performed |
| Category | URL category assigned by the edge URL filtering engine |
| Reputation | Reputation score assigned by the edge URL filtering engine.  URLs with scores below the reputation level(s) allowed via policy will be blocked.  Reputation levels and their associated scores are included below for reference. |

##  Reputation levels
| Reputation level | Score Range |
|---|---|
| Trustworthy | 81-100 |
| Low Risk | 61-80 |
| Medium Risk | 41-60 |
| Suspicious | 21-40 |
| High Risk | 0-20 |
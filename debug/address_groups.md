#	--address_groups [v4 | v6 | all]

##	Description
Dumps a list of the address based object groups configured in the VCO.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none (or 'all') | Display all configured address groups |
| v4 | Display only IPv4 and domain name based address groups (includes the IPv4 portions of mixed v4/v6 groups) |
| v6 | Display only IPv6 and domain name based address groups (includes the IPv6 portions of mixed v4/v6 groups) |

##  Example usage
```
example_com:velocli> debug --address_groups all    
[
  {
    "addresses": [
      {
        "ipv6": "2606:4700:4700::1001",
        "mask": "ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff"
      },
      {
        "ipv6": "2606:4700:4700::1111",
        "mask": "ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff"
      }
    ],
    "logicalId": "2ee0fe67-7f20-435a-85c2-343bc437c5d6"
  },
  {
    "addresses": [
      {
        "ip": "1.0.0.1",
        "mask": "255.255.255.255"
      },
      {
        "ip": "1.1.1.1",
        "mask": "255.255.255.255"
      },
      {
        "ipv6": "2606:4700:4700::1001",
        "mask": "ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff"
      },
      {
        "ipv6": "2606:4700:4700::1111",
        "mask": "ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff"
      }
    ],
    "logicalId": "7995d0b7-f54f-4ae4-beb0-5e10966e7b6b"
  },
  {
    "addresses": [
      {
        "Domain name": "testmynids.org"
      }
    ],
    "logicalId": "bb837841-7b90-4476-8614-e8a8731b16fe"
  },
  {
    "addresses": [
      {
        "ip": "8.8.4.4",
        "mask": "255.255.255.255"
      },
      {
        "ip": "8.8.8.8",
        "mask": "255.255.255.255"
      }
    ],
    "logicalId": "00093ecf-8594-40c8-a0dc-c6dd9c594b0e"
  }
]
```

##  Field descriptions
| Object | Description |
|---|---|
| addresses | List of the IPv4 and IPv6 prefix(es)/mask(s) and any domain names that are included in the address group. |
| logicalId | UUID of the address group |

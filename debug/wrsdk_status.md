#	--wrsdk_status

##	Description
Displays the status of the Webroot Software Development Kit (SDK) integrated into the VeloCloud Edge. This includes information about the versions of the IP reputation and URL classification databases used by the SDK for security features.

##  Arguments (optional)
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --wrsdk_status
{
  "db_ver": {
    "ip_maj": 1,
    "ip_min": 6373,
    "ip_upd": 140,
    "url_maj": 9
  }
}
```

##  Field descriptions
| Field          | Description                                           |
|----------------|-------------------------------------------------------|
| `db_ver`       | An object containing database version information.    |
| `db_ver.ip_maj`| The major version number of the IP reputation database. |
| `db_ver.ip_min`| The minor version number of the IP reputation database. |
| `db_ver.ip_upd`| The update version number of the IP reputation database.|
| `db_ver.url_maj`| The major version number of the URL classification database. |
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
    "ip_min": 6401,
    "ip_upd": 140,
    "url_maj": 9,
    "url_min": 436,
    "url_upd": 10
  },
  "ntics_reachable": true,
  "stats": {
    "cache": 0,
    "cdbapp": 0,
    "cdbconnection": 0,
    "cdbfile": 0,
    "cdbip": 0,
    "cdburl": 0,
    "cloud": 0,
    "dp": 0,
    "filemd5": 0,
    "ipg": 0,
    "ipr": 0,
    "ipt": 0,
    "net": 0,
    "phishingscore": 0,
    "tievidence": 0,
    "tihistory": 0,
    "timd5": 0,
    "tiurl": 0,
    "uc": 0
  },
  "vc_webroot_db_loaded": true,
  "wrsdk_db_loaded": true,
  "wrsdk_init_done": true,
  "wrsdk_state": "Inited"
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
| `db_ver.url_min`| The minor version number of the URL classification database. |
| `db_ver.url_upd`| The update version number of the URL classification database. |
| `ntics_reachable`| `true`/`false` indicator for whether the NSX Threat Intelligence Cloud Service is reachable. |
| `stats` | Object containing Webroot SDK stats |
| `stats.cache` | Number of times data cached from a previous lookup was retrieved. |
| `stats.cdbapp` | Number of times Cloud Database (CDB) app stats were successfully read. |
| `stats.connection` | Number of successful CDB URL connection lookups. |
| `stats.cdbfile` | Number of successful CDB file lookups. |
| `stats.cdbip` | Number of successful CDB IP lookups. |
| `stats.cdburl` | Number of successful CDB URL lookups. |
| `stats.cloud` | Number of times data was retrieved from the CDB. |
| `stats.dp` | Number of times data was retrieved from the local dB. |
| `stats.filemd5` | Number of successful MD5 file lookups. |
| `stats.ipg` | Number of successful IP geo lookups. |
| `stats.ipr` | Number of successful IP reputation lookups. |
| `stats.ipt` | Number of successful IP threat lookups. |
| `stats.net` | Number of times a network lookup occurred, regardless of result. |
| `stats.phishingscore` | Number of successful phishing score lookups. |
| `stats.tievidence` | Number of successful lookups of threat insight IP evidences. |
| `stats.tihistory` | Number of successful lookups of threat insight URL histories. |
| `stats.timd5` | Number of successful lookups of threat insight MD5s. |
| `stats.tiurl` | Number of successful lookups of threat insight URLs. |
| `stats.uc` | Number of times a URL info task returned an “Uncategorized” result. |
| `vc_webroot_db_loaded` | `true`/`false` indicator for whether URL DB and IP DB are downloaded and loaded from NTICS by the edge. |
| `wrsdk_db_loaded` | `true`/`false` indicator for whether URL DB and IP DB are downloaded and loaded from NTICS by Webroot SDK. |
| `wrsdk_init_done` | `true`/`false` indicator for whether the Webroot SDK has finished initializing. |
| `wrsdk_state` | Current working state of the Webroot SDK. |
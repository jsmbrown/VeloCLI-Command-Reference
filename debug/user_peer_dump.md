#	--user_peer_dump

##	Description
Dumps a list of all peer edges/clusters with both the peer UUID and friendly name.

##  Arguments
None

##  Example usage
```
example__com:velocli> debug --user_peer_dump
LOGICAL_ID                                       PEER
891413b5-4fd7-417f-8efc-102aeb579df8        AzurevWAN
3294602a-5a69-4694-a7d2-811aff737faa   vNET Peer Test
82354916-b421-4c48-b3b5-6e0a06795904         Home-620
```

##  Field descriptions
| Column | Description |
|---|---|
| LOGICAL_ID | UUID of the peer edge or cluster |
| PEER | Friendly name of the peer edge or cluster |

#	--user_peer_dump

##	Description
Dumps a list of all peer edges/clusters with both the peer UUID and friendly name.

##  Arguments
None

##  Example usage
![image](Images/user_peer_dump.png)

'''
example_com:velocli> debug --user_peer
LOGICAL_ID                                  PEER
891413b5-4fd7-417f-8efc-102aeb579df8   AzurevWAN
'''

##  Field descriptions
| Column | Description |
|---|---|
| LOGICAL_ID | UUID of the peer edge or cluster |
| PEER | Friendly name of the peer edge or cluster |

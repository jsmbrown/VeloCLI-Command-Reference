#	--edge_list

##	Description
Displays a list of all VeloCloud Edges associated with the enterprise, along with their respective Logical IDs and Profile IDs. This command is useful for quickly identifying edges and their assigned configuration profiles managed by the VeloCloud Orchestrator.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --edge_list
Name                                          LogicalId                             ProfileId
AWS East Lab Hub   de5ee312-1b4a-4eba-8726-bbd3a4e52db2  893487a2-1518-11ee-b33f-0ae26eaf7805
gcp-us-east1_1     80230d92-f754-42d1-bf19-b5a85534ffdc  00000000-0000-0000-0000-000000000000
gcp-us-east1_2     58e340d6-32ec-4f45-8994-366acf8d92fd  00000000-0000-0000-0000-000000000000
HQ-620             82352316-b421-4c48-b3b5-6e0a06795904  2ce32039-bc9c-11e8-ac9a-0a83c3e55ff9
```

##  Field descriptions
| Column    | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| Name      | The user-defined name of the VeloCloud Edge.                                |
| LogicalId | The unique identifier (UUID) assigned to the VeloCloud Edge.                |
| ProfileId | The unique identifier (UUID) of the configuration profile applied to the Edge. (will be all `0` for edges without branch to branch VPN enabled)|
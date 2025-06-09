#	--cws_pol_dump

##	Description
Displays the Cloud Security Service (CSS) policy configuration active on the VeloCloud Edge. This includes the logical identifier, policy name, and policy ID associated with CSS, which is used for directing internet-bound user traffic to ZScaler proxy nodes for web security filtering.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --cws_pol_dump
Logical Id   CWS Policy Name  CWS Policy ID

example_com:velocli>
```
##  Field descriptions
| Column            | Description                                         |
|-------------------|-----------------------------------------------------|
| Logical Id        | The logical identifier for the CSS policy instance. |
| CWS Policy Name   | The name assigned to the CSS policy.                |
| CWS Policy ID     | The unique identifier for the CSS policy.           |
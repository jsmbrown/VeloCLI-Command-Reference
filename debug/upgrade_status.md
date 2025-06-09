#	--upgrade_status

##	Description
This command displays the current software upgrade status of the VeloCloud Edge. It indicates whether an upgrade has been triggered, is in progress, has completed successfully, or has failed.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --upgrade_status
{
  "upgradeStatus": "No upgrade triggered"
}
```

##  Field descriptions
| Field         | Description                                       |
|---------------|---------------------------------------------------|
| upgradeStatus | Describes the current state of the software upgrade. |
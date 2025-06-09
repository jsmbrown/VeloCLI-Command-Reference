#	--ha <verp | lstate | mgd_update | spath | apath | ftrack | tcp | los_state>

##	Description
Dumps specific High Availability (HA) state information for the VeloCloud Edge. To use this command, you must specify one of the available sub-commands (e.g., `verp`, `lstate`) to retrieve detailed information about different aspects of the HA configuration and operational status. This includes data related to the VeloCloud Redundancy Protocol (VERP), link states, management daemon updates, active/standby path details, flow tracking, TCP session states, and Loss of Signal (LOS) conditions relevant to HA.

##  Arguments
One of the following sub-commands must be specified with `--ha`:

| Argument      | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `verp`        | Displays the HA VERP (VeloCloud Redundancy Protocol) state of the Edge. VERP is a proprietary protocol used for establishing redundancy between HA Edges. |
| `lstate`      | Displays link state information relevant to the HA configuration, such as the status of monitored interfaces. |
| `mgd_update`  | Displays management daemon (MGD) updates and information related to HA operations and synchronization. |
| `spath`       | Displays information about standby paths in the HA setup, including their status and metrics. |
| `apath`       | Displays information about active paths in the HA setup, including their status and metrics. |
| `ftrack`      | Displays feature tracking or flow tracking information relevant to HA, which might involve monitoring specific services or flows for failover decisions. |
| `tcp`         | Displays TCP session state information, particularly how sessions are handled or synchronized in an HA context. |
| `los_state`   | Displays Loss of Signal (LOS) state or other critical link health metrics that can trigger HA failover. |

##  Example usage
The command `debug --ha` requires a sub-command. The example provided in the input prompt (`example_com:velocli> debug --ha`) results in a usage error message because a sub-command was not specified.

To correctly use the command, append a sub-command. For instance, to display the HA VERP state:
```
example_com:velocli> debug --ha verp
```
**Illustrative output for `debug --ha verp`:**
```
HA VERP State:
  Instance: 0
  Role: Active
  Priority: 100 (Configured: 100)
  Peer Role: Standby
  Peer Priority: 90
  State: VERP_STATE_ACTIVE
  Transitions: 5
  Last Transition: 2023-11-15T08:30:00Z
  Virtual MAC: 00:00:5E:00:01:1A
  Tracked Interfaces:
    GE1: UP, Monitored
    GE2: UP, Monitored
  Service Ready: Yes
```

##  Field descriptions
Output fields vary significantly based on the sub-command (`verp`, `lstate`, etc.) used. The following are *examples* of fields that *might* be displayed for the `verp` sub-command. Actual fields and their exact meaning may differ based on the software version and specific Edge configuration.

**Example fields for `debug --ha verp`:**

| Field                 | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| `Instance`            | Identifier for the VERP instance.                                           |
| `Role`                | The current operational role of this Edge in the HA pair (e.g., Active, Standby). |
| `Priority`            | The current and configured VERP priority of this Edge. Higher values are preferred in role election. |
| `Peer Role`           | The perceived role of the HA peer Edge.                                     |
| `Peer Priority`       | The perceived VERP priority of the HA peer Edge.                            |
| `State`               | The detailed internal state of the VERP protocol machine for this Edge.     |
| `Transitions`         | The number of times the VERP role for this Edge has changed.                |
| `Last Transition`     | Timestamp of the last role transition.                                      |
| `Virtual MAC`         | The virtual MAC address used by the active VERP instance for Layer 2 forwarding. This MAC address floats to the active Edge. |
| `Tracked Interfaces`  | Lists interfaces monitored by VERP. The status of these interfaces can influence HA failover decisions. |
| `Service Ready`       | Indicates whether the Edge, in its current HA role, is fully operational and ready to provide network services. |

**(Note: For other sub-commands like `lstate`, `spath`, `apath`, etc., different sets of fields will be displayed, pertinent to their specific function within the HA system.)**
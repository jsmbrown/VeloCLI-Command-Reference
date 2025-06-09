#	--qoe_threshold

##	Description
Displays the current Quality of Experience (QoE) threshold values configured on the VeloCloud Edge. These thresholds are used by the system to assess the quality of network paths for different types of applications based on observed latency, loss, and jitter. The system categorizes path quality into "good", "fair" (yellow), and "poor" (red) based on these values.

##  Arguments (optional)
| Argument | Description |
|---|---|
| None | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --qoe_threshold
{
  "qoe": {
    "trans": {
      "jitter": {
        "red": 200,
        "yellow": 200
      },
      "latency": {
        "red": 500,
        "yellow": 500
      },
      "loss": {
        "red": 20,
        "yellow": 20
      }
    },
    "video": {
      "jitter": {
        "red": 50,
        "yellow": 50
      },
      "latency": {
        "red": 300,
        "yellow": 300
      },
      "loss": {
        "red": 10,
        "yellow": 10
      }
    },
    "voice": {
      "jitter": {
        "red": 50,
        "yellow": 50
      },
      "latency": {
        "red": 300,
        "yellow": 300
      },
      "loss": {
        "red": 10,
        "yellow": 10
      }
    }
  }
}
```
*Note: The example output above is illustrative. The actual values may vary based on the Edge's configuration.*

##  Field descriptions
The output is a JSON object detailing QoE thresholds for different application categories and network metrics.

| Field Path                      | Description                                                                                                                               |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `qoe`                           | The root object containing all QoE threshold configurations.                                                                              |
| `qoe.<app_category>`            | An object representing an application category for which specific QoE thresholds are defined. Common categories include `trans` (transactional), `video`, and `voice`. |
| `qoe.<app_category>.<metric>`   | An object defining the thresholds for a specific network performance metric within an application category. Metrics include `jitter` (in milliseconds), `latency` (in milliseconds), and `loss` (as a percentage). |
| `qoe.<app_category>.<metric>.red`    | The "red" threshold value for the specified metric and application category. If the measured value for this metric exceeds the "red" threshold, the path quality is considered poor for that application type. |
| `qoe.<app_category>.<metric>.yellow` | The "yellow" threshold value for the specified metric and application category. If the measured value for this metric exceeds the "yellow" threshold but is less than or equal to the "red" threshold, the path quality is considered fair (or degraded) for that application type. Path quality is considered "good" if the metric is below the "yellow" threshold. |

**Example Breakdown:**
*   `qoe.trans.jitter.red: 200` means that for transactional applications, if the jitter on a path exceeds 200ms, the path's quality is considered "red" (poor) for transactional traffic.
*   `qoe.video.loss.yellow: 10` means that for video applications, if packet loss on a path is greater than 10% (but less than or equal to the `red` threshold for video loss), the path's quality is considered "yellow" (fair) for video traffic.
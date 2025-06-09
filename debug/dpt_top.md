#	--dpt_top [core-id|all]

##	Description
Shows detailed statistics for Data Plane (DP) core utilization and task performance. This command helps in identifying performance bottlenecks or high CPU usage on specific cores handling network traffic.

##  Arguments (optional)
| Argument | Description |
|---|---|
| core-id | Specifies a particular DP core ID for which to display statistics. |
| all | Displays statistics for all available DP cores. If no argument is provided, this is the default behavior. |

##  Example usage
```
example_com:velocli> debug --dpt_top
100.00% Core 0: flags=ITF----, cpuset=0x2
   |--- 96.51% Idle
   |--- 1.67% Tasks
   |       |--- 0.21/12.44%  dp_worker_queue0                                 min=62ns       max=737ns      work=0/s       max_work=64
   |       |--- 0.19/11.36%  crypto_poll0                                     min=80ns       max=798ns      work=0/s       max_work=4096
   |       |--- 0.16/9.44%   dpdk_l2fwd_rx_packet_eth0_q0                     min=83ns       max=561ns      work=15/s      max_work=64
```

##  Field descriptions
The output is hierarchical, showing overall core statistics and then breaking down utilization by tasks running on that core.

| Field/Column | Description |
|---|---|
| **Core Line** | (e.g., `100.00% Core 0: flags=ITF----, cpuset=0x2`) |
| Percentage (Overall) | Total utilization percentage of the specific core. |
| Core ID | The identifier of the CPU core (e.g., `Core 0`). |
| flags | Internal flags associated with the core's state or configuration. |
| cpuset | The CPU set affinity for this core, indicating which CPUs it can run on. |
| **Idle Line** | (e.g., `|--- 96.51% Idle`) |
| Percentage (Idle) | Percentage of time the core has been idle. |
| **Tasks Line** | (e.g., `|--- 1.67% Tasks`) |
| Percentage (Tasks) | Percentage of time the core has spent executing tasks. |
| **Individual Task Lines** | (e.g., `|--- 0.21/12.44%  dp_worker_queue0 ...`) |
| Current/Peak % | The current percentage of core utilization by this task, followed by the peak percentage observed for this task. (e.g., `0.21/12.44%`) |
| Task Name | The name of the specific data plane task or process (e.g., `dp_worker_queue0`, `crypto_poll0`, `dpdk_l2fwd_rx_packet_eth0_q0`). |
| min | Minimum execution time observed for this task instance, typically in nanoseconds (ns). |
| max | Maximum execution time observed for this task instance, typically in nanoseconds (ns). |
| work | Current work rate of the task (e.g., operations per second, packets per second). |
| max_work | Maximum work capacity or batch size for the task. |
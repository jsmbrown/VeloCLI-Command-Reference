#	--de2e_delete &lt;vceid&gt;

##	Description
Tears down Dynamic Edge to Edge (DE2E) tunnels to the specified VeloCloud Edge (VCE). This command is used to manually remove dynamically established tunnels to a particular peer Edge.

##  Arguments
| Argument  | Description |
|-----------|-------------|
| `&lt;vceid&gt;` | Required. The unique identifier of the VeloCloud Edge (VCE) to which existing Dynamic Edge to Edge (DE2E) tunnels should be torn down. This ID can typically be found in the VeloCloud Orchestrator for the target Edge. |

##  Example usage
```
example_com:velocli> debug --de2e_delete edge001-aabbccdd-1234-5678-90ab-cdef01234567
```

##  Field descriptions
This command is used to perform an action (tearing down DE2E tunnels) and does not produce tabular output. Upon successful execution, it typically returns no output or a simple confirmation message. If an error occurs (e.g., an invalid `vceid` is provided or the specified Edge is not a DE2E peer), an error message will be displayed.
# --ike_logger_setlevel &lt;global_level_num&gt; &lt;ikev1_level_num&gt; &lt;enable_notice&gt; [module_name=module_level_num ...]

## Description
Overrides the default log level for the IKE (Internet Key Exchange) module. This command allows for fine-grained control over the verbosity of IKE-related logging, which is essential for diagnosing VPN tunnel issues and monitoring IKE operations. Adjusting log levels can help in capturing detailed information during troubleshooting or reducing log volume during normal operation.

## Arguments
| Argument                       | Description                                                                                                                               | Accepted Values                                                                 |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| `global_level_num`             | Sets the global log level for all IKE operations. This level applies unless overridden by a more specific setting (e.g., `ikev1_level_num` or a module-specific level). | 3-10, 99 (See Log Level Details below)                                          |
| `ikev1_level_num`              | Sets the log level specifically for IKEv1 protocol operations.                                                                            | 3-10, 99 (See Log Level Details below)                                          |
| `enable_notice`                | Enables (`1`) or disables (`0`) notice-level messages. Notices typically provide high-level information about state changes or successful operations. | `0` (disable), `1` (enable)                                                     |
| `module_name=module_level_num` | Optional. Allows setting a specific log level for an individual IKE internal module (e.g., `ENC` for encryption, `AUTH` for authentication). This argument can be repeated for multiple modules by appending them. Format: `MODULENAME=LEVEL`. | `module_name`: Name of the IKE module.<br>`module_level_num`: 3-10, 99 (See Log Level Details below) |

## Log Level Details
The following numeric values define the verbosity of IKE logging:
| Level | Description                                                                                                                              |
|-------|------------------------------------------------------------------------------------------------------------------------------------------|
| 3     | External, non-fatal, high-level errors. For example, an incorrectly formatted message received from a peer, or a failed negotiation.       |
| 4     | Positive high-level information, such as a successfully completed negotiation.                                                             |
| 5     | Information about starting a high or middle-level operation. For example, the initiation of a negotiation, or opening a cryptographic device. |
| 6     | Uncommon situations or potential issues that might indicate a bug or misconfiguration.                                                   |
| 7     | Nice-to-know information, such as entering or exiting a function, or the result of a low-level operation.                                  |
| 8     | Dumps of data blocks, such as hashes, cryptographic keys, certificates, or other non-massive data structures.                              |
| 9     | Dumps of IKE protocol packets.                                                                                                           |
| 10    | Intermediate results or mid-operation status updates (non-final results).                                                                  |
| 99    | Displays the most comprehensive debugging information. **Caution:** This level is CPU intensive and should be used judiciously, primarily for deep troubleshooting. |

## Example Usage
The command requires specific log level parameters. If called without them, it will return an error indicating insufficient arguments:
```
example_com:velocli> debug --ike_logger_setlevel
Insufficient Arguments

example_com:velocli>
```

To set the global IKE log level to 4, IKEv1 log level to 5, enable notices, and set the 'ENC' module log level to 7:
```
example_com:velocli> debug --ike_logger_setlevel 4 5 1 ENC=7
```
*(Note: Successful execution of this command typically does not produce detailed output to the console. The changes take effect in the IKE logging system, and the results can be observed in the relevant log files or system logging output.)*

## Field Descriptions
This command is used for configuration and does not produce a tabular output with specific fields. Its primary effect is to change the IKE logging behavior. Output to the console is generally limited to a success confirmation (which may be minimal or absent) or an error message such as "Insufficient Arguments". The impact of the command is observed in the generated IKE logs.
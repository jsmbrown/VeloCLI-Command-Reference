#	--qat_dump

##	Description
This command displays the status of Intel QuickAssist Technology (QAT) on the VeloCloud Edge. QAT is a hardware acceleration feature that can offload computationally intensive tasks like encryption and decryption, potentially improving performance for VPN tunnels and other security functions.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --qat_dump
{
  "Status": "Enabled"
}
```

##  Field descriptions
| Field  | Description                                                                 |
|--------|-----------------------------------------------------------------------------|
| Status | Indicates the current operational state of QAT. Can be "Enabled" or "Disabled". |
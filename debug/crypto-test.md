#	--crypto-test

##	Description
Run a crypto test on the path(s) connected through an interface. This command is used to verify the cryptographic operations for the secure tunnels (paths) established by the VeloCloud Edge. It typically tests the underlying crypto modules and algorithms used for encryption, decryption, and integrity protection of the data plane traffic over these paths.

##  Arguments
This command does not take any specific arguments.

##  Example usage
```
example_com:velocli> debug --crypto-test
```

##  Field descriptions
The output of this command will display the results of the cryptographic self-tests. While the exact output format may vary, it generally includes:
*   Status indications (e.g., pass/fail) for various cryptographic algorithm checks.
*   Information about the specific tests performed.
*   Potentially, details on any errors encountered during the tests.

This information helps in diagnosing issues related to secure tunnel formation or data integrity over the SD-WAN overlay.
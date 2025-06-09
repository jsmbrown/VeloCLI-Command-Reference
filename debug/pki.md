#	--pki

##	Description
Dumps the current Public Key Infrastructure (PKI) configuration active on the VeloCloud Edge. This includes details about Certificate Revocation Lists (CRLs) used by the system to validate certificates, which is crucial for secure communication within the SD-WAN fabric, including tunnels to Gateways, other Edges, and the VeloCloud Orchestrator.

##  Arguments (optional)
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --pki
{
  "CRLs": [
    {
      "Authority Key Identifier": "54D22C41BBD89BE9A35049B136C417A2EE81065B",
      "CRL Version": "2 (0x1)",
      "Issuer": "CN=vco12-usvi1, OU=OPS, O=VeloCloud",
      "Last Update": "2023-10-26T12:00:00Z",
      "Next Update": "2023-10-27T12:00:00Z",
      "Revoked Certificates": [
        {
          "Revocation Date": "2023-01-15T10:30:00Z",
          "Serial Number": "0A1B2C3D4E5F"
        }
      ],
      "Signature Algorithm": "sha256WithRSAEncryption"
    }
  ],
  "Certificates": [
    {
      "Issuer": "CN=VeloCloud Root CA, O=VeloCloud Networks, Inc., L=Mountain View, ST=California, C=US",
      "Serial Number": "1234567890ABCDEF",
      "Subject": "CN=edgeSerial-xxxx, O=VeloCloud Networks, Inc., L=Mountain View, ST=California, C=US",
      "Valid From": "2023-01-01T00:00:00Z",
      "Valid To": "2025-01-01T00:00:00Z",
      "Key Usage": "Digital Signature, Key Encipherment",
      "Extended Key Usage": "TLS Web Client Authentication, TLS Web Server Authentication"
    }
  ]
}
```

##  Field descriptions
The output is in JSON format.
| Field                      | Description                                                                                                |
|----------------------------|------------------------------------------------------------------------------------------------------------|
| `CRLs`                     | An array of objects, where each object represents a Certificate Revocation List (CRL).                     |
| `CRLs[].Authority Key Identifier` | The identifier of the public key of the CA that signed this CRL.                                       |
| `CRLs[].CRL Version`       | The version number of the CRL format.                                                                      |
| `CRLs[].Issuer`            | The Distinguished Name (DN) of the Certificate Authority (CA) that issued and signed the CRL.              |
| `CRLs[].Last Update`       | The date and time this CRL was issued.                                                                     |
| `CRLs[].Next Update`       | The date and time by which the next CRL will be issued.                                                    |
| `CRLs[].Revoked Certificates` | An array of objects, each detailing a certificate that has been revoked.                                 |
| `CRLs[].Revoked Certificates[].Revocation Date` | The date and time when the certificate was revoked.                                      |
| `CRLs[].Revoked Certificates[].Serial Number` | The serial number of the revoked certificate.                                              |
| `CRLs[].Signature Algorithm` | The algorithm used to sign the CRL.                                                                        |
| `Certificates`             | An array of objects, where each object represents a digital certificate present on the Edge.               |
| `Certificates[].Issuer`    | The Distinguished Name (DN) of the entity that signed and issued the certificate.                          |
| `Certificates[].Serial Number` | A unique number assigned to the certificate by the CA.                                                   |
| `Certificates[].Subject`   | The Distinguished Name (DN) of the entity the certificate identifies (e.g., the Edge itself).              |
| `Certificates[].Valid From` | The date and time from which the certificate is valid.                                                     |
| `Certificates[].Valid To`  | The date and time until which the certificate is valid.                                                    |
| `Certificates[].Key Usage` | Defines the purpose of the public key contained in the certificate (e.g., digital signature, key encipherment). |
| `Certificates[].Extended Key Usage` | Further refines the intended uses of the public key (e.g., client authentication, server authentication). |
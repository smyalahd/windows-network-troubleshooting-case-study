# Network Connectivity Test

## Objective
Verify whether an HTTPS-related TCP connection can be established to a public test domain.

## Test
```powershell
Test-NetConnection example.com -Port 443
```

## Sanitized Result
```text
ComputerName     : example.com
RemoteAddress    : [IPv6 address redacted]
RemotePort       : 443
InterfaceAlias   : [network interface]
SourceAddress    : [source IP address redacted]
TcpTestSucceeded : True
```

## Interpretation
The TCP connection to the public test domain on port 443 succeeded at the time of testing.

This confirms connectivity to this specific endpoint only. It does not verify access to internal applications, DNS correctness in a corporate environment, or the overall health of a network.

## Evidence Type
Real local connectivity test. No internal incident was tested.

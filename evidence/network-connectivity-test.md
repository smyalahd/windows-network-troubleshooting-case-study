# Network Connectivity Test

## 1. Objective

Verify whether a TCP connection can be established to a public server on port 443.

**What I am doing:**  
I am checking whether my computer can establish a network connection to `example.com` on port 443, which is commonly used for HTTPS traffic.

## 2. Command

```powershell
Test-NetConnection example.com -Port 443
```

**Explanation:**
- `Test-NetConnection` is a PowerShell command used to test network connectivity.
- `example.com` is the destination hostname.
- `-Port 443` specifies the destination TCP port.
- Port 443 is commonly used by HTTPS services.

## 3. Sanitized Result

```text
ComputerName     : example.com
RemoteAddress    : [IPv6 address redacted]
RemotePort       : 443
InterfaceAlias   : [network interface]
SourceAddress    : [source IP address redacted]
TcpTestSucceeded : True
```

**What the output means:**
- **ComputerName:** The hostname I tested.
- **RemoteAddress:** The IP address selected for the destination.
- **RemotePort:** The destination port used for the test.
- **InterfaceAlias:** The local network interface used, such as Wi-Fi.
- **SourceAddress:** The local IP address used for the connection.
- **TcpTestSucceeded:** Indicates whether the TCP connection was established successfully.

## 4. Interpretation

The test succeeded because `TcpTestSucceeded` returned `True`.

This confirms that my computer could establish a TCP connection to the selected endpoint on port 443 at the time of testing.

It does not prove that a website's application is functioning correctly, that all HTTPS communication will succeed, or that an internal company application is reachable.

## 5. What I Learned

- A successful DNS lookup does not automatically guarantee that a TCP connection will succeed.
- `Test-NetConnection` helps investigate connectivity to a specific host and port.
- Port 443 is commonly used for HTTPS, but this command tests TCP connectivity rather than the full application-level HTTPS experience.
- Troubleshooting results should be interpreted in context and compared with the expected behavior.

## 6. Evidence Type

Real local connectivity test. No internal corporate application or incident was tested.

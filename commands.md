# Windows Network Troubleshooting Commands

Use these commands only on systems you own or are authorized to support. Replace example values with approved hostnames and ports.

## 1. `ipconfig /all`

**Purpose:** Inspect adapter state, IPv4/IPv6 configuration, default gateway, and configured DNS servers.

```powershell
ipconfig /all
```

**Look for:** An unexpected address, missing default gateway, disconnected adapter, or DNS server inconsistent with organizational configuration. Sanitize output before sharing; it may contain internal IPs, DNS suffixes, or device details.

## 2. `nslookup`

**Purpose:** Ask the configured DNS resolver to resolve a hostname.

```powershell
nslookup app.example.test
```

**Look for:** Whether a response is returned, which DNS server answered, and whether the result matches an approved reference. A successful lookup does not prove the application port is reachable.

## 3. `Test-NetConnection`

**Purpose:** Test TCP reachability to a specific documented port.

```powershell
Test-NetConnection app.example.test -Port 443
```

**Look for:** `TcpTestSucceeded`. A `False` result can have several causes, including routing, firewall rules, VPN, a stopped service, or an incorrect destination. It does not identify the cause by itself.

## 4. `ping` (optional)

```powershell
ping app.example.test
```

A ping checks ICMP reachability when ICMP is allowed. Some hosts block ICMP, so a failed ping does not automatically mean the host or application is unavailable.

## 5. Compare with a known-good endpoint

Repeat approved checks on a known-good device or account, if policy allows. Record differences rather than assuming the first unusual result is the root cause.

## Evidence checklist

- [ ] Time and time zone of each test
- [ ] Hostname tested (sanitize if confidential)
- [ ] DNS server and result (sanitize sensitive details)
- [ ] TCP port tested and `TcpTestSucceeded` result
- [ ] Whether other users/devices are affected
- [ ] User confirmation after resolution

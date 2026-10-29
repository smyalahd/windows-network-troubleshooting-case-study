# Windows Network Troubleshooting Case Study

A practical IT support portfolio project demonstrating structured troubleshooting of a Windows user's inability to access an internal business application. The project documents a repeatable diagnostic workflow, Windows networking commands, incident notes, and root-cause analysis.

> **Scope and honesty:** The internal application incident is a simulated training scenario, not a real customer incident. The network diagnostic tests in the `evidence/` folder were executed on a local Windows computer against the public domain `example.com`. No company systems or personal data were used.

## Scenario

A user reports:

"I cannot open the internal business application. It worked yesterday."

The objective is to isolate the likely failure layer without unnecessary changes: local connectivity, IP configuration, DNS resolution, TCP reachability, or the application/service itself.

## Troubleshooting Approach

1. **Clarify scope and impact:** Determine whether one user or multiple users are affected, whether one or several applications are unavailable, when the issue started, and whether any recent changes occurred.
2. **Check local network configuration:** Use `ipconfig /all` to review IP configuration, DNS servers, gateway, and network adapter details.
3. **Test DNS resolution:** Use `nslookup` to check whether the application hostname resolves to an IP address.
4. **Check basic connectivity:** Use `ping` when appropriate, while remembering that a failed ping alone does not prove a host is unavailable.
5. **Test TCP reachability:** Use `Test-NetConnection` to check connectivity to the documented application port.
6. **Compare results:** Compare findings with a known-good endpoint or the expected configuration.
7. **Document and escalate:** Record the symptoms, user impact, diagnostic results, actions, and next steps in the incident ticket.

## Repository Contents

- [`case-study.md`](case-study.md) — simulated investigation and root-cause analysis
- [`commands.md`](commands.md) — Windows diagnostic commands and interpretation
- [`incident-report.md`](incident-report.md) — example incident ticket and closure notes
- [`evidence/`](evidence/) — documented practical network diagnostic tests

## Practical Evidence

The following tests were executed on a local Windows computer against the public domain `example.com`. They are separate from the simulated internal application incident.

- [`network-connectivity-test.md`](evidence/network-connectivity-test.md) — tested TCP connectivity to port 443 using `Test-NetConnection`
- [`dns-lookup-test.md`](evidence/dns-lookup-test.md) — checked DNS name resolution using `nslookup`
- [`ping-connectivity-test.md`](evidence/ping-connectivity-test.md) — checked ICMP responses, round-trip time, and packet loss using `ping`

### Key Results

- **TCP connectivity:** The connection test to port 443 succeeded.
- **DNS resolution:** The domain resolved to multiple IPv4 and IPv6 addresses.
- **Ping connectivity:** Four replies were received, with 0% packet loss and an average round-trip time of 12 ms.

These results describe the local tests at the time they were performed. They do not establish the health of an internal corporate network or application.

## Quick Command Reference

Run these commands in PowerShell on a device you are authorized to troubleshoot. Replace example hostnames and ports with approved values when investigating a real incident.

```powershell
ipconfig /all
nslookup app.example.test
ping app.example.test
Test-NetConnection app.example.test -Port 443
```

### Command Purpose

| Command | Purpose |
|---|---|
| `ipconfig /all` | Review local IP configuration and network adapter details |
| `nslookup` | Investigate DNS name resolution |
| `ping` | Test ICMP responses and observe packet loss and response times |
| `Test-NetConnection` | Test TCP connectivity to a specified host and port |

## Key Learning Points

- Follow a layered troubleshooting method instead of guessing.
- Distinguish DNS resolution issues from TCP connectivity problems.
- Interpret command output in context; one failed test rarely proves the root cause.
- Make only authorized, low-risk checks before escalating.
- Document reproducible findings and next steps in clear incident notes.
- Separate verified technical evidence from simulated findings.

## Disclaimer

The internal application scenario and its example findings are illustrative. The domain `example.test` is reserved for testing and is not intended to identify a real internal service. The practical evidence files document separate tests against `example.com`.

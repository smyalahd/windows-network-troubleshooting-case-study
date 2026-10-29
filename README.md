# Windows Network Troubleshooting Case Study

A simulated IT support case study demonstrating structured troubleshooting of a Windows user's inability to access an internal business application. It documents a repeatable diagnostic workflow, Windows networking commands, incident notes, and root-cause analysis.

> **Scope and honesty:** This is a simulated training scenario, not a real customer incident. No company systems or personal data were used. Example findings are hypothetical and clearly labeled.

## Scenario

A user reports: "I cannot open the internal business application. It worked yesterday."

The objective is to isolate the likely failure layer without unnecessary changes: local connectivity, IP configuration, DNS resolution, TCP reachability, or the application/service itself.

## Troubleshooting approach

1. Clarify scope and impact: one user or multiple users, one application or several, when it started, and any recent changes.
2. Check local network configuration with `ipconfig /all`.
3. Test name resolution with `nslookup app.example.test`.
4. Remember that a failed ping alone does not prove a host is down.
5. Test the documented application port with `Test-NetConnection app.example.test -Port 443`.
6. Compare results with a known-good endpoint or escalate with evidence.
7. Record findings, user impact, actions, and next steps in the ticket.

## Repository contents

- [`case-study.md`](case-study.md) — simulated investigation and root-cause analysis
- [`commands.md`](commands.md) — Windows diagnostic commands and interpretation
- [`incident-report.md`](incident-report.md) — example incident ticket and closure notes
- [`evidence/`](evidence/) — place for sanitized screenshots or sample output

## Quick command reference

Run commands in PowerShell on a device you are authorized to troubleshoot. Replace example hostnames and ports with approved values.

```powershell
ipconfig /all
nslookup app.example.test
Test-NetConnection app.example.test -Port 443
```

## Key learning points

- Follow a layered troubleshooting method rather than guessing.
- Interpret command output in context; one failed test rarely proves root cause.
- Make only authorized, low-risk checks before escalating.
- Write concise, reproducible ticket notes.

## Disclaimer

All hostnames, symptoms, and results are illustrative. `example.test` is a reserved example domain and is not intended to identify a real internal service.

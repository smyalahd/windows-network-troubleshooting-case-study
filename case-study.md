# Case Study: User Cannot Access an Internal Application

## 1. Incident summary

**Type:** Application access / network troubleshooting  
**Status:** Simulated and resolved for training purposes  
**User impact:** One employee cannot open an internal business application

### User statement

> "The application worked yesterday, but today the page does not load."

## 2. Initial questions

- Is the issue affecting only this user, or are colleagues affected too?
- Is the user connected to the corporate LAN or approved VPN?
- Do other internal applications work?
- Does the issue occur in another browser or on another approved device?
- When did it start? Were there any recent password, VPN, network, or application changes?

These questions establish scope before making changes.

## 3. Diagnostic workflow

Use approved hostnames, ports, and procedures in a real environment.

| Step | Check | What it helps determine |
|---|---|---|
| 1 | `ipconfig /all` | IP address, gateway, DNS servers, adapter state |
| 2 | `nslookup app.example.test` | Whether the hostname resolves through configured DNS |
| 3 | `Test-NetConnection app.example.test -Port 443` | Whether TCP connectivity to the documented HTTPS port succeeds |
| 4 | Compare with a known-good user/device | Whether the issue is isolated or broader |
| 5 | Check service status or escalate | Whether the fault is beyond endpoint-level support |

A ping result is not definitive: ICMP may be blocked while the application remains reachable.

## 4. Simulated findings

**Illustrative findings only — not captured from a real network:**

- The local adapter is connected and has a valid IP configuration.
- The application hostname resolves to an unexpected address compared with an approved reference.
- TCP connectivity to the expected application port fails.
- A second user on the same network can access the application.

## 5. Hypothesis and root-cause analysis

**Most likely hypothesis in this simulated example:** a DNS record or DNS path issue affecting one endpoint or resolver.

This is a hypothesis, not a conclusion from symptoms alone. Validate the expected DNS answer with the authorized infrastructure team and compare resolver configuration and results. If DNS is correct, continue with routing, firewall, proxy, VPN, and application-service checks.An unexpected IP address is not automatically evidence of a DNS fault. Compare the result with an approved reference and account for legitimate load balancing, split DNS, and environment-specific records.

## 6. Resolution and validation

Do not edit DNS, flush caches, restart services, or change network settings without following approved procedures and authorization.

Example controlled resolution path:

1. Share timestamps, hostname, DNS server, resolved address, and TCP test output with the responsible team.
2. Have the authorized DNS/network team validate and correct the record or resolver path if confirmed.
3. Re-run name resolution and TCP reachability checks.
4. Ask the user to confirm the application opens.
5. Document the confirmed cause, fix, validation, and follow-up action.

## 7. What would change the diagnosis?

- If the hostname does not resolve: investigate DNS configuration, VPN, and resolver availability.
- If DNS resolves but TCP fails for many users: investigate routing, firewall, VPN, or service availability.
- If TCP succeeds but the application fails: investigate browser, authentication, proxy, TLS, or application-layer errors.
- If only one user is affected: compare local configuration and endpoint-specific settings with a known-good device.

## 8. Lessons learned

- Confirm scope and impact before changing anything.
- Use multiple signals and compare against a known-good endpoint.
- Keep facts separate from hypotheses.
- Escalate with evidence and document how service was validated.

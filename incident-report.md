# Example Incident Ticket

> This is a simulated ticket for portfolio and training purposes.

## Ticket details

- **Ticket ID:** DEMO-INC-001
- **Category:** Application access / network
- **Priority:** Assign using the organization's impact and urgency matrix
- **Status:** Resolved (simulated)
- **Affected user:** Demo user
- **Service:** Internal business application (example hostname only)

## User-reported issue

The user reports that the internal application no longer loads, although it worked on the previous business day.

## Impact and scope

Initial scope check indicates one user is affected. Other internal applications work. A colleague can access the application from a separate device. These are hypothetical details for the scenario.

## Troubleshooting performed

1. Reviewed local IP configuration using `ipconfig /all`.
2. Checked hostname resolution using `nslookup app.example.test`.
3. Tested TCP connectivity to the documented HTTPS port using `Test-NetConnection app.example.test -Port 443`.
4. Compared results with the approved reference and a known-good endpoint.

## Findings

In this simulated case, the DNS answer differs from the approved reference and the TCP test to the expected destination fails. This suggests a possible DNS-related issue but is not sufficient by itself to confirm root cause.

## Resolution / escalation

Escalated the evidence to the authorized DNS/network team for validation. In a real incident, record the team's confirmed action and do not mark the ticket resolved until connectivity and user access are verified.

## Closure note template

**Root cause:** [Insert confirmed cause; do not use a hypothesis as fact.]  
**Action taken:** [Document approved change or corrective action.]  
**Validation:** [Record DNS/TCP results and user confirmation.]  
**Follow-up:** [Record monitoring, prevention, or related problem ticket, if applicable.]

## Communication example

"Thanks for reporting this. I checked the endpoint's network configuration, DNS resolution, and TCP connectivity to the application's documented port. The results suggest a possible DNS-related issue, so I have escalated the evidence to the responsible team for confirmation. I will update the ticket once the cause is confirmed and access has been validated."

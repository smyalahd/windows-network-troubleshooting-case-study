# DNS Lookup Test

## 1. Objective
Check whether a domain name can be translated into IP addresses using DNS (Domain Name System).

**What I am doing:**  
I am checking whether my computer can find the IP addresses associated with `example.com`.

## 2. Command
```powershell
nslookup example.com
```

**Explanation:**
- `nslookup` is a command-line tool for querying DNS.
- `example.com` is the domain name I want to resolve.
- The command displays the DNS resolver used and the returned IP addresses.

## 3. Sanitized Result
```text
DNS server: [local DNS resolver details redacted]

Non-authoritative answer:
Name: example.com
Addresses:
  [IPv6 addresses returned]
  [IPv4 addresses returned]
```

**What the output means:**
- **DNS server:** The resolver that answered my query. My original output showed my local router, so I removed its details for privacy.
- **Non-authoritative answer:** The response was provided by a resolver or cache rather than directly by the domain's authoritative DNS server. This is normal.
- **Addresses:** The returned IPv4 and IPv6 addresses associated with the domain.

## 4. Interpretation
The DNS lookup succeeded because the domain name was resolved to multiple IP addresses.

This does not prove that every network service is working. It confirms only that DNS resolution worked for this public domain at the time of testing.

## 5. What I Learned
- DNS translates domain names into IP addresses.
- `nslookup` helps investigate potential name-resolution problems.
- A DNS result should be compared with the expected result and the affected environment before diagnosing a fault.

## 6. Evidence Type
Real local DNS lookup. No internal corporate application or incident was tested.

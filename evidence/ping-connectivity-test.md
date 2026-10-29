# Ping Connectivity Test

## 1. Objective

Check whether a destination host responds to ICMP Echo Requests and measure the round-trip time.

**What I am doing:**  
I am checking whether `example.com` responds to ping requests and whether packets are lost during this test.

## 2. Command

```powershell
ping example.com
```

**Explanation:**
- `ping` sends ICMP Echo Requests to the destination.
- `example.com` is the hostname being tested.
- By default, Windows sends four requests when pinging a hostname.

## 3. Sanitized Result

```text
Reply from [destination IP]: time=10ms
Reply from [destination IP]: time=9ms
Reply from [destination IP]: time=20ms
Reply from [destination IP]: time=9ms

Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)

Minimum = 9ms, Maximum = 20ms, Average = 12ms
```

## 4. Interpretation

All four ICMP Echo Requests received replies, resulting in 0% packet loss during this test. The average round-trip time was 12 ms.

**What the results mean:**
- **Sent / Received:** Number of requests sent and replies received.
- **Packet loss:** Requests that did not receive a reply during the test.
- **Minimum / Maximum:** Lowest and highest measured round-trip times.
- **Average:** Mean round-trip time across the successful replies.

## 5. Important Limitations

A successful ping indicates that the destination responded to ICMP requests at the time of testing.

It does not prove that a website or application is working correctly. Some hosts or firewalls block ICMP, so a failed ping does not necessarily mean the host is unavailable.

## 6. What I Learned

- `ping` helps test basic IP connectivity and observe packet loss and response times.
- `nslookup` checks DNS name resolution.
- `Test-NetConnection` checks TCP connectivity to a specified port.

Using these tests together can help narrow down a network issue, but results must be interpreted in context.

## 7. Evidence Type

Real local network test against a public domain. No internal corporate application or incident was tested.

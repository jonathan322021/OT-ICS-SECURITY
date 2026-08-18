# Troubleshooting Log

## Issue #001 - Jump Server cannot ping pfSense MGMT Interface

### Environment

| Asset | IP |
|--------|--------|
| pfSense MGMT | 192.168.30.1 |
| Jump Server | 192.168.30.10 |

### Symptoms

- pfSense can ping Jump Server.
- Jump Server cannot ping pfSense.
- HTTPS access to pfSense from MGMT network fails.

### Investigation

#### Network Configuration

Verified:

- VMnet4 configured correctly.
- pfSense OPT2 configured as 192.168.30.1/24.
- Jump Server configured as 192.168.30.10/24.
- Default gateway configured as 192.168.30.1.

#### Firewall Validation

Verified OPT2 firewall rule:

- Source: OPT2 net
- Destination: Any
- Protocol: Any
- Action: Pass

#### Ubuntu Checks

```bash
ip route
ip neigh
sudo ufw status
```

Results:

- Correct routing.
- ARP resolution successful.
- UFW disabled.

#### Packet Capture

Captured on pfSense OPT2:

```text
192.168.30.10 > 192.168.30.1 ICMP Echo Request
```

Result:

- pfSense receives ICMP requests.
- No ICMP replies observed.

### Lessons Learned

- Validated Layer 2 connectivity through ARP.
- Used packet capture for communication troubleshooting.
- Validated firewall rules.
- Reinforced understanding of IEC 62443 Zones and Conduits.

### IEC 62443 Concepts Practiced

- Zones
- Conduits
- Defense in Depth
- Network Segmentation
- Restricted Data Flow
- Troubleshooting of Secure Communications

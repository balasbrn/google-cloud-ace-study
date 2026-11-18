# Lab review: VPC Networking and Compute Engine

Course: Google Cloud Fundamentals: Core Infrastructure  
Lab: Get Started with Virtual Private Cloud Networking and Compute Engine  
Date reviewed: 2026-11-18

## What the lab demonstrates

- A project needs a VPC network to attach VM network interfaces. A VPC includes subnets, routes, and firewall policy.
- A VPC is global. Its subnets are regional, each with an internal IPv4 CIDR range and gateway.
- Auto mode VPCs create a subnet in each region. This is convenient for learning, while custom mode gives more control over subnet ranges and topology.
- Routes determine destinations and next hops. Firewall rules determine which traffic is allowed or denied. Successful connectivity requires both a route and an allowing firewall rule.
- Internal VM-to-VM connectivity across subnets/zones can use internal IP addresses and VPC routes. External IPs are not required for this private path.
- Ephemeral external IPs can change when a VM is stopped and restarted. Reserve a static IP when a stable address is required.

## Firewall rules and test results

| Test | Rule that permits the traffic in this lab |
|---|---|
| SSH to a Linux VM over TCP port 22 | `mynetwork-allow-ssh` |
| Ping a VM using ICMP, including its external IP | `mynetwork-allow-icmp` |
| Ping another VM using its internal IP | `mynetwork-allow-custom` |

**Lab question:** Which firewall rule allows ping to the VM's external IP?  
**Answer:** `mynetwork-allow-icmp`.

Removing a rule isolates its effect: removing allow-icmp blocks ping to the external address; removing allow-custom blocks internal ping; removing allow-ssh prevents SSH. These are ingress permissions on the destination VM/network targets.

The default network shown in the lab has broad SSH, RDP, and ICMP ingress examples. Treat those as lab defaults, not a production firewall pattern. Apply least privilege when designing real access.

## Commands to recognize

From a VM SSH terminal, the lab uses:

```bash
ping -c 3 <destination-ip>
exit
```

`-c 3` sends three ICMP echo requests. Ping may fail because of a missing route, firewall policy, or ICMP filtering. A failed ping alone does not prove that all application traffic is blocked.

## Exam cues

- Internal IP communication between VMs in the same VPC does not require external IPs.
- Auto mode creates regional subnets automatically. Custom mode is useful when you need explicit IP planning.
- Routes and firewalls do different jobs.
- Ingress means traffic entering a target. Egress means traffic leaving it.
- For SSH, check TCP:22 and the destination's matching firewall rule.
- For ping, check ICMP permissions. SSH permission does not permit ping.

## AWS comparison

GCP VPC ≈ AWS VPC. GCP subnet ≈ AWS subnet, though GCP subnets are regional and the overall GCP VPC network is global.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “Get Started with Virtual Private Cloud Networking and Compute Engine,” https://www.skills.google/paths/499/course_templates/60/labs/689567

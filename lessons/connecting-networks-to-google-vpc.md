# Connecting networks to Google VPC

Course: Google Cloud Fundamentals: Core Infrastructure  
ACE domain: Planning and implementing networking resources  
Lesson: Connecting networks to Google VPC  
Date studied: 2026-11-16

## The decision to make

Choose connectivity by asking:
1. Do both sides need private IP-to-private IP communication?
2. What bandwidth, performance, and availability are required?
3. Can you place and operate routing equipment at a Google point of presence, or would you rather use a service provider?

## Connectivity options

| Option | Path and addresses | Best fit | Key point |
|---|---|---|---|
| Cloud VPN | Encrypted IPsec tunnel over the internet; supports private network connectivity | Private connectivity when internet bandwidth/performance is sufficient | Cloud Router can exchange dynamic routes with BGP |
| Direct Peering | Network peers with Google at a Google point of presence for access to Google services | Public Google services when you have suitable colocation/network presence | Lesson says this is not covered by a Google SLA |
| Carrier Peering | Reach Google through a service provider | Public Google services when you need a provider intermediary | Provider is part of the path |
| Dedicated Interconnect | Direct physical private connection to Google | High-bandwidth private connectivity when you can provision equipment at a Google colocation facility | Redundant topology can qualify for an SLA; VPN can be backup |
| Partner Interconnect | Private connectivity through a supported service provider | Private connectivity when direct colocation is unavailable or capacity needs differ | Provider delivers part of the path; eligible topology may qualify for an SLA |
| Cross-Cloud Interconnect | Dedicated physical connectivity between Google Cloud and a supported other cloud | High-bandwidth multicloud connectivity | Current supported providers, bandwidth options, and encryption details should be checked in current docs |

## Cloud Router and BGP

Cloud Router exchanges route information dynamically using **BGP**. With a VPN, this can propagate newly added VPC subnet routes to the connected network without manually updating routes at each end.

Cloud Router exchanges control-plane route information. The VPN or Interconnect carries the traffic.

## Quick selection guide

- Need private addressing on both sides and internet-based connectivity is adequate → **Cloud VPN**.
- Need private, high-performance connectivity and can establish a physical presence at Google's colocation facility → **Dedicated Interconnect**.
- Need private, high-performance connectivity through a provider → **Partner Interconnect**.
- Need multicloud dedicated connectivity → **Cross-Cloud Interconnect**.
- Need access to Google public services without private address connectivity → consider **Direct Peering** or **Carrier Peering**, based on network presence and provider needs.

## AWS comparison

- Cloud VPN ≈ AWS Site-to-Site VPN.
- Dedicated Interconnect ≈ AWS Direct Connect.
- Partner Interconnect ≈ Direct Connect through a hosted connection provider.
- Cloud Router/BGP routing has analogues in AWS dynamic routing with BGP.

## Exam cues and freshness

- VPN uses an encrypted tunnel over the internet. Interconnect uses dedicated physical connectivity.
- Direct/Carrier Peering provide access to Google services and are distinct from private VPC connectivity products.
- BGP provides dynamic route exchange.
- SLA eligibility depends on topology and redundancy requirements.
- This video includes specific capacity and SLA figures that may change. Verify current product documentation for supported bandwidths, provider coverage, SLA terms, and configuration requirements.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “Connecting networks to Google VPC,” transcript supplied by the learner, https://www.skills.google/paths/499/course_templates/60/video/689566

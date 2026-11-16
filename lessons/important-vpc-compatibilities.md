# Important VPC compatibilities

Course: Google Cloud Fundamentals: Core Infrastructure  
ACE domain: Planning and implementing networking  
Lesson: Important VPC compatibilities  
Date studied: 2026-11-16

## Built-in routing

VPC networks have built-in routing tables, so you do not provision or manage a router for basic VPC routing. Routes can carry traffic between instances in the same network, across subnets, and between zones without requiring external IP addresses.

**Exam cue:** Internal communication can work using internal IPs when routes and firewall policy allow it. An external IP is for external reachability, not a requirement for all VM-to-VM communication.

## Distributed firewall

Google Cloud VPC provides a distributed firewall controlling ingress (incoming) and egress (outgoing) traffic to VM instances. Firewall rules can target instances by network tags. For example, a rule can allow TCP ports 80 and 443 to VMs tagged `WEB`, without listing each VM IP.

Remember to reason about direction, protocol, port, source or destination, and the rule's target. A matching firewall rule is needed in addition to a route.

## Connecting VPC networks and projects

The lesson introduces **VPC Network Peering** as a way to establish connectivity between two VPC networks so they can exchange traffic.

It then begins describing **Shared VPC** as an alternative when an organization needs to use IAM to control which users and resources in one project can use a VPC hosted in another project. The supplied transcript ends mid-sentence here. Review the full lesson or official docs for the complete Shared VPC discussion.

## AWS comparison

- GCP VPC routing and firewall rules have AWS VPC analogues, though rule evaluation and network architecture differ.
- VPC Network Peering ≈ AWS VPC Peering.
- Shared VPC is a centrally managed network shared across projects, broadly comparable to AWS VPC sharing patterns, with different IAM and resource models.

## Exam cues

- Built-in VPC routes mean no separate router needs to be created for ordinary internal routing.
- Internal VM traffic does not inherently require external IP addresses.
- Firewall rules can apply to VM groups through network tags.
- Peering connects networks. Shared VPC lets service projects use a centrally managed host-project network and is governed through IAM.
- Routes decide where traffic can go; firewalls decide whether traffic is allowed. Both can affect connectivity.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “Important VPC compatibilities,” transcript supplied by the learner, https://www.skills.google/paths/499/course_templates/60/video/689563

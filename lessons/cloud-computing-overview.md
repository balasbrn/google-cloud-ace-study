# Cloud computing overview

Course: Google Cloud Fundamentals: Core Infrastructure  
Lesson: Cloud computing overview  
Exam domain: Foundation for all ACE domains  
Date studied: 2026-11-10

## Five core traits

1. **On-demand self-service** — provision compute, storage, or networking through an interface without provider staff manually handling each request.
2. **Broad network access** — access services over networks using standard client devices.
3. **Resource pooling** — provider resources are pooled and assigned dynamically. Users generally do not choose the exact physical host.
4. **Rapid elasticity** — scale resources up or down quickly as demand changes.
5. **Measured service** — usage is metered, enabling pay-for-use or reservation-based billing.

Remember: self-service, network access, pooled resources, elasticity, and measured usage.

## Infrastructure evolution covered

- **Colocation** rents physical data-center space. The customer still owns or manages the hardware.
- **Virtualized data centers** provide virtual servers, disks, and networks, while customers retain more infrastructure configuration and operations responsibility.
- **Container-based and managed cloud services** automate more provisioning and configuration, allowing teams to focus more on applications and data.

## When this matters

Elasticity supports workloads with changing demand. Managed services can reduce infrastructure operations. Metering helps connect resource consumption to cost. Stopping one workload does not necessarily stop charges for separately provisioned persistent resources.

## AWS comparison

These five traits apply across cloud providers. AWS has analogous compute, object storage, networking, and metered billing services. These are conceptual equivalents, not exact feature matches.

## Exam cues

- Provision automatically without waiting for staff → on-demand self-service.
- Scale quickly with demand → elasticity.
- Provider dynamically assigns resources from a shared pool → resource pooling.
- Pay according to measured consumption → measured service.
- Virtual machines leave the customer with more OS and configuration responsibility than higher-level managed services.

## Quick review

A batch workload grows sharply at month end and is quiet during the rest of the month. Which cloud characteristic best supports matching capacity to changing demand?

**Answer:** Rapid elasticity.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “Cloud computing overview,” https://www.skills.google/paths/499/course_templates/60/video/689545

# Cloud DNS and Cloud CDN

Course: Google Cloud Fundamentals: Core Infrastructure  
ACE domains: Planning and implementing networking; ensuring successful operation  
Lesson: Cloud DNS and Cloud CDN  
Date studied: 2026-11-16

## Cloud DNS

DNS maps human-readable hostnames to network addresses. **Cloud DNS** is Google's managed, programmable DNS service for publishing and managing DNS zones and records. It can be managed through the Console, CLI, or API, and serves DNS data from redundant locations.

The public resolver **8.8.8.8** is a separate Google-operated public DNS service. Cloud DNS is for hosting and managing DNS records for domains and services.

## Cloud CDN

A **content delivery network (CDN)** caches content at edge locations closer to end users. Cloud CDN can reduce user-perceived latency, reduce load on the origin, and potentially reduce delivery costs.

The lesson describes enabling Cloud CDN on an Application Load Balancer and notes that other CDN providers can also be used, including providers connected through Google's CDN Interconnect partner program.

## How to choose

| Need | Service |
|---|---|
| Publish DNS records and manage zones for a domain | Cloud DNS |
| Resolve hostnames using a public recursive resolver | Public DNS resolver such as 8.8.8.8 |
| Cache content nearer to users and reduce origin requests | Cloud CDN or another CDN |

DNS resolution directs a client to a destination. CDN caching serves eligible content from edge caches. They solve related but different delivery problems.

## AWS comparison

- Cloud DNS ≈ Amazon Route 53.
- Cloud CDN ≈ Amazon CloudFront.

## Exam cues

- DNS translates hostnames to IP addresses.
- Cloud DNS is managed authoritative DNS hosting and programmable zone/record management.
- A CDN caches content near users to lower latency and origin load.
- Cloud CDN integration with a load balancer does not mean DNS and CDN are the same service.
- Product configuration, supported load balancers, and pricing can change. Verify current docs when implementing.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “Cloud DNS and Cloud CDN,” transcript supplied by the learner, https://www.skills.google/paths/499/course_templates/60/video/689565

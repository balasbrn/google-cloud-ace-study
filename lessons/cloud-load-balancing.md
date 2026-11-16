# Cloud Load Balancing

Course: Google Cloud Fundamentals: Core Infrastructure  
ACE domain: Planning and implementing networking  
Lesson: Cloud Load Balancing  
Date studied: 2026-11-16

## Purpose

A load balancer distributes client traffic across multiple application instances. This helps applications handle changing demand and reduces the risk of performance problems when traffic is uneven or backends become unhealthy.

Cloud Load Balancing is a managed, software-defined service. Google operates and scales the load-balancing infrastructure, so you do not run the balancer on your own VM.

The lesson emphasizes cross-region balancing, health-aware traffic distribution and failover, and no requirement to request pre-warming ahead of an expected traffic spike. Verify exact behavior and product scope against current documentation.

## Main decision: application or network

| Type | OSI layer and traffic | Connection behavior | Typical fit |
|---|---|---|---|
| Application Load Balancer | Layer 7, HTTP and HTTPS | Reverse proxy. Can terminate TLS and route based on application-level rules such as host or path. | Web applications needing URL-aware routing |
| Proxy Network Load Balancer | Layer 4, TCP and other supported traffic | Terminates client connection and creates a separate backend connection. | Proxy-based TCP services and advanced traffic management |
| Passthrough Network Load Balancer | Layer 4, TCP, UDP, and supported IP protocols | Forwards packets without terminating the client connection. Preserves the original source IP. | Direct server return or protocols needing passthrough behavior |

Application and network load balancers can have internal or external configurations, depending on the product. Select scope and regional or global behavior based on where clients and backends are located.

## Selection checklist

1. Is the traffic HTTP or HTTPS and does routing need to inspect host/path or other HTTP information? Consider an Application Load Balancer.
2. Is it TCP/UDP or another IP protocol? Consider a Network Load Balancer.
3. Must the backend see the original client source IP and keep the connection unproxied? Consider passthrough.
4. Should the load balancer terminate client connections and proxy to backends? Consider proxy.
5. Do clients or backends span regions? Check the appropriate global or regional product and its failover behavior.

## AWS comparison

- Application Load Balancer ≈ AWS ALB.
- Proxy Network Load Balancer is a Layer 4 proxy pattern. Compare AWS NLB capabilities and proxy requirements carefully.
- Passthrough Network Load Balancer is a Layer 4 forwarding pattern. It is not a one-to-one match for every AWS NLB mode.

## Exam cues

- Content-based HTTP(S) routing and TLS termination → Layer 7 Application Load Balancer.
- TCP/UDP transport traffic → Network Load Balancer.
- Preserve the original source IP and do not terminate the connection → passthrough.
- Terminate and proxy connections → proxy.
- Load balancing distributes traffic; autoscaling changes the number of backend instances. They work together but solve different problems.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “Cloud Load Balancing,” transcript supplied by the learner, https://www.skills.google/paths/499/course_templates/60/video/689564

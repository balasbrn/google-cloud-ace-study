# The Google Cloud network

Course: Google Cloud Fundamentals: Core Infrastructure  
ACE links: regions and zones, location selection, availability, durability, latency  
Date studied: 2026-11-10

## Core concepts

Google Cloud runs services on a global private network with caching locations that can serve frequently requested content nearer to users. Location choices affect **availability, durability, and latency**. Latency is the time for information to travel from source to destination.

- A **region** is an independent geographic area containing multiple zones.
- A **zone** is a deployment area within a region. Zonal resources such as a VM are placed in a specified zone.
- **Multi-region** is available for some services and can replicate data across zones in multiple regions according to the product's configuration.

## How to choose a location

- Choose a region near users or dependent services when low latency matters.
- Spread appropriate resources across zones to reduce exposure to a single-zone failure.
- Consider multiple regions or a supported multi-region design for regional resilience and geographic access.
- Check that the specific product and configuration are available in the chosen location. Location inventory changes, so verify current availability in Google's locations documentation.

More geographic distribution can improve resilience or user proximity, while introducing design and cost considerations. The exact behavior depends on the service. A region is not automatically a multi-region deployment.

## AWS comparison

- GCP region ≈ AWS Region.
- GCP zone ≈ AWS Availability Zone.
- Multi-region replication concepts exist in both clouds, but implementation and service guarantees differ.

## Exam cues

- **Zone** is the placement/failure domain for many zonal resources.
- **Region** groups zones in one geographic area.
- Multi-zone resilience does not by itself protect against a regional outage.
- Multi-region capabilities are service-specific. Check product location behavior rather than assuming every resource supports it.
- Confirm the current location list and service availability before choosing.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “The Google Cloud network,” https://www.skills.google/paths/499/course_templates/60/video/689547

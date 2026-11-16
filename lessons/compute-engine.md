# Compute Engine

Course: Google Cloud Fundamentals: Core Infrastructure  
ACE domain: Planning and implementing compute  
Lesson: Compute Engine  
Date studied: 2026-11-16

## What it is

Compute Engine is Google Cloud's Infrastructure as a Service (IaaS) offering. It lets you create and run virtual machines on Google infrastructure, selecting the operating system, CPU, memory, and storage.

## Creating and configuring VMs

You can create instances through the Cloud Console, Google Cloud CLI, or Compute Engine API. Use Google-provided Linux and Windows Server images, customized images, or supported other operating systems. Choose a predefined machine type or configure a custom machine type with the CPU and memory your workload needs.

Cloud Marketplace can deploy a preconfigured stack, including software, VM, storage, and networking setup. Check the estimated monthly price before launch because some third-party licensed images add software charges on top of normal infrastructure usage.

## Pricing and discounts from this lesson

- VM compute is billed by the second with a one-minute minimum.
- Sustained-use discounts can apply automatically to eligible VMs running a significant portion of the month.
- Committed-use discounts suit predictable workloads in exchange for a one-year or three-year commitment.
- Spot VMs can reduce cost substantially for interruptible workloads. Google may stop them when capacity is needed elsewhere, so applications must handle interruption and resume safely.
- Spot VMs have no fixed maximum runtime, but availability is not guaranteed.
- Custom machine types let you pay for a closer fit to CPU and memory needs.

Pricing percentages and terms in course videos can become outdated. Verify current rates, eligibility, and discount rules in official Google Cloud pricing documentation before making a cost estimate.

## Storage and performance point

The lesson states that high throughput between Compute Engine processing and persistent disks is available by default without choosing a special machine type or storage option. For a real design, check the specific disk type, VM limits, and current performance documentation.

## How to choose

| Need | Consider |
|---|---|
| Full operating-system control or software requiring a VM | Compute Engine |
| Stable, predictable long-running capacity | Standard VMs and evaluate committed-use discounts |
| Flexible background batch work that can restart | Spot VMs |
| CPU and memory combination unlike available presets | Custom machine type |
| Fast setup of a known software stack | Cloud Marketplace image, after checking software charges |

## AWS comparison

Compute Engine VMs ≈ Amazon EC2 instances.

## Exam cues

- Spot means lower cost with interruption risk. Design for restart or checkpointing.
- Marketplace deploys preconfigured solutions. Review software licensing charges separately from VM charges.
- Custom machine types specify CPU and memory to fit the workload.
- Compute Engine is IaaS, so the customer manages the guest operating system and software stack.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, “Compute Engine,” transcript supplied by the learner, https://www.skills.google/paths/499/course_templates/60/video/689561

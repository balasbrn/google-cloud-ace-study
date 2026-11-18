# Cloud Storage

Course: Google Cloud Fundamentals: Core Infrastructure  
Topic: Cloud Storage  
Reviewed: 2026-11-18

## What it is

Cloud Storage is Google's managed object storage for unstructured data. Objects contain data plus metadata and are addressed by a unique object name within a bucket. It suits media, website assets, backups, archives, data lakes, and intermediate workflow results.

**AWS equivalent:** Cloud Storage ≈ Amazon S3.

## Buckets, locations, and objects

- A bucket name must be globally unique. Choose its location based on residency, availability, and latency needs; for a Europe-focused workload, consider an appropriate European region or EU multi-region.
- Bucket locations are regional, dual-region, or multi-region. Location choices and data placement affect resilience, latency, and cost; verify current options and pricing in official docs.
- Objects are effectively immutable: replacing an object creates a new generation. Without Object Versioning, the prior live version is replaced; with it enabled, prior generations can be retained and restored.
- Object Versioning can increase storage charges. Use lifecycle rules to control old generations and delete/transition objects according to retention needs.

## Access and protection

- Prefer IAM for most access control; project-level grants can be inherited by buckets and objects. Grant least privilege.
- ACLs provide finer-grained legacy/per-object access control when needed. Avoid mixing IAM and ACL approaches without understanding the bucket's access model.
- A lifecycle policy can delete objects by age or creation date, keep only a set number of noncurrent versions, or transition data between storage classes. Lifecycle actions may take time to execute and are not an immediate cleanup command.
- For production data, consider retention policies, soft delete, object versioning, and backups according to recovery requirements; these are distinct protections and can affect cost.

## Commands to recognize

```bash
# Create a bucket in a chosen location
gcloud storage buckets create gs://BUCKET_NAME --location=LOCATION

# Copy a local file to a bucket
gcloud storage cp ./file gs://BUCKET_NAME/path/file

# List objects
gcloud storage ls gs://BUCKET_NAME/**

# Enable object versioning
gcloud storage buckets update gs://BUCKET_NAME --versioning

# Inspect object generations / versions
gcloud storage ls --all-versions gs://BUCKET_NAME/path/**
```

The older `gsutil` syntax is still commonly encountered in learning material, for example `gsutil cp` and `gsutil versioning set on gs://BUCKET_NAME`. Prefer the current `gcloud storage` command group for new workflows; check official CLI docs for exact flags.

## Exam cues and gotchas

- Object storage is not a mounted file system or raw block disk. Use a file system or persistent disk when an application needs those semantics.
- A bucket is a global namespace resource with a chosen geographic location; objects inherit bucket-level characteristics.
- Versioning supports recovery from overwrite/deletion but retains billable old generations until removed or lifecycle-managed.
- Lifecycle management automates retention and class transitions; it does not itself guarantee legal retention or prevent deletion.
- IAM is usually the first access-control choice. Use least privilege and avoid public access unless explicitly required.
- Storage classes (Standard, Nearline, Coldline, Archive) trade storage price against access frequency, retrieval fees, and minimum storage duration. Pick by expected access pattern; check current pricing and rules before the exam.

## Running example

For `crypto-ml-filter`, Cloud Storage can hold durable copies of datasets and model artifacts. Versioning can help recover overwritten objects; a lifecycle rule can expire stale intermediate data. Keep credentials and sensitive records out of public buckets.

## Source

Google Skills, Google Cloud Fundamentals: Core Infrastructure, Cloud Storage video transcript (provided by learner).

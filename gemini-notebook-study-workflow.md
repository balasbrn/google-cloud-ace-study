# Gemini Notebook study workflow

## Goal
Use Gemini Notebook as a study companion for the Google Cloud Associate Cloud Engineer (ACE) exam. Keep the official exam guide as the source of truth and organize notes by its four domains.

## Workflow
1. Add or select trustworthy source material, prioritizing official Google Cloud documentation and the current ACE exam guide.
2. Ask Notebook to summarize each source in plain language and map claims to the relevant ACE exam domain and subtopic.
3. For each service, capture what it does, when to choose it, alternatives, AWS equivalent, important commands, limits, pricing or location gotchas, and source links.
4. Compare sources when information differs. Flag uncertain or time-sensitive details for verification in official docs.
5. Turn notes into retrieval practice: ask for one multiple-choice question at a time, answer before revealing the explanation, and record missed concepts as weak spots.
6. Review weak spots in later sessions and update the main ACE notes only with validated, reusable learning.

## Prompt template

> I am preparing for the Google Cloud Associate Cloud Engineer exam. Use only the sources in this notebook and prioritize the latest official ACE exam guide. Explain [topic] concisely. Organize it under the matching exam domain and subtopic. Include what it is, when to choose it over alternatives, key gcloud/gsutil/kubectl commands with useful flags, exam-relevant limits and gotchas, and the closest AWS equivalent. Cite the source for each important claim. Flag anything that may have changed or cannot be confirmed from the sources. Finish with one original multiple-choice question and wait for my answer before explaining it.

## GPU vs TPU quick comparison

| Cloud GPUs | Cloud TPUs |
|---|---|
| General-purpose parallel accelerators with broad framework and library support. Useful for flexible workloads, custom models, and varied development workflows. | Google-designed tensor processors optimized for matrix-heavy machine-learning workloads at scale. Software compatibility and supported model paths matter when choosing them. |
| AWS comparison: broadly analogous to GPU instances such as EC2 accelerated computing instances. | AWS comparison: broadly analogous in purpose to specialized ML accelerators such as AWS Trainium or Inferentia, with different software and hardware ecosystems. |

Choose based on framework/operator support, model shape, performance needs, scale, availability, and total cost. Verify current accelerator availability and software support in Google Cloud documentation before deployment.

## Source

- User-provided Gemini Notebook infographic, “Cloud GPUs vs. Cloud TPUs: AI Accelerator Comparison,” shared November 10, 2026.
- Google Cloud ACE exam guide: https://services.google.com/fh/files/misc/associate_cloud_engineer_exam_guide_english.pdf

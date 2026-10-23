---
title: "Temporal Serverless Workers on Cloud Run: Scale workers ahead of demand"
url: "https://cloud.google.com/blog/products/serverless/temporal-serverless-workers-on-cloud-run-worker-pools/"
date: "2026-10-15"
author: "Sagar Randive"
feed_url: "https://cloudblog.withgoogle.com/products/application-development/rss/"
---
The open-source Temporal execution platform is rapidly becoming a foundational layer of modern software infrastructure — especially for orchestration in distributed systems and AI agent workloads. However, deploying and scaling workers in Temporal comes with unique challenges. Workers poll for tasks instead of serving requests, so request-driven serverless platforms can be an awkward fit.

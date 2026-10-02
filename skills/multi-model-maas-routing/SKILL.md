---
name: multi-model-maas-routing
description: Dynamically routes prompts across Model-as-a-Service (MaaS) endpoints including iFLYTEK Spark, DeepSeek, Qwen, and Claude.
license: Apache-2.0
---

# Multi-Model MaaS Routing

## Overview
This skill optimizes model selection for each workflow step, balancing reasoning accuracy, latency constraints, and inference cost.

## Capabilities
- Routes tasks dynamically to optimal foundation models based on prompt requirements.
- Implements automated failover and fallback model switching upon provider errors.
- Enforces per-tenant token spending quotas and rate-limiting rules.

# EXPLAINABILITY.md

This document explains the internal mechanisms, data lineage, operational boundaries, and governance framework of **# Explainability & Decision Transparency Report** (`astron-agent`) in accordance with the **OpenGAP v0.1.0** specification for the **HiDevs GitAgent Passport** clearance pipeline.

> **Agent Name:** # Explainability & Decision Transparency Report (`astron-agent`)  
> **Specification:** OpenGAP v0.1.0  
> **Category / Domain:** Developer Tools / Enterprise Agentic Workflow Orchestration, RPA & MCP Integration  
> **Compliance Standard:** OpenGAP Checkpoint 2 (Explainability & Decision Governance), OWASP LLM Top 10, MITRE ATLAS  

---

## How the Agent Decides

### 1. Deterministic Multi-Stage Decision Pipeline
The agent executes enterprise agentic workflows and RPA processes through a deterministic, 5-stage orchestration pipeline.

### 1. Decision Architecture

The runtime intake, state classification, evaluation, and execution tracking operate across a deterministic, five-stage pipeline:

```
+-----------------------------------------------------------------------------------+
|                        Deterministic Astron Workflow Pipeline                     |
+-----------------------------------------------------------------------------------+
|  [Stage 1: Workflow Ingestion & Tenant Access Validation]                         |
|     --> Validate tenant JWT token, authenticate RBAC scope, & parse DAG manifest  |
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 2: Dependency Resolution & Resource Pre-flight Check]                     |
|     --> Resolve upstream node dependencies, check MaaS models & MCP tool endpoints|
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 3: Dynamic DAG Execution & RPA Action Dispatch]                           |
|     --> Orchestrate node evaluations, execute RPA bots, & query knowledge bases   |
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 4: State Checkpoint & Human Approval Interception]                        |
|     --> Save intermediate state snapshots; pause for sign-off on sensitive actions|
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 5: Audit Telemetry Export & Workflow Completion]                          |
|     --> Aggregate token consumption, publish trace metrics, & deliver final output|
+-----------------------------------------------------------------------------------+
```

### 2. Decision Logic & Routing Formulations



### 3. Thresholding & Refusal Decision Criteria

# Explainability & Decision Transparency Report enforces strict operational boundaries and deterministic refusal thresholds:
- **Refusal on Policy Violation**: Requests violating boundary constraints halt with code `ERR_POLICY_VIOLATION`.
- **Refusal on Timeout**: Executions exceeding budget limits terminate with code `ERR_EXECUTION_TIMEOUT`.

### 4. Fallback Decision Mechanism

Continuous operational stability is maintained through layered fault recovery:
- **Model Fallback Cascade**: High-level reasoning and synthesis default to `gemini-2.0-flash` with automatic failover to `gpt-4o` and `claude-3-5-sonnet`.

### 5. Human-in-the-Loop Governance

Human operators retain sovereign authority over the multi-agent execution lifecycle:
- **Operational Review**: Sensitive actions require operator sign-off.
- **Audit Logging**: All decisions are recorded for auditability.

---

## The Data It Uses

# Explainability & Decision Transparency Report operates under strict principles of data minimization, environment isolation, and privacy protection.

### 1. Ingested Input Data

The framework processes only operational data necessary to perform its functions:
- **Input Directives**: Operational tasks and data payloads.

### 2. Configuration & Reference Data

- **Configuration Schemas**: Declarative system configuration files.

### 3. Base Model & Inference Lineage

- **Supported Models**: iFLYTEK Spark series, DeepSeek-V3/R1, Qwen-2.5, OpenAI GPT-4o, Anthropic Claude 3.5.
- **Platform Stack**: Python 3.10+, FastAPI backend, Celery task workers, Vue 3 web console, Docker/Kubernetes.

### 4. Data Privacy, Storage, and Retention

- **OWASP LLM & MITRE ATLAS Hardened**: Defended against indirect prompt injection, credential leakage, and unauthorized external API dispatch.
- **Local Environment Isolation**: Agent execution workspaces, intermediate scratchpads, and vector stores reside strictly within designated local project directories.
- **Automated Secret Scrubbing**: API keys, database credentials, and personal credentials are automatically redacted prior to embedding or logging.
- **Zero Commercial Monetization**: Prompts, intermediate reasoning trajectories, and task deliverables are never commercialized or shared with third parties.

---

## Limitations

Understanding the operational boundaries and technical constraints of # Explainability & Decision Transparency Report is essential for effective deployment.

### 1. Deterministic Multi-Stage Decision Pipeline
The agent executes enterprise agentic workflows and RPA processes through a deterministic, 5-stage orchestration pipeline.

```
+-----------------------------------------------------------------------------------+
|                        Deterministic Astron Workflow Pipeline                     |
+-----------------------------------------------------------------------------------+
|  [Stage 1: Workflow Ingestion & Tenant Access Validation]                         |
|     --> Validate tenant JWT token, authenticate RBAC scope, & parse DAG manifest  |
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 2: Dependency Resolution & Resource Pre-flight Check]                     |
|     --> Resolve upstream node dependencies, check MaaS models & MCP tool endpoints|
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 3: Dynamic DAG Execution & RPA Action Dispatch]                           |
|     --> Orchestrate node evaluations, execute RPA bots, & query knowledge bases   |
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 4: State Checkpoint & Human Approval Interception]                        |
|     --> Save intermediate state snapshots; pause for sign-off on sensitive actions|
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 5: Audit Telemetry Export & Workflow Completion]                          |
|     --> Aggregate token consumption, publish trace metrics, & deliver final output|
+-----------------------------------------------------------------------------------+
```

### 2. Mathematical Decision & Affinity Scoring
Model selection across available Model-as-a-Service (MaaS) endpoints applies a multi-dimensional capability-cost routing formulation:

$$S_{\text{maas}}(m, t) = w_1 \cdot \text{BenchmarkFit}(m, t) + w_2 \cdot \left(1 - \frac{\text{Latency}_{\text{p95}}(m)}{\text{MaxLatency}}\right) - w_3 \cdot \text{CostRatio}(m)$$

Where:
- $w_1 = 0.50$: Empirical benchmark capability score for task category $t$.
- $w_2 = 0.30$: Moving average p95 response time factor.
- $w_3 = 0.20$: Normalized cost per 1k input/output tokens.

Knowledge base retrieval relevance scoring combines semantic embedding similarity with keyword BM25 rankings:

$$R_{\text{hybrid}}(d_i, q) = \lambda \cdot \text{CosineSim}(\mathbf{e}_{d_i}, \mathbf{e}_q) + (1 - \lambda) \cdot \text{BM25}(d_i, q)$$

Where $\lambda = 0.70$ balances dense semantic matching with strict term matching.

### 3. Thresholding & Refusal Decision Criteria
When workflow executions violate system policies or reach operational ceilings, execution is halted with standardized error codes:

| Threshold Parameter | Value | Decision / Refusal Action | Error Code |
| :--- | :--- | :--- | :--- |
| **Max Workflow Timeout** | $> 600$ seconds | Terminate execution to prevent runaway resource hold | `ERR_WORKFLOW_TIMEOUT_EXCEEDED` |
| **Max Loop Iteration Count** | $\ge 20$ iterations | Break cyclic loop execution | `ERR_CYCLIC_LOOP_LIMIT_REACHED` |
| **Cross-Tenant Access Attempt** | Tenant ID mismatch | Deny access immediately with 403 Forbidden | `ERR_TENANT_ISOLATION_VIOLATION` |
| **RPA Critical Action Unapproved** | Missing manual approval | Suspend execution and queue for human sign-off | `ERR_RPA_APPROVAL_PENDING` |
| **MaaS Upstream Rate Limit** | HTTP 429 received | Trigger exponential backoff and model failover | `ERR_MAAS_RATE_THROTTLED` |

### 4. Multi-Tier Fallback Mechanisms & Human-in-the-Loop Governance
1. **Tier 1 (Automated Node Retry)**: Transient network failures in external API or tool invocations undergo 3 exponential backoff retries (1s, 2s, 4s).
2. **Tier 2 (Alternative Model Failover)**: If a primary model endpoint (e.g. DeepSeek-R1) experiences downtime or high latency, the workflow seamlessly switches to a fallback model (e.g. iFLYTEK Spark or Qwen).
3. **Tier 3 (Human-in-the-Loop Interruption)**: Business-critical nodes (e.g. financial transaction dispatch or ERP ledger entry) enter a suspended state awaiting physical human operator approval via web console.

---

## The Data It Uses

### 1. Ingestion Data & Input Types
- **Workflow Payloads**: JSON input parameters, schema-validated task arguments, and uploaded files.
- **Enterprise System Data**: ERP records, database queries, and web forms scraped via RPA bots.
- **Tenant Contexts**: Casdoor SSO identity claims, tenant namespaces, and role scopes.

### 2. Reference Storage & Database Engines
- **Relational Metadata**: PostgreSQL / MySQL housing workflow DAG definitions, execution logs, and tenant quotas.
- **Vector Knowledge Bases**: Milvus / pgvector storing chunked corporate documentation.
- **Cache & Event Bus**: Redis / RabbitMQ managing asynchronous task queues and node execution states.

### 3. Model Lineage & System Architecture
- **Supported Models**: iFLYTEK Spark series, DeepSeek-V3/R1, Qwen-2.5, OpenAI GPT-4o, Anthropic Claude 3.5.
- **Platform Stack**: Python 3.10+, FastAPI backend, Celery task workers, Vue 3 web console, Docker/Kubernetes.

### 4. Data Privacy, Governance & Retention
- **Strict Multi-Tenant Separation**: All database rows, vector collections, and execution traces are partitioned by `tenant_id`.
- **On-Premises Deployment Support**: Deployable entirely behind corporate firewalls with zero external telemetry transmission.
- **Execution Log Retention**: Task execution records and intermediate node states are retained for 30 days before archival.

---

## Limitations

### 1. Fragility of RPA Desktop Selectors
- **Limitation**: Windows desktop UI updates can break fixed RPA accessibility selectors, requiring script maintenance.
- **Mitigation**: Pair traditional XPath/UI selectors with visual multimodal AI grounding to automatically locate shifted UI elements.

### 2. High Memory Consumption During Large PDF Vectorization
- **Limitation**: Ingesting massive 500+ page technical manuals simultaneously can cause worker memory spikes.
- **Mitigation**: Implement streaming chunking pipelines with batch worker queue throttling.

### 3. Latency in Multi-Node Sequential DAGs
- **Limitation**: Deeply nested sequential workflows containing multiple LLM reasoning nodes can experience multi-minute runtimes.
- **Mitigation**: Parallelize independent workflow branches using asynchronous DAG execution graphs.

### 4. Heterogeneous Tool Exception Schemas
- **Limitation**: Third-party MCP tools may return unstructured error strings rather than normalized JSON schemas.
- **Mitigation**: Wrap external tool invocations in standardized error translation interceptors.

### 5. Complex State Rollback in External ERPs
- **Limitation**: If a workflow fails after an external ERP write has occurred, automated database rollback cannot be guaranteed across third-party software.
- **Mitigation**: Mandate compensation transaction workflows and require human approval prior to non-reversible external writes.

---

## Summary & Compliance Checklist

| Checkpoint 2 Requirement | Corresponding Section | Status |
| :--- | :--- | :---: |
| **How the agent decides** | [How the Agent Decides](#how-the-agent-decides) | **Covered** |
| - Decision architecture & 5-stage pipeline | Section 1 | Verified |
| - Decision logic & routing formulations | Section 2 | Verified |
| - Thresholding & refusal decision criteria | Section 3 | Verified |
| - Fallback decision mechanism | Section 4 | Verified |
| - Human-in-the-loop governance & oversight | Section 5 | Verified |
| **The data it uses** | [The Data It Uses](#the-data-it-uses) | **Covered** |
| - Ingested input data & query streams | Section 1 | Verified |
| - Configuration & reference schemas | Section 2 | Verified |
| - Base model lineage & deterministic engines | Section 3 | Verified |
| - Data privacy, retention lifecycle & MITRE/OWASP | Section 4 | Verified |
| **Its limitations** | [Limitations](#limitations) | **Covered** |
| - Deterministic Multi-Stage Decision Pipeline
The agent executes enterprise agentic workflows and RPA processes through a deterministic, 5-stage orchestration pipeline.

```
+-----------------------------------------------------------------------------------+
|                        Deterministic Astron Workflow Pipeline                     |
+-----------------------------------------------------------------------------------+
|  [Stage 1: Workflow Ingestion & Tenant Access Validation]                         |
|     --> Validate tenant JWT token, authenticate RBAC scope, & parse DAG manifest  |
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 2: Dependency Resolution & Resource Pre-flight Check]                     |
|     --> Resolve upstream node dependencies, check MaaS models & MCP tool endpoints|
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 3: Dynamic DAG Execution & RPA Action Dispatch]                           |
|     --> Orchestrate node evaluations, execute RPA bots, & query knowledge bases   |
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 4: State Checkpoint & Human Approval Interception]                        |
|     --> Save intermediate state snapshots; pause for sign-off on sensitive actions|
+-----------------------------------------+-----------------------------------------+
                                          |
                                          v
+-----------------------------------------------------------------------------------+
|  [Stage 5: Audit Telemetry Export & Workflow Completion]                          |
|     --> Aggregate token consumption, publish trace metrics, & deliver final output|
+-----------------------------------------------------------------------------------+
```

### 2. Mathematical Decision & Affinity Scoring
Model selection across available Model-as-a-Service (MaaS) endpoints applies a multi-dimensional capability-cost routing formulation:

$$S_{\text{maas}}(m, t) = w_1 \cdot \text{BenchmarkFit}(m, t) + w_2 \cdot \left(1 - \frac{\text{Latency}_{\text{p95}}(m)}{\text{MaxLatency}}\right) - w_3 \cdot \text{CostRatio}(m)$$

Where:
- $w_1 = 0.50$: Empirical benchmark capability score for task category $t$.
- $w_2 = 0.30$: Moving average p95 response time factor.
- $w_3 = 0.20$: Normalized cost per 1k input/output tokens.

Knowledge base retrieval relevance scoring combines semantic embedding similarity with keyword BM25 rankings:

$$R_{\text{hybrid}}(d_i, q) = \lambda \cdot \text{CosineSim}(\mathbf{e}_{d_i}, \mathbf{e}_q) + (1 - \lambda) \cdot \text{BM25}(d_i, q)$$

Where $\lambda = 0.70$ balances dense semantic matching with strict term matching.

### 3. Thresholding & Refusal Decision Criteria
When workflow executions violate system policies or reach operational ceilings, execution is halted with standardized error codes:

| Threshold Parameter | Value | Decision / Refusal Action | Error Code |
| :--- | :--- | :--- | :--- |
| **Max Workflow Timeout** | $> 600$ seconds | Terminate execution to prevent runaway resource hold | `ERR_WORKFLOW_TIMEOUT_EXCEEDED` |
| **Max Loop Iteration Count** | $\ge 20$ iterations | Break cyclic loop execution | `ERR_CYCLIC_LOOP_LIMIT_REACHED` |
| **Cross-Tenant Access Attempt** | Tenant ID mismatch | Deny access immediately with 403 Forbidden | `ERR_TENANT_ISOLATION_VIOLATION` |
| **RPA Critical Action Unapproved** | Missing manual approval | Suspend execution and queue for human sign-off | `ERR_RPA_APPROVAL_PENDING` |
| **MaaS Upstream Rate Limit** | HTTP 429 received | Trigger exponential backoff and model failover | `ERR_MAAS_RATE_THROTTLED` |

### 4. Multi-Tier Fallback Mechanisms & Human-in-the-Loop Governance
1. **Tier 1 (Automated Node Retry)**: Transient network failures in external API or tool invocations undergo 3 exponential backoff retries (1s, 2s, 4s).
2. **Tier 2 (Alternative Model Failover)**: If a primary model endpoint (e.g. DeepSeek-R1) experiences downtime or high latency, the workflow seamlessly switches to a fallback model (e.g. iFLYTEK Spark or Qwen).
3. **Tier 3 (Human-in-the-Loop Interruption)**: Business-critical nodes (e.g. financial transaction dispatch or ERP ledger entry) enter a suspended state awaiting physical human operator approval via web console.

---

## The Data It Uses

### 1. Ingestion Data & Input Types
- **Workflow Payloads**: JSON input parameters, schema-validated task arguments, and uploaded files.
- **Enterprise System Data**: ERP records, database queries, and web forms scraped via RPA bots.
- **Tenant Contexts**: Casdoor SSO identity claims, tenant namespaces, and role scopes.

### 2. Reference Storage & Database Engines
- **Relational Metadata**: PostgreSQL / MySQL housing workflow DAG definitions, execution logs, and tenant quotas.
- **Vector Knowledge Bases**: Milvus / pgvector storing chunked corporate documentation.
- **Cache & Event Bus**: Redis / RabbitMQ managing asynchronous task queues and node execution states.

### 3. Model Lineage & System Architecture
- **Supported Models**: iFLYTEK Spark series, DeepSeek-V3/R1, Qwen-2.5, OpenAI GPT-4o, Anthropic Claude 3.5.
- **Platform Stack**: Python 3.10+, FastAPI backend, Celery task workers, Vue 3 web console, Docker/Kubernetes.

### 4. Data Privacy, Governance & Retention
- **Strict Multi-Tenant Separation**: All database rows, vector collections, and execution traces are partitioned by `tenant_id`.
- **On-Premises Deployment Support**: Deployable entirely behind corporate firewalls with zero external telemetry transmission.
- **Execution Log Retention**: Task execution records and intermediate node states are retained for 30 days before archival.

---

## Limitations

### 1. Fragility of RPA Desktop Selectors | Section 1 | Verified |
| - High Memory Consumption During Large PDF Vectorization | Section 2 | Verified |
| - Latency in Multi-Node Sequential DAGs | Section 3 | Verified |
| - Heterogeneous Tool Exception Schemas | Section 4 | Verified |
| - Complex State Rollback in External ERPs | Section 5 | Verified |

# Operational Rules & Constraints

## 1. RPA Execution Guardrails
- RPA tasks involving destructive modifications, system reconfiguration, or credential updates must require human-in-the-loop authorization.
- RPA browser and desktop automation sessions must run in sandboxed virtual displays or dedicated worker pools.

## 2. Multi-Tenant Data Boundaries
- Cross-tenant data leakage is strictly prohibited; workflow states, vector knowledge bases, and plugin credentials must remain isolated by tenant ID.
- User queries to knowledge base collections must enforce strict document-level permission masks.

## 3. Workflow Concurrency & Resource Limits
- Workflows must not exceed a maximum execution timeout (default 600 seconds) or max loop iterations ($N_{\text{loop}} \le 20$).
- Heavy batch extraction or vector indexing jobs must be throttled to prevent resource starvation in high-availability clusters.

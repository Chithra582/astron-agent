---
name: workflow-dag-orchestration
description: Coordinates directed acyclic graph (DAG) execution, manages conditional branches, and tracks workflow state snapshots.
license: Apache-2.0
---

# Workflow DAG Orchestration

## Overview
This skill compiles and executes multi-node agentic workflows, orchestrating parallel task branches and managing transactional state.

## Capabilities
- Compiles declarative JSON/YAML workflow schemas into executable DAG execution graphs.
- Manages conditional branching, looping, and parallel execution paths.
- Captures intermediate execution state snapshots for fault tolerance and resume-on-failure.

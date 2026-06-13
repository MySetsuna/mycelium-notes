---
status: accepted
date: 2026-06-13
---

# 1. Adopt rmcp 1.7 for the MCP server

## Context and Problem Statement

Need a Rust MCP server with stdio + HTTP.

## Considered Options

- rmcp official SDK
- hand-rolled JSON-RPC

## Decision Outcome

Chose rmcp 1.7 (official, macro-based, dual transport).

### Consequences

- stdio for agent harness, HTTP for dashboard, shared axum app.


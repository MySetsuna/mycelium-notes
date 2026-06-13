---
status: accepted
date: 2026-06-14
---

# 2. Ship a self-contained HTML dashboard before the full Vite/Tauri portal

## Context and Problem Statement

The roadmap calls for a Vite+React+Tauri portal (Phase 3), but that needs npm install and a build step. We wanted a visible, runnable website immediately.

## Considered Options

- Build the full Vite+Tauri portal now
- Generate a single self-contained HTML file with embedded data + CDN libs

## Decision Outcome

Chose the self-contained HTML generator (mycelium dashboard): offline, no build, double-click to open. The full Vite/Tauri portal remains Phase 3.

### Consequences

- Immediate visible value; proves the data->viz pipeline.
- Lite dashboard uses Cytoscape (UMD) instead of React Flow since there is no bundler; the Phase-3 portal will use React Flow as planned.


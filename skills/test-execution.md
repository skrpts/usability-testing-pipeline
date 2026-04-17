---
type: skill
id: test-execution
title: "Test Execution"
description: "Human gate — pauses for user to run usability tests and paste results"
tags: [Production, Gate, UX, Testing]
connections:
  - target: llm-service
    type: runs_on
metadata:
  gate: true
---

## Capability

Human gate — pauses for user to run usability tests and paste results

This is a **gate step** — execution pauses until the user responds. The user's response becomes this step's output.

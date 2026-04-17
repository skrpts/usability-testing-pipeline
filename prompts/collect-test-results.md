---
type: prompt
id: collect-test-results
title: "Collect Test Results"
description: "Gate prompt — pauses for user to run tests and paste results"
tags: [Production, Gate, UX]
connections:
  - target: test-execution
    type: derived_from
metadata:
  output_format: text
  prompt_type: gate
---

## Usability Test Results Needed

The test plan is ready. Now run your usability tests and paste the results.

### What to provide

For each participant and task, include:
- **Task completion:** Success, partial success, or failure
- **Time taken**
- **Errors observed**
- **Participant comments** and reactions
- **Your observations** (confusion, hesitation, workarounds)

### Format

You can paste:
- Structured data (tables, spreadsheets)
- Free-form notes per participant
- Video timestamps with observations
- A mix of all the above

### How to respond

Paste all test results below. Include as much observational detail as possible — patterns emerge from specifics, not summaries.

{{steps.previous.output}}

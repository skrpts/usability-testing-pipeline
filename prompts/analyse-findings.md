---
type: prompt
id: analyse-findings
title: "Analyse Test Findings"
description: "Analyses usability test results to identify patterns and severity"
tags: [Production, UX, Analysis]
connections:
  - target: findings-analysis
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a UX researcher analysing usability test results. Identify patterns, quantify issues, and assess severity.

## Your Task

### 1. Task Performance Summary
For each tested task:
- Completion rate (% success, partial, failure)
- Average time on task
- Common error patterns
- Participant sentiment

### 2. Issue Identification
For each usability issue found:
- **Description:** What the issue is
- **Severity:** Critical (blocks task), Major (significant difficulty), Minor (inconvenience), Cosmetic
- **Frequency:** How many participants encountered it
- **Evidence:** Specific observations and quotes
- **Affected tasks:** Which tasks this issue impacts

### 3. Pattern Analysis
- Issues that appear across multiple tasks
- Differences between user segments (if applicable)
- Comparison with known issues (validated or not?)

### 4. Quantitative Summary
- Overall task success rate
- Average SUS score (if available)
- Issues by severity count
- Top 5 issues by impact (severity × frequency)

{{steps.previous.output}}

---
type: prompt
id: generate-recommendations
title: "Generate Recommendations"
description: "Produces prioritised UX recommendations from test findings"
tags: [Production, UX, Generation]
connections:
  - target: recommendations-generation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

You are a UX strategist producing actionable recommendations from usability test findings.

## Your Task

### 1. Prioritised Recommendations
For each recommendation:
- **Issue addressed:** Link to specific finding(s)
- **Recommendation:** Specific, actionable change
- **Priority:** High (fix now), Medium (next sprint), Low (backlog)
- **Effort:** Small (< 1 day), Medium (1-3 days), Large (> 3 days)
- **Impact:** Expected improvement in task success/time/satisfaction
- **Evidence:** Why this recommendation addresses the issue

### 2. Quick Wins
Issues that are high-impact but low-effort to fix. These should be actioned immediately.

### 3. Strategic Improvements
Larger changes that require design iteration:
- Proposed approach
- What to prototype
- What to re-test

### 4. What NOT to Change
Things that tested well — protect these in future iterations.

### 5. Re-Test Plan
- Which recommendations should be validated with follow-up testing
- Suggested test format for validation
- Success criteria for the re-test

{{steps.previous.output}}

---
type: workflow
id: usability-testing-pipeline
title: Usability Testing Pipeline
description: "Plan usability tests, collect results via gate step, analyse findings, and produce prioritised recommendations"
tags: [Production, Customer-Facing, UX, Testing, Gate]
connections:
  - target: test-planning
    type: uses
  - target: test-execution
    type: uses
  - target: findings-analysis
    type: uses
  - target: recommendations-generation
    type: uses
  - target: language-polish
    type: uses
  - target: consistency-check
    type: uses
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "test-planning"
  - "test-execution"
  - "findings-analysis"
  - "recommendations-generation"
  - "language-polish"
  - "consistency-check"
execution:
  - skill: "test-planning"
    prompt: "plan-tests"
    step_type: "generation"
  - skill: "test-execution"
    prompt: "collect-test-results"
    step_type: "validation"
  - skill: "findings-analysis"
    prompt: "analyse-findings"
    step_type: "synthesis"
  - skill: "recommendations-generation"
    prompt: "generate-recommendations"
    step_type: "generation"
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
    context:
      voice_profile: ""
      grammar_strictness: ""
  - parallel:
    - skill: "consistency-check"
      prompt: "check-consistency"
      step_type: "review"
      context:
        voice_profile: ""
        consistency_strictness: ""
---

## Overview

This workflow guides you through a complete usability testing cycle: plan tests, run them, analyse findings, and produce prioritised recommendations. A **gate step** pauses the workflow for you to conduct actual tests and paste results, grounding the analysis in real user data.

## Pipeline Stages

### Stage 1: Test Planning

**Input:** Product description, test objectives, user segments, known issues

Invoke the **test-planning** skill to produce test tasks, scenarios, success criteria, and an observation guide.

**Output:** Complete test plan with 5-8 task scenarios.

### Stage 2: Test Execution (Gate Step)

Execution **pauses** via the **test-execution** gate step. Run your usability tests using the generated plan, then paste your results — task completion data, observations, participant comments.

**Output:** Your test results, ready for analysis.

### Stage 3: Findings Analysis

**Input:** Test results from Stage 2

Invoke the **findings-analysis** skill to identify issues, quantify severity, and detect patterns.

**Output:** Structured findings with severity ratings and evidence.

### Stage 4: Recommendations

**Input:** Analysis from Stage 3

Invoke the **recommendations-generation** skill to produce prioritised, actionable recommendations.

**Output:** Prioritised recommendations with quick wins, strategic improvements, and re-test plan.

### Stage 5: Language Polish

Invoke **language-polish** for final cleanup.

### Stage 6: Consistency Check (Parallel)

Invoke **consistency-check** to verify findings and recommendations are consistent.

## Error Handling

- If test results are sparse, analysis flags lower confidence
- If only 1-2 participants were tested, findings are marked as preliminary

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.product_description}}` | Yes | What your product does | `Project management tool for small teams` |
| `{{input.test_objectives}}` | Yes | What you want to learn | `Can users create a project and invite members?` |
| `{{input.user_segments}}` | No | Who is testing | `New users with no prior exposure` |
| `{{input.existing_issues}}` | No | Known issues to validate | `Users confused by permissions model` |

## Outputs

| Name | Description |
|------|-------------|
| Test plan | Tasks, scenarios, success criteria, observation guide |
| Findings analysis | Prioritised issues with severity and evidence |
| Recommendations | Actionable improvements with effort estimates |

## Setup

1. Run the test plan stage first.
2. Conduct usability tests (in person, remote, or unmoderated).
3. Paste results at the gate step.

## Provider Notes

- Test planning and recommendations benefit from stronger models.
- Analysis works well on most capable models.

## Example Input

```
Product Description: "A project management tool for small teams (5-20 people). Features include: task boards (Kanban style), timeline view, team chat, file sharing, and basic reporting. Web app with responsive mobile support."
Test Objectives: "Can new users create a project, add tasks, assign team members, and set due dates without help? Secondary: can they find and use the timeline view?"
User Segments: "New users who have never seen the product — recruited from general population, must have used at least one project management tool before"
Known Issues: "Users report confusion with the permissions model when inviting team members. The timeline view is reportedly hard to find."
```

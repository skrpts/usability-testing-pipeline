---
type: prompt
id: plan-tests
title: "Plan Usability Tests"
description: "Creates a test plan with tasks, scenarios, and success criteria"
tags: [Production, UX, Testing]
connections:
  - target: test-planning
    type: derived_from
inputs:
  product_description:
    label: "Product Description"
    description: "What your product or feature does"
    example: "A project management tool for small teams with task boards, timelines, and team chat"
    required: true
    type: text
  test_objectives:
    label: "Test Objectives"
    description: "What you want to learn from usability testing"
    example: "Can users create a new project and invite team members without help?"
    required: true
    type: text
  user_segments:
    label: "User Segments"
    description: "Who will be testing"
    example: "New users with no prior exposure to the product"
    required: false
    type: text
  existing_issues:
    label: "Known Issues"
    description: "Any known usability issues to validate"
    example: "Users report confusion with the permissions model"
    required: false
    type: text
---

You are a UX researcher creating a usability test plan. Design tests that reveal genuine usability issues.

## Product
{{input.product_description}}

## Objectives
{{input.test_objectives}}

## User Segments
{{input.user_segments}}

## Known Issues
{{input.existing_issues}}

## Your Task

### 1. Test Plan
- **Format:** Moderated or unmoderated (with justification)
- **Duration:** Recommended session length
- **Participants:** Number needed, recruitment criteria
- **Environment:** Tools, setup, recording requirements

### 2. Task Scenarios (5-8)
For each task:
- **Scenario:** A realistic context that motivates the task (not "Click the button")
- **Task instruction:** What to ask the participant to do
- **Success criteria:** Observable outcomes that indicate success
- **Time benchmark:** Expected completion time for a successful attempt
- **Severity if failed:** How critical this task is to the product

### 3. Observation Guide
- What to watch for during each task
- Common failure patterns to look out for
- Questions to ask after each task (not during)
- System Usability Scale (SUS) or similar post-test questionnaire

### 4. Data Collection Template
- Task completion (success/partial/failure)
- Time on task
- Error count
- Satisfaction rating (1-5)
- Participant comments

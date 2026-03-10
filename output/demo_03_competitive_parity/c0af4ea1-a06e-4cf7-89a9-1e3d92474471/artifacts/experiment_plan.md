# Experiment Plan: CollabDocs Real-time Editor

**Run ID:** c0af4ea1-a06e-4cf7-89a9-1e3d92474471
**Date:** 2026-03-09

---

## Hypothesis

If we enhance the real-time collaboration features, then Daily Active Users Engaged in Collaboration will increase by 25% because improved user experience will encourage more users to participate in collaboration sessions.

## Success Metrics & Guardrails

### Primary Success Metrics

| Metric                                       | Baseline | Target  | Measurement Method                                               | Window        |
|----------------------------------------------|----------|---------|------------------------------------------------------------------|---------------|
| Daily Active Users Engaged in Collaboration   | 120000   | 150000  | Daily tracking of active users participating in collaboration sessions. | 30 days       |
| Daily Collaboration Sessions                   | 14200    | 20000   | Daily tracking of collaboration sessions initiated.              | 30 days       |

### Guardrail Metrics

| Metric                          | Current Value | Max Acceptable Degradation | Measurement Method                                               |
|---------------------------------|----------------|-----------------------------|------------------------------------------------------------------|
| Concurrent Edit Attempts Blocked | 2300           | 1500                        | Daily tracking of blocked concurrent edit attempts.              |

## Experiment Design

We will conduct a phased rollout of the enhanced real-time collaboration features. The rollout will occur in four phases: 10% of users for 7 days, 25% of users for 7 days, 50% of users for 7 days, and 100% of users. At each phase, we will evaluate the success and guardrail metrics. If the guardrail metric for Concurrent Edit Attempts Blocked exceeds 1500 during any phase, we will halt the rollout and reassess the changes.

## Sample Size & Duration

To achieve a minimum detectable effect (MDE) of 25% increase in Daily Active Users with 80% power and a significance level of 0.05, we require a sample size of at least 1000 users per arm. Given our traffic, we estimate the experiment will last 30 days to gather sufficient data across all phases.

## Segmentation

We will analyze the following cohorts post-hoc: users who frequently collaborate (defined as users who have participated in more than 5 collaboration sessions in the last month) versus infrequent collaborators. This segmentation is crucial to understand if the enhancements are more beneficial to active users versus new or less engaged users.

## Rollback Criteria

If the Concurrent Edit Attempts Blocked metric exceeds 1500 during any phase, we will immediately halt the rollout and revert to the previous version of the features.

## Data Collection Plan

We will track the following events: `collaboration_session_initiated`, `user_engaged_in_collaboration`, and `edit_attempt_blocked`. We will also log user attributes to identify assistive technology usage, such as `screen_reader_active` and `keyboard_navigation_enabled`.

## Analysis Plan

We will use a chi-square test for proportions to analyze the increase in Daily Active Users and Daily Collaboration Sessions. Interim looks will be scheduled at the end of each phase, applying a Holm-Bonferroni correction for multiple comparisons. The significance level will be set at 0.05, and results will be reviewed and signed off by the product management team.
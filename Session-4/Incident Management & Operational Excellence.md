# Session 4: Incident Management & Operational Excellence

**Duration:** 45 Minutes  
**Audience:** SREs, Operations Engineers, DevOps Engineers, Support Engineers  
**Goal:** Understand how mature enterprises handle incidents and production outages.

---

# Agenda

| Topic | Time |
|--------|------|
| Introduction | 5 min |
| Incident Lifecycle | 10 min |
| Handling Production Outages | 10 min |
| Escalation Management | 7 min |
| Communication During Incidents | 5 min |
| Post-Incident Review & Learning Culture | 5 min |
| Recap | 3 min |

---

# 1. Introduction (5 Minutes)

## Ask Participants

**Question:**

> Has anyone ever been on a production bridge call at 2 AM?

Most enterprise engineers eventually experience this.

An incident is not simply a technical problem.

An incident is:

> Any event that impacts customers, business operations, SLAs, or service availability.

---

## Real Enterprise Examples

### Example 1: E-Commerce

Customers cannot place orders during a festive sale.

**Business impact:**
- Revenue loss
- Customer dissatisfaction

Severity: **P1**

---

### Example 2: Internal Reporting Portal Down

Only internal users cannot access reports.

Severity: **P3**

---

## Important Mindset

In mature organizations:

> The first priority is service restoration.

Not root cause analysis.

---

# 2. Incident Lifecycle (10 Minutes)

Most enterprises follow a lifecycle similar to this:

```text
Detect
  ↓
Assess
  ↓
Declare Incident
  ↓
Respond
  ↓
Mitigate
  ↓
Recover
  ↓
Review & Improve
```

---

# Phase 1: Detection

Incidents are usually detected by:

- Monitoring tools
- Customer complaints
- Service desk
- Synthetic monitoring
- Business teams

## Real Example

Dynatrace alert:

```text
Checkout API error rate > 30%
```

Another example:

Support team reports:

> Multiple customers cannot login.

Incident detected.

---

# Phase 2: Assessment

Questions to ask immediately:

1. Which application is affected?
2. Is production impacted?
3. How many users are impacted?
4. Is there a workaround?
5. What is the severity?

---

## Enterprise Example

### Scenario

Monitoring shows:

```text
CPU = 98%
```

Questions:

- Is customer traffic impacted?
- Is response time increasing?
- Is this normal peak load?

Sometimes alerts are not incidents.

---

# Phase 3: Incident Declaration

When customer or business impact exists:

Declare incident.

Examples:

```text
INC-123456 created.
Severity = P1
Bridge call started.
```

---

# Phase 4: Response

Activities:

- Assemble responders.
- Assign Incident Commander.
- Start troubleshooting.

Typical bridge participants:

- SRE Team
- Application Team
- DBA Team
- Network Team
- Cloud Team

---

# Enterprise Role Structure

## Incident Commander

Responsible for:

- Driving the call
- Tracking actions
- Coordinating teams

Does NOT troubleshoot.

---

## Technical Lead

Responsible for:

- Leading investigation
- Suggesting mitigation

---

## Communications Lead

Responsible for:

- Sending updates to stakeholders

---

# Real Example

Incident Commander:

> App Team, please investigate application logs.

> DBA Team, verify database health.

> Next update in 15 minutes.

---

# Phase 5: Mitigation

Goal:

> Restore service as quickly as possible.

Examples:

- Rollback deployment
- Restart failed pods
- Increase capacity
- Failover to DR site

---

# Real Enterprise Scenario

## Situation

New deployment completed at 11:00 PM.

At 11:05 PM:

```text
HTTP 500 errors increased.
```

Bad approach:

```text
Let's analyze code for two hours.
```

Good approach:

```text
Rollback deployment immediately.
```

Service restored in 10 minutes.

Root cause analysis can happen later.

---

# 3. Handling Production Outages (10 Minutes)

## Golden Rules

# Rule 1: Stay Calm

Panic creates mistakes.

---

# Rule 2: Build Timeline

Always ask:

```text
What changed?
```

Examples:

- Deployment
- Infrastructure patching
- Firewall changes
- Certificate renewal

---

## Example Timeline

```text
10:00 Deployment completed
10:03 Errors started
10:05 Alert triggered
```

Deployment immediately becomes suspect.

---

# Rule 3: Use Runbooks

Mature organizations maintain runbooks.

Example:

```text
Kubernetes API Failure Runbook

1. Verify cluster health.
2. Check API server pods.
3. Check etcd health.
4. Review recent changes.
5. Escalate platform team if unresolved.
```

Runbooks reduce MTTR.

---

# Rule 4: Work Hypothesis Driven

Bad troubleshooting:

```text
Restart random services.
```

Good troubleshooting:

Hypothesis:

> Database connections exhausted.

Validation:

```sql
select count(*) from v$session;
```

Evidence-based troubleshooting.

---

# Rule 5: Keep Notes

During bridge calls maintain timeline.

Example:

```text
09:10 Incident declared
09:15 DBA engaged
09:25 Root cause identified
09:35 Rollback completed
09:40 Service restored
```

These notes help during postmortems.

---

# 4. Escalation Management (7 Minutes)

Escalation means engaging the right people at the right time.

---

# Functional Escalation

Need technical expertise.

Example:

SRE discovers:

```text
Storage array failure.
```

Escalate:

Storage Team.

---

# Hierarchical Escalation

Inform management.

Typical triggers:

- P1 incident
- SLA breach risk
- Long outage
- Customer escalation

---

# Typical Enterprise Escalation Path

```text
L1 Support
   ↓
L2 Operations
   ↓
SME
   ↓
Manager
   ↓
Director
```

---

# Practical Rule

If no progress within 15–20 minutes:

Escalate.

Never struggle alone for one hour.

---

## Real Example

You are primary on-call.

Oracle database issue detected.

You are not DBA expert.

Correct action:

```text
Engage DBA immediately.
```

---

# 5. Communication During Incidents (5 Minutes)

Poor communication makes incidents worse.

---

# Stakeholders

- Engineering Teams
- Leadership
- Customer Support
- Customers
- Executives

---

# Communication Principles

Be:

- Clear
- Concise
- Honest
- Timely

Never guess.

---

# Bad Update

```text
Something weird is happening in JVM.
```

---

# Good Update

```text
Customers are experiencing login failures.

Engineering teams are actively investigating.

Current impact: Approximately 70% of users.

Next update: 15 minutes.
```

---

# Enterprise Communication Template

```text
Incident ID: INC123456

Severity: P1

Impact:
Customers unable to login.

Current Status:
Investigation in progress.

Actions Taken:
Application and DBA teams engaged.

Next Update:
15 minutes.
```

---

# Update Frequency

| Severity | Frequency |
|-----------|-----------|
| P1 | Every 15 min |
| P2 | Every 30 min |
| P3 | Hourly |

---

# 6. Post-Incident Review & Learning Culture (5 Minutes)

Once service is restored:

Work is not finished.

---

# Goal

Learn.

Improve.

Prevent recurrence.

---

# Blameless Culture

Wrong:

> Who broke production?

Correct:

> Why did our systems allow this failure?

---

# Real Example

Bad statement:

```text
John deployed bad code.
```

Better statement:

```text
Deployment pipeline lacked validation checks.
```

---

# Standard PIR Questions

## What happened?

## Why did it happen?

## What worked well?

## What did not work?

## How do we prevent recurrence?

---

# Sample Action Items

| Action | Owner |
|---------|-------|
| Add memory alert | SRE Team |
| Improve runbook | Operations Team |
| Add deployment validation | DevOps Team |
| Automate rollback | Platform Team |

---

# Characteristics of Mature Organizations

| Immature | Mature |
|-----------|---------|
| Blame people | Improve systems |
| No runbooks | Document everything |
| Reactive | Proactive |
| Manual recovery | Automation |
| Poor communication | Frequent updates |

---

# Key Takeaways

1. Restore service first.
2. Communicate frequently.
3. Escalate early.
4. Use runbooks.
5. Keep timelines.
6. Conduct blameless reviews.
7. Continuously improve.

---

# Discussion Questions

1. What should be the first action during a P1 outage?
2. When should you escalate?
3. Why are runbooks important?
4. Why should postmortems be blameless?

---

> Mature organizations are not defined by the absence of incidents. They are defined by how effectively they respond, recover, learn, and improve.

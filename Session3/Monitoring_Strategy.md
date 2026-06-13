# Monitoring Strategy for Modern Systems

**Duration:** 45 Minutes

## Agenda

| Time        | Topic                                         |
| ----------- | --------------------------------------------- |
| 0 - 3 min   | Introduction: What is Monitoring?             |
| 3 - 10 min  | Building an Effective Monitoring Strategy     |
| 10 - 20 min | Metrics, Logs, and Traces                     |
| 20 - 30 min | What Should Be Monitored and Why?             |
| 30 - 38 min | Alerting Best Practices                       |
| 38 - 42 min | Common Monitoring Mistakes                    |
| 42 - 45 min | Practical Monitoring Approach & Key Takeaways |
| Bonus       | Important Monitoring & SRE Metrics            |

---

# What is Monitoring? (3 mins)

Monitoring means keeping an eye on your systems, applications, and services to ensure everything is working properly.

## Simple Example

Think of your car:

* Speedometer → Shows speed
* Fuel Gauge → Shows fuel level
* Engine Warning Light → Alerts when something is wrong

Similarly, monitoring helps answer:

* Is the application running?
* Is it slow?
* Are users facing errors?
* Is the server healthy?

---

# 1. Building an Effective Monitoring Strategy (7 mins)

## What is a Monitoring Strategy?

A monitoring strategy is a plan that answers:

* What should we monitor?
* How should we monitor it?
* When should we alert someone?

## Example: Online Shopping Website

| Component       | Why Monitor It?              |
| --------------- | ---------------------------- |
| Website         | Is it accessible?            |
| Login Service   | Can users log in?            |
| Payment Service | Are payments successful?     |
| Database        | Is data stored correctly?    |
| Server          | Is CPU or Memory overloaded? |

## Good Monitoring Strategy

Focus on:

* Customer impact
* Business impact
* Outage prevention

---

# 2. Metrics, Logs, and Traces (10 mins)

These are the three pillars of observability.

## Metrics

Numbers collected over time.

### Examples

* CPU Usage = 80%
* Memory Usage = 70%
* Response Time = 2 sec
* Error Rate = 5%

### Real-Life Example

Fitness Watch:

* Steps
* Heart Rate
* Calories

### Why Metrics?

* Health overview
* Trend analysis
* Alerting

---

## Logs

Detailed records of events.

### Example

```text
10:30 User Login Successful
10:35 Invalid Password
10:40 Database Connection Failed
```

### Real-Life Example

Logs are the diary of an application.

### Why Logs?

* Troubleshooting
* Root Cause Analysis
* Security Investigation

---

## Traces

Show the complete journey of a request.

### Example

```text
Website
  ↓
Order Service
  ↓
Payment Service
  ↓
Database
```

### Real-Life Example

Tracking a courier package from pickup to delivery.

### Why Traces?

* Find bottlenecks
* Troubleshoot microservices
* Understand dependencies

---

# 3. What Should Be Monitored and Why? (10 mins)

## Infrastructure Monitoring

Monitor:

* CPU
* Memory
* Disk
* Network

### Example

CPU reaches 100%.

Result:
Application becomes slow.

---

## Application Monitoring

Monitor:

* Response Time
* Error Rate
* Request Count

### Example

Normal response time:

```text
1 second
```

Suddenly:

```text
10 seconds
```

Users will notice immediately.

---

## Database Monitoring

Monitor:

* Slow Queries
* Connection Count
* Storage Usage

### Example

Slow database = Slow application.

---

## Business Monitoring

Monitor:

* Orders per minute
* Payment Success Rate
* User Registrations
* Revenue Transactions

### Example

Website is healthy.

But:

```text
Payments are failing
```

Business loses revenue.

---

# 4. Alerting Best Practices (8 mins)

## What is an Alert?

A notification sent when action is required.

### Example

```text
CPU > 90%
```

---

## Good Alerts are Actionable

Bad Alert:

```text
Something looks strange
```

Good Alert:

```text
Payment Service Error Rate > 10%
```

---

## Alert on Customer Impact

Bad:

```text
One server restarted
```

Good:

```text
Users cannot place orders
```

---

## Prioritize Alerts

### Critical (P1)

```text
Website Down
```

Immediate action required.

### Warning (P2/P3)

```text
Disk Usage 80%
```

Needs attention but not urgent.

---

## Avoid Alert Fatigue

Too many alerts lead to engineers ignoring alerts.

---

# 5. Common Monitoring Mistakes (4 mins)

## Too Many Alerts

Example:

```text
500 alerts/day
```

People stop paying attention.

---

## Monitoring Only Infrastructure

Monitor:

✅ CPU

✅ Memory

But forget:

❌ User Experience

❌ Business Transactions

---

## No Ownership

Alert arrives.

Nobody knows who should respond.

---

## Collecting Data but Never Reviewing It

Metrics, logs, and traces are useless if nobody uses them.

---

## No Dashboard

Teams cannot quickly understand system health.

---

# Practical Monitoring Approach (3 mins)

Follow these 5 steps:

### Step 1

Monitor Infrastructure

```text
CPU
Memory
Disk
Network
```

### Step 2

Monitor Applications

```text
Response Time
Error Rate
Request Volume
```

### Step 3

Monitor Business Metrics

```text
Orders
Payments
Logins
```

### Step 4

Create Meaningful Alerts

```text
Service Down
High Error Rate
Slow Response Time
```

### Step 5

Review and Improve

Ask:

```text
Which alerts are useful?
Which alerts create noise?
What else should we monitor?
```

---

# Key Takeaways

✅ Monitoring helps detect issues before users complain

✅ Metrics = What happened

✅ Logs = Why it happened

✅ Traces = Where it happened

✅ Monitor Infrastructure, Applications, and Business Metrics

✅ Create Actionable Alerts

✅ Avoid Alert Fatigue

✅ Focus on Customer and Business Impact

## Easy Formula to Remember

```text
Metrics = What happened

Logs = Why it happened

Traces = Where it happened

Alerts = Tell me when I need to act
```

---

# Bonus: Important Monitoring & SRE Metrics

| Metric                   | Simple Definition                               |
| ------------------------ | ----------------------------------------------- |
| Availability             | Percentage of time a service is available       |
| SLI                      | Actual service performance experienced by users |
| Error Budget             | Allowed failure before SLO is breached          |
| Latency                  | Time taken to process a request                 |
| Traffic (RPS)            | Number of requests per second                   |
| Error Rate               | Percentage of failed requests                   |
| CPU Utilization          | Percentage of CPU being used                    |
| Memory Utilization       | Percentage of Memory being used                 |
| MTTD                     | Average time to detect incidents                |
| MTTR                     | Average time to resolve incidents               |
| MTBF                     | Average uptime between failures                 |
| Deployment Frequency     | How often code is deployed                      |
| Lead Time for Changes    | Time from code commit to deployment             |
| Change Failure Rate      | Percentage of deployments causing issues        |
| Time to Restore (TTR)    | Time to restore service after an outage         |
| Incident Recurrence Rate | Percentage of repeated incidents                |
| Toil Ratio               | Percentage of repetitive manual work            |
| On-call Page Volume      | Number of alerts during on-call                 |
| Saturation               | Resource utilization level                      |

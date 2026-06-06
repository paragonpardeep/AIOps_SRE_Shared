# Session 2: Reliability Mindset & Service Ownership

## Objective

Develop the core mindset that successful SRE teams use to manage service reliability and understand how reliability impacts customers and business outcomes.

**Duration:** 45 Minutes

---

# Agenda

| Topic                                     | Duration |
| ----------------------------------------- | -------- |
| What is Reliability?                      | 8 min    |
| Reliability from Business Perspective     | 7 min    |
| Service Ownership Culture                 | 8 min    |
| Measuring Service Health                  | 7 min    |
| SLI, SLO, SLA Concepts                    | 10 min   |
| Real-world Examples & Interview Questions | 5 min    |

---

# 1. What is Reliability?

## Discussion Question

What is more important?

* Website with 100 features but crashes daily
* Website with 20 features but never crashes

Most businesses prefer the second option because customers value consistency and trust.

## Definition

Reliability is the ability of a system to consistently perform its intended function without failure.

### Simple Meaning

Users should be able to use the service whenever they need it.

### Examples

✅ Google Search responds consistently

✅ UPI payments succeed most of the time

❌ Banking application unavailable during salary day

❌ E-commerce site crashes during a major sale

---

## Reliability vs Availability

Many people use these terms interchangeably, but they are different.

### Availability

Is the service accessible?

Example:

* Website opens successfully

### Reliability

Can the service perform its intended function correctly?

Example:

* Website opens, but checkout functionality does not work

### Key Difference

| Availability         | Reliability              |
| -------------------- | ------------------------ |
| Service is reachable | Service works correctly  |
| Focus on uptime      | Focus on user experience |

---

# 2. Reliability from a Business Perspective

Business leaders do not primarily focus on:

* CPU utilization
* Memory utilization
* Kubernetes nodes
* Server health

Business leaders care about:

* Revenue
* Customer satisfaction
* Brand reputation
* Business continuity

---

## Example 1: Amazon Prime Day

Imagine Amazon experiences a 30-minute outage during Prime Day.

### Impact

* Millions of dollars in lost revenue
* Customer frustration
* Negative publicity
* Loss of customer trust

Business sees:

> Revenue loss

Business does not see:

> CPU utilization reached 90%

---

## Example 2: Banking Application

Suppose UPI transactions fail for 15 minutes.

### Impact

* Customer complaints
* Escalations
* Regulatory concerns
* Business reputation damage

An SRE should think:

> How does this outage impact customers and business?

Not:

> CPU usage is high

---

## Interview Question

### Why is reliability important?

**Answer:**

Reliability ensures customers can consistently use services without interruption, reducing revenue loss, improving customer satisfaction, and protecting business reputation.

---

# 3. Service Ownership Culture

## Traditional Model

Development Team

↓

Hands over application to Operations Team

↓

Operations Team handles production issues

### Problems

* Finger-pointing
* Slow issue resolution
* Lack of accountability

---

## Modern SRE Culture

### You Build It, You Run It

Developers and SREs share responsibility for production systems.

---

## What Service Ownership Means

If you own a service, you are responsible for:

* Architecture
* Monitoring
* Performance
* Scalability
* Reliability
* Incident response
* Continuous improvement

Instead of saying:

> This is not my problem.

An owner says:

> Let's investigate and resolve it.

---

## Real Example

### Payment Service Owner Responsibilities

* Monitor service health
* Respond to incidents
* Perform capacity planning
* Improve reliability
* Conduct Root Cause Analysis (RCA)
* Reduce recurring issues

---

## Interview Question

### What is service ownership?

**Answer:**

Service ownership means being accountable for the complete lifecycle of a service, including development, monitoring, maintenance, reliability, incident management, and customer experience.

---

# 4. Measuring Service Health

A common SRE principle:

> If you cannot measure it, you cannot improve it.

Monitoring and metrics are critical to understanding system health.

---

## Four Golden Signals

Introduced by Google SRE.

### 1. Latency

How long it takes to process a request.

Examples:

* Login response time = 200 ms
* Checkout response time = 500 ms

Problem:

* Login takes 10 seconds

---

### 2. Traffic

Amount of demand on the service.

Examples:

* Requests per second (RPS)
* Transactions per minute

---

### 3. Errors

Failed requests or operations.

Examples:

* HTTP 500 errors
* Failed payments
* Database connection failures

---

### 4. Saturation

How close resources are to their limits.

Examples:

* CPU utilization
* Memory utilization
* Disk usage
* Network utilization

---

## Interview Question

### What metrics would you monitor for a payment application?

**Answer:**

* Transaction success rate
* Response time
* Error rate
* Request volume
* CPU and memory utilization
* Database performance metrics

---

# 5. Introduction to SLI, SLO, and SLA

This is one of the most frequently asked SRE interview topics.

---

## SLI (Service Level Indicator)

A measurable metric used to evaluate service performance.

### Example

99.95% of login requests are successful.

### SLI Answers

> How are we currently performing?

### Common SLIs

* Availability
* Latency
* Error rate
* Throughput

---

## SLO (Service Level Objective)

A target value for an SLI.

### Example

99.9% login success rate per month.

### SLO Answers

> What is our target?

---

## SLA (Service Level Agreement)

A formal commitment made to customers.

### Example

99.5% availability guarantee.

If violated:

* Financial penalties
* Service credits
* Contractual consequences

### SLA Answers

> What have we promised our customers?

---

## Easy Way to Remember

| Concept | Meaning             | Example |
| ------- | ------------------- | ------- |
| SLI     | Measurement         | 99.92%  |
| SLO     | Internal Target     | 99.90%  |
| SLA     | Customer Commitment | 99.50%  |

---

## Real Example

### Payment Service

SLI:

* 99.92% successful transactions

SLO:

* 99.90% successful transactions

SLA:

* 99.50% successful transactions

Result:

SLI exceeds SLO, indicating the service is performing well.

---

# Error Budget

One of the most important Google SRE concepts.

If:

SLO = 99.9%

Then:

Allowed failure = 0.1%

This allowable failure is called the **Error Budget**.

---

## Why Error Budget Matters

It helps balance:

* Innovation
* Reliability

### Example

If the error budget is exhausted:

❌ Pause risky feature releases

✅ Focus on reliability improvements

---

## Interview Question

### Explain SLI, SLO, and SLA.

**Answer:**

SLI is the measured reliability metric, SLO is the target value for that metric, and SLA is the contractual commitment made to customers.

---

# 6. Real-World Reliability Examples

## Netflix

### Challenges

* Millions of concurrent users
* Global scale

### Reliability Practices

* Auto-scaling
* Multi-region architecture
* Continuous monitoring
* Chaos Engineering

### Outcome

Highly reliable streaming experience.

---

## Google Search

### Focus Areas

* Availability
* Query latency
* Error rates

Google uses SLOs extensively to manage reliability.

---

## UPI Payments

### Critical Metrics

* Transaction success rate
* Payment latency
* Failure percentage

Even a small increase in failure rate can impact millions of users.

---

# Common Interview Questions

## Q1. What is reliability?

**Answer:**

The ability of a system to consistently perform its intended functions with minimal failures.

---

## Q2. Difference between availability and reliability?

**Answer:**

Availability means the service is accessible, while reliability means the service performs correctly and consistently.

---

## Q3. What are the Four Golden Signals?

**Answer:**

* Latency
* Traffic
* Errors
* Saturation

---

## Q4. What is service ownership?

**Answer:**

Service ownership means taking end-to-end responsibility for the health, reliability, operation, and improvement of a service.

---

## Q5. Explain SLI, SLO, and SLA.

**Answer:**

* SLI = Measurement
* SLO = Target
* SLA = Customer Commitment

---

## Q6. What is an Error Budget?

**Answer:**

The amount of unreliability allowed while still meeting the SLO target.

---

# Key Takeaways

* Reliability is a business requirement, not just a technical metric.
* SRE focuses on customer experience and business impact.
* Service ownership requires end-to-end accountability.
* Service health is measured using the Four Golden Signals.
* SLI, SLO, SLA, and Error Budgets are foundational SRE concepts.
* Successful SRE teams balance innovation with reliability.

---

# Final Thought

> A successful SRE does not simply keep systems running. They ensure customers can reliably achieve their goals while enabling the business to grow.

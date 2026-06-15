# 🏥 MedSched – Security, Performance, and Bug Bounty Report (Milestone 3)

## System Overview

MedSched is a healthcare appointment scheduling application designed to allow patients to schedule, modify, and cancel appointments with healthcare providers. The system also provides administrative functions for managing schedules and patient information.

The objective of this project was to evaluate the security, performance, and reliability of the MedSched application through structured testing activities. Security testing was conducted to identify vulnerabilities that could expose sensitive information or compromise system integrity. Performance testing was performed using Apache JMeter to evaluate how the system responds under concurrent user activity. All identified issues were documented and prioritized using a bug bounty–style severity framework.

---

## Security Testing Summary

### Testing Scope

Security testing focused on:

* User authentication
* Input validation
* Credential protection
* Basic vulnerability assessment

### Tools Used

* Browser Developer Tools
* Manual Security Testing
* Input Validation Testing

### Security Findings

#### Issue #1 – SQL Injection Vulnerability

**Category:** Security
**Severity:** Critical

Testing revealed that the login form did not properly validate user input. Malicious SQL statements could potentially be inserted into authentication fields, allowing unauthorized access to application resources.

**Potential Impact:**

* Unauthorized account access
* Database compromise
* Exposure of sensitive information

**Evidence:**
See GitHub Issue #1 for screenshots and testing evidence.

---

#### Issue #2 – Weak Password Protection

**Category:** Security
**Severity:** Critical

Password handling mechanisms lacked sufficient protections to ensure secure storage and transmission of credentials.

**Potential Impact:**

* Credential theft
* Unauthorized account access
* Loss of user trust

**Evidence:**
See GitHub Issue #2 for screenshots and supporting documentation.

---

## Performance Testing Summary

### Test Configuration

Apache JMeter was used to simulate concurrent user activity.

**Configuration:**

* Number of Threads (Users): 10
* Ramp-Up Period: 10 Seconds
* Duration: 60 Seconds
* Workflow Tested: Appointment Scheduling / Login Process

### Performance Results

| Metric                | Result       |
| --------------------- | ------------ |
| Average Response Time | Insert Value |
| Throughput            | Insert Value |
| Error Rate            | Insert Value |

### Analysis

Performance testing evaluated system responsiveness under moderate user load.

The collected results indicate whether the application can effectively support concurrent users without excessive delays or failures. Any elevated response times or error rates suggest potential bottlenecks within the application infrastructure, database operations, or server configuration.

#### Issue #3 – High Response Time Under Load

**Category:** Performance
**Severity:** High

Testing identified increased response times during the appointment scheduling process when multiple users accessed the system simultaneously.

**Potential Impact:**

* Reduced user satisfaction
* Increased abandonment of tasks
* Lower system reliability

**Evidence:**
See GitHub Issue #3 and attached JMeter Summary Report screenshots.

---

## Bug Bounty–Style Issue Prioritization

| GitHub Issue ID | Summary of Finding                           | Category    | Technical Evidence              | Severity | Justification                                                |
| --------------- | -------------------------------------------- | ----------- | ------------------------------- | -------- | ------------------------------------------------------------ |
| #1              | SQL Injection on Login                       | Security    | Manual Input Validation Testing | Critical | Allows unauthorized access and potential database compromise |
| #2              | Weak Password Protection                     | Security    | Credential Inspection Testing   | Critical | May expose sensitive user credentials                        |
| #3              | High Response Time on Appointment Scheduling | Performance | Apache JMeter Summary Report    | High     | Impacts usability and user satisfaction                      |

---

## Usability and User Impact Analysis

### Security and User Trust

Security vulnerabilities directly affect user confidence in the application. If users believe their personal or medical information is at risk, they may choose not to use the system. The SQL injection vulnerability represents a significant threat because it could allow unauthorized access to protected information.

### Performance and User Experience

Performance issues influence how users perceive system reliability. Long response times during appointment scheduling may cause frustration and reduce confidence in the platform. Users may abandon tasks or submit duplicate requests if the system appears unresponsive.

These issues negatively impact both usability and overall user satisfaction.

---

## Recommendations and Next Steps

### Issue #1 – SQL Injection

**Recommended Fixes:**

* Implement parameterized SQL queries
* Validate and sanitize all user inputs
* Apply server-side input validation

### Issue #2 – Weak Password Protection

**Recommended Fixes:**

* Use bcrypt password hashing
* Enforce HTTPS across all application traffic
* Strengthen password complexity requirements

### Issue #3 – Performance Bottleneck

**Recommended Fixes:**

* Optimize database queries
* Add indexing to frequently accessed tables
* Implement caching mechanisms
* Conduct additional load testing with larger user groups

### Prioritization

1. Fix SQL Injection Vulnerability (Critical)
2. Improve Password Protection (Critical)
3. Address Performance Bottlenecks (High)

---

## Conclusion

Security and performance testing identified several issues that could negatively affect system reliability, security, and user trust. The most significant risks involve authentication security and system responsiveness under load.

Addressing these findings will improve application stability, strengthen security controls, and provide a better overall user experience. All findings have been documented through GitHub Issues and supported with testing evidence to ensure traceability and accountability throughout the remediation process.

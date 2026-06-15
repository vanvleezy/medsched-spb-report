# MedSched Security, Performance, and Bug Bounty Report

## System Overview
MedSched is an appointment scheduling system that supports patient login, appointment booking, rescheduling, and admin management.

---

## Security Testing Summary

Testing types:
- Authentication testing
- Input validation testing
- Manual vulnerability scanning

### Findings

**#1 SQL Injection on Login (Critical)**  
- Evidence: Manual input manipulation in login form  
- Impact: Unauthorized database access and data exposure  

**#3 Cleartext Password Transmission (Critical)**  
- Evidence: Packet inspection shows unencrypted credentials  
- Impact: Exposure of sensitive user credentials  

---

## Performance Testing Summary (JMeter)

Test Configuration:
- 10 users
- Ramp-up: 10 seconds
- Duration: 60 seconds

### Results:
- Avg Response Time: 8.5s (checkout endpoint)
- Throughput: Moderate under load
- Error Rate: 15% on search endpoint

### Analysis:
System shows performance degradation under concurrent load, especially in checkout and search functions.

---

## Bug Bounty Prioritization Table

| Issue ID | Summary | Category | Evidence | Severity | Justification |
|----------|--------|----------|----------|----------|--------------|
| #1 | SQL Injection Login | Security | Manual test | Critical | Full DB compromise risk |
| #2 | Checkout Latency | Performance | JMeter 8.5s | High | User abandonment risk |
| #3 | Cleartext Password | Security | Packet capture | Critical | Credential exposure |
| #4 | Search Errors | Performance | 15% error rate | Medium | Reduced reliability |

---

## Usability and User Impact Analysis

- Slow checkout reduces user trust and increases abandonment.
- Cleartext passwords severely damage user confidence in system security.

---

## Recommendations and Next Steps

- Implement parameterized queries to fix SQL injection
- Enable HTTPS/TLS for all endpoints
- Optimize database queries and add indexing for checkout/search
- Improve caching for frequently accessed data

---

## Submission Notes
- Ensure GitHub repo is public
- Attach screenshots in issues folder or GitHub Issues

---
date created: Monday, December 1st 2025, 1:49:46 pm
date modified: Monday, December 1st 2025, 1:55:42 pm
---

# TM353 TMA 01 - Case Study Analysis

## Overview
- **Incident Date**: Friday 31 January 2025, 9:48am
- **Resolution**: Sunday 2 February 2025
- **Type**: Software failure (NOT cyber attack)
- **Location**: UK Mainframe operating system

---

## Timeline of Events

### Friday 31 January 2025
- **09:48** - Incident begins (software problem in UK Mainframe)
- **11:34** - UK regulators (FCA) notified (1 hour 46 minutes after start)
- **~11:48** - First communications to customers (within 2 hours)
  - Service status web pages updated
  - Notifications to staff
  - Automated telephone messages updated
  - Social media post (@BarclaysUKHelp)
  - Press statement distributed
- **Throughout day** - Progressive degradation of Mainframe performance
- **Evening** - Services continue to fail intermittently

### Saturday 1 February 2025
- **01:30** - Barclays app and online banking back online
- **08:00** - Customers experience new difficulties logging in and payment errors
- **12:00 (midday)** - Issues largely resolved
- **Throughout day** - Contact centres able to service accounts but payment balances not up-to-date

### Sunday 2 February 2025
- **Throughout day** - Mainframe and platforms remain stable
- **Later** - Mitigation actions taken (on advice of Mainframe provider)

### Friday 21 February 2025
- **Software fix received** from Mainframe provider
- Now undergoing comprehensive testing

---

## Root Cause Analysis

### Primary Cause
**Software problem in critical module of UK Mainframe operating system**

### Contributing Factors (from 2-year pattern)
Based on 33 incidents in 2 years (Jan 2023 - Jan 2025):
1. **Technology change** (12 instances)
   - Software updates
   - System upgrades
   - Infrastructure changes

2. **Operational error** (10 instances)
   - Human mistakes
   - Configuration errors
   - Procedural failures

3. **Third-party technology or service failure** (7 instances)
   - External provider issues
   - Integration failures
   - Dependency failures

### Impact Areas
- Infrastructure
- Applications
- Underlying system configurations

---

## Technical System Architecture

### Core System: UK Mainframe
**Underpins**:
- Core banking applications
  - Deposits
  - Overdrafts
  - Debit cards

**Serves**:
- Barclays UK (primary)
- International & UK Corporate Bank
- Private Bank & Wealth Management (PBWM)

### Dependent Services
**Customer-facing channels**:
- Mobile app
- Online banking
- Debit card payments (in-store and online)
- ATM withdrawals
- Branch systems
- Contact centre technology
- Interactive phone response

**External integrations**:
- Address finder service
- Secure payment service
- Regulatory reporting systems

---

## Impact Analysis

### Customer Impact

#### Scale
- **Total customers**: 13+ million digitally active UK customers
- **Login failures**: 5% of attempts to log into mobile app/online banking
- **Payment failures**: 
  - 17% of successful logins attempted payments
  - 56% of payment attempts failed
- **Additional impacts**: Lower volumes in Corporate Bank and PBWM

#### Service Availability During Incident

| Service | Status | Notes |
|---------|--------|-------|
| Mobile app login | Severely impacted | 5% failure rate |
| Online banking login | Severely impacted | Same as app |
| Payment processing | Critically impacted | 56% failure rate for those who could log in |
| Debit cards (in-store/online) | Mostly functional | Short periods of reduced availability |
| ATM withdrawals | Mostly functional | Short periods of reduced availability |
| Branches | Open | Normal or extended hours, but technology impacted |
| Contact centres | Open | Normal or extended hours, long wait times |
| Interactive phone | Impacted | Contributed to long wait times |

### Timing Significance

**Why this was particularly critical**:
1. **End of January payroll** - Many customers receiving first pay of the year
2. **Self-assessment tax deadline** - 31 January deadline for HMRC payments
3. **Friday (start of weekend)** - Extended period before business recovery

### Stakeholder Impacts

**Customers**:
- Unable to access wages
- Unable to pay tax (though HMRC confirmed no late penalties until 1 March)
- Unable to make urgent payments
- Anxiety and frustration
- Long contact centre wait times

**Vulnerable customers**:
- Prioritized in remediation efforts
- Potentially more severely impacted by lack of access

**Barclays employees**:
- IT staff: Crisis management, long hours
- Branch staff: Extended hours, manual workarounds
- Contact centre staff: High call volumes, stressed customers

**HMRC**:
- Direct contact with Barclays needed
- Had to extend penalty deadline

**Regulators (FCA)**:
- Required notification and ongoing updates
- Incident reporting under Payment Services Regulation (PSR) 2017

**Media**:
- High-profile story
- Reputational impact for Barclays

**Parliamentary committee**:
- Required detailed explanation from CEO

---

## Barclays Response

### Immediate Actions (During Incident)

**Crisis Management**:
- Crisis Management procedures enacted immediately upon identification
- Prioritization of vulnerable customers
- Focus on restoring services swiftly

**Communication Strategy**:
- Multi-channel approach within first 2 hours
- Service status web pages
- Staff notifications
- Automated phone messages
- Social media updates (@BarclaysUKHelp)
- Press statements
- Direct contact with HMRC
- Ongoing updates throughout incident

**Operational Response**:
- Branches remained open (normal or extended hours)
- Contact centres remained open (normal or extended hours)
- Staff worked to serve customers despite technology limitations

### Post-Incident Actions

**Customer Remediation**:
- Commitment: "No customer will be out of pocket"
- Proactive remediation effort
- Focus on vulnerable customers

**Technical Response**:
- 2 February: Mitigation actions on Mainframe provider advice
- 21 February: Software fix received
- Comprehensive testing of fix underway

**Governance**:
- Third-party review of root cause and response
- Objective: Identify learnings for future incidents

---

## Historical Context

### Incident Pattern (January 2023 - January 2025)

**Total incidents reported to FCA**: 33
- **15 incidents**: Caused 93 hours total customer impact across channels
- **18 incidents**: No direct channel impact but affected payment processing
- **Excludes**: The 31 January incident

**Breakdown by cause**:
- Technology change: 12 instances (36%)
- Operational error: 10 instances (30%)
- Third-party failure: 7 instances (21%)
- Other: 4 instances (12%)

### Implications
- **Systemic issues**: Pattern suggests recurring vulnerabilities
- **Learning failures**: Similar incidents not prevented
- **Multiple failure modes**: Not a single type of problem
- **Ongoing risk**: Recent incident adds to concerning pattern

---

## Key Quotes from Sources

### From Newspaper Article (Aliaj, 2025)

> "We know this isn't ideal." - Barclays online statement

> "We know some customers may be having issues trying to make a payment to HMRC ahead of the deadline for self-assessment tax returns. We're in direct contact with HMRC, they are aware of the technical issues with our system and have confirmed today's issues will not result in late-payment penalties, as they don't apply until 1st March." - Barclays spokesperson

> "We will ensure that no customer is left out of pocket because of delayed payments caused by this incident." - Barclays spokesperson

> "The outage came at a particularly critical time for Barclays' more than 20 million UK customers, many of whom were set to receive their first pay cheque of the year."

> "A number of customers disputed this, saying they had been unable to make card payments." - Re: Barclays claim cards were working normally

### From CEO Letter (Maru, 2025)

> "We are deeply sorry for the impact this incident has had on our customers who were not able to access some of our services during the incident period."

> "On identification of the incident, we immediately enacted our Crisis Management procedures which allowed us to prioritise restoring services as swiftly as possible to impacted customers, with a particular focus on those with vulnerable characteristics."

> "Throughout the incident, our priority and focus was to act quickly with our customers' interests always front of mind."

> "We have identified the root cause as being a software problem in a critical module of our UK Mainframe operating system and can confirm that this incident was not due to a cyber-attack or any other malicious activity."

> "This problem caused progressively severe degradation of Mainframe processing performance through a substantial part of 31st January and into the following day."

> "Our UK Mainframe underpins core banking applications of deposits, overdrafts, and debit cards across Barclays UK, with services also supporting our International & UK Corporate Bank and Private Bank & Wealth Management (PBWM) businesses."

> "Within the first two hours of the incident, we proactively communicated about the issues with customers via multiple channels."

> "Our proactive remediation effort remains focused on the prioritisation of customers with vulnerable characteristics and ensuring no customer will be out of pocket as a result of this incident."

---

## Systems Analysis

### System Complexity Indicators

**Multiple components**:
- Mainframe (core)
- Mobile app
- Online banking
- Payment processing
- Debit card systems
- Branch systems
- Contact centre systems
- Interactive phone systems
- External integrations

**Multiple stakeholders**:
- 13+ million customers
- Barclays staff (IT, branches, contact centres)
- Executives/board
- Regulators
- HMRC
- Mainframe provider
- Media
- Parliamentary oversight

**Tight coupling**:
- Single Mainframe failure cascaded through entire system
- No apparent redundancy or failover
- All channels affected simultaneously

### Emergent Properties

**System behaviour greater than sum of parts**:
- Single software fault → system-wide outage
- Progressive degradation (not immediate total failure)
- Media amplification effect
- Regulatory response
- Political scrutiny

**Unpredictable consequences**:
- Timing coincided with critical dates (payday, tax deadline)
- Customer panic and frustration
- Long contact centre wait times creating feedback loop
- Reputational damage beyond technical impact

### Adaptation Evidence

**Successful adaptation**:
- Crisis Management procedures activated
- Prioritization of vulnerable customers
- Extended branch/contact centre hours
- Multi-channel communication strategy
- Direct liaison with HMRC
- Manual workarounds in branches

**Failed adaptation**:
- Pattern of 33 incidents suggests learning failures
- Similar root causes recurring (technology change, operational error)
- Insufficient testing/prevention mechanisms
- Dependency on Mainframe provider for fix

### Co-evolution

**System evolved with environment**:
- 13 million digitally active customers (growing digital adoption)
- Regulatory framework (PSR 2017 reporting requirements)
- External service integrations (address finder, payment services)
- Social media communication channels

**Environment shaped by system**:
- Customer expectations of 24/7 availability
- Regulatory scrutiny increases after incidents
- Parliamentary oversight triggered
- Media attention shapes public perception

**Ongoing co-evolution**:
- Third-party review will drive system changes
- Regulatory response may change requirements
- Customer expectations will increase
- Technology landscape continues to evolve

---

## Failure Analysis Framework

### What Constitutes Failure?

**Multiple perspectives on failure**:

1. **Customer perspective**:
   - Inability to access money
   - Failed payments
   - Long wait times
   - Stress and anxiety
   - **Verdict**: Clear failure

2. **Barclays operational perspective**:
   - System outage
   - Service unavailability
   - Crisis management needed
   - **Verdict**: Clear failure

3. **Regulatory perspective**:
   - Reportable incident under PSR 2017
   - Customer harm
   - Pattern of incidents
   - **Verdict**: Clear failure

4. **Barclays technical perspective**:
   - Software fault occurred
   - BUT: Not cyber attack, recovery achieved
   - **Verdict**: Failure, but with mitigating factors

5. **Mainframe provider perspective**:
   - Software problem in their system
   - BUT: May argue complexity, testing limitations
   - **Verdict**: Likely defensive about being labeled "failure"

6. **Media perspective**:
   - Major bank outage during critical time
   - Customer impact
   - **Verdict**: Newsworthy failure

### Significance of Failure

**Why this matters**:
1. **Scale**: 13+ million customers affected
2. **Timing**: Critical payday/tax deadline period
3. **Duration**: Multi-day incident
4. **Pattern**: Part of 33 incidents in 2 years
5. **Systemic**: Single point of failure revealed
6. **Trust**: Reputational damage to banking system
7. **Regulatory**: Parliamentary inquiry triggered
8. **Financial**: Customer remediation costs

---

## Dependencies and Vulnerabilities

### Critical Dependencies

**Internal**:
- UK Mainframe (single point of failure)
- Multiple services depend on Mainframe
- Branch/contact centre technology
- Payment processing systems

**External**:
- Mainframe provider (for software and fixes)
- Address finder service
- Payment service providers
- Telecommunications infrastructure
- Internet connectivity

### Vulnerabilities Exposed

1. **Single point of failure**: Mainframe has no apparent redundancy
2. **Cascading failures**: One component failure affects entire system
3. **Testing inadequacy**: Software fault not caught before deployment
4. **Provider dependency**: Required external vendor for fix
5. **Communication challenges**: Multiple channels needed coordination
6. **Capacity issues**: Contact centres overwhelmed
7. **Timing vulnerability**: No ability to schedule outage window

---

## Lessons and Principles

### Violated Principles (from TM353 Block 1 Part 3)

**Complexity management**:
- System too tightly coupled
- Insufficient redundancy
- Limited failover capability

**Resilience**:
- Single point of failure
- Inadequate graceful degradation
- Insufficient redundancy

**Testing and quality**:
- Software fault reached production
- Insufficient testing of critical module
- No detection before customer impact

**Learning from failure**:
- 33 incidents in 2 years shows pattern
- Similar causes recurring
- Insufficient prevention after previous incidents

### Emerging Lessons

**From this incident**:
1. Mainframe dependency is critical vulnerability
2. Communication must be faster and clearer
3. Testing of critical systems needs enhancement
4. Redundancy/failover systems required
5. Pattern analysis needed to prevent recurrence
6. Third-party dependencies carry risk
7. Crisis management procedures work but need technical prevention

**From historical pattern**:
1. Technology change is high-risk activity
2. Operational errors are common
3. Third-party reliability is concern
4. Current governance insufficient to prevent recurrence

---

## References

Aliaj, O. (2025) 'Barclays app outage deprives customers of banking services', *Financial Times*, 31 January. Available at: <https://www-ft-com.libezproxy.open.ac.uk/content/ffb1b828-0f58-431b-893a-c39284ea2d88> (Accessed: 18 July 2025).

Maru, V. (2025) *Letter to Treasury Committee of the UK Parliament*, 26 February. Available at: <https://committees.parliament.uk/publications/46937/documents/242221/default/> (Accessed: 18 July 2025).

---

## Quick Facts for TMA Answers

**When citing numbers**:
- 13+ million digitally active UK customers
- 5% login failure rate
- 17% attempted payments (of successful logins)
- 56% payment failure rate (of attempts)
- 33 incidents in 2 years (Jan 2023 - Jan 2025)
- 15 incidents caused 93 hours downtime
- 9:48am start time, 31 January 2025
- 11:34am regulator notification (1h 46m delay)
- 01:30am Saturday partial recovery
- 12:00pm Saturday largely resolved
- Sunday stable

**When describing system**:
- UK Mainframe = core system
- Underpins: deposits, overdrafts, debit cards
- Serves: Barclays UK + Corporate + PBWM
- Multiple channels affected: app, online, payments, branches, contact centres

**When describing causes**:
- Software problem in critical Mainframe module
- NOT cyber attack
- Pattern: technology change (12), operational error (10), third-party (7)

**When describing response**:
- Crisis Management procedures enacted immediately
- Communications within 2 hours
- Vulnerable customers prioritized
- Extended branch/contact hours
- HMRC contacted directly
- No customer out of pocket commitment

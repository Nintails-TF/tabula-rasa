---
date created: Monday, December 1st 2025, 1:49:46 pm
date modified: Thursday, December 4th 2025, 9:47:16 am
---

# TM353 TMA 01 - Report Submission

**Student**: [Your Name]  
**PI**: [Your Personal Identifier]  
**Module**: TM353 IT Systems Planning for Success  
**Assignment**: TMA 01  
**Submission Date**: [Date]

---

## Question 1: Successful IT Systems (30 marks)

### Part (a) - Spray Diagram or Rich Picture (10 marks)

![[../../../../03_Reference/Pictures/TMA01-spray-diagram.drawio (1).png]]

**Rationale and Insights**:
I've chosen this approach to building a spray diagram, as when working through various pieces of material, I found the Figure 2.4. that depicted the Post Office Horizon failure to be very readable. I decided to include details about how key stakeholders such as customer and staff where effected, highlighting the stress and anxiety felt by both parties. 

The core insight was that the system failure was catastrophic because it occurred across 3 different domains (technical, temporal, social/cultural). e.g. The mainframe bug was the catalyst, it happened during tax season, Barclay's didn't learn from previous incidents.

**Word Count: 98**

---

### Part (b) - Multiple Cause Diagram (10 marks)

**Significant event selected**: Widespread customer dissatisfaction and financial hardship.
![[../../../../03_Reference/Pictures/TM353-Multiple-Cause-Diagram.drawio.png]]

**Rationale and Insights**:

I examined widespread customer frustration as the significant event, focusing on how system failure impacts business's core need: maintaining customer relationships. I began with root causes, expanding outward before grouping spatially into four categories: temporal amplifiers, technical failures, operational failures, and customer perspective.

What I found was how the technical issue bled into all categories except the temporal. The key insight was how customer-company trust is critical. That emotions and negative perceptions can turn a technical incident into a relationship breakdown.

Systems that are customer facing require robustness, as trust is hard to rebuild once broken.

**Word count: 96**

---

### Part (c) - Five Key Stakeholders (10 marks)

I've used **Dix's four classes of stakeholders** approach to identify five key stakeholders.
#### Primary Stakeholders
Barclays 13+ million active customers who operate through online/mobile banking, branch services, and debit cards. Their primary interest is fundamental: Reliable access to deposits and withdrawals to store or access cash either physically or digitally. 
#### Secondary Stakeholders
HMRC relies on payments that are processed through Barclays system. Their interest is tied into the financial system as a whole, they want citizens to be able to submit self-assessment taxes by the deadline. System failure creates administrative burden on their end.

Barclays Branch and Contact Centre Staff are also secondary stakeholders, they depend on the system outputs to effectively serve customers. Their interest is in giving accurate, current system data to process transactions and resolve issues. System failure can break this process and make them unable to help customers.
#### Tertiary Stakeholders:
Barclays Senior Management/CEO are affected by system failure through multiple channels: reputational damage, regulatory scrutiny, and in this case parliamentary accountability. Their interest is in organizational reputation and regulatory compliance, they face consequences from the FCA/Parliament if the system breaks down.
#### Facilitating Stakeholders:
UK Mainframe provider is the external vendor who designed, developed, and maintains the critical Mainframe software to ensure that processes at Barclays work as intended. Their interest is in building a reliable system, that works well for their clients. A system failure in this case forces them to develop a fix quickly and manage liability.

**Word count: 245**

---

## Question 2: Systems Failures (30 marks)

### Part (a) - Identifying and Analysing Failures (8 marks)

**Three significant failures identified**:

1. **Single point of failure architecture** - The UK Mainframe had no redundancy or backup system. Causing a system-wide collapse when a single module failed. The mainframe code, or Barclays implementation of the mainframe should of been changed.
2. **Pattern of reoccurring incidents** - 33 incidents in 2 years with similar root causes to this event. Systematic failure with the current approach and a failure to learn from mistakes.
3. **Inadequate testing procedures** - Software fault that was critical within the Mainframe model should never of reached live production.


**Analysis**:

I have chosen the **pattern of recurring incidents** as my main issue. I consider this to be a critical failure as 33 incidents in two years indicates systemic inability to learn and improve organizational processes. The same root causes *(technology change, operational error, third-party issues)* repeatedly occur despite previous incidents. This is suitable for further analysis as it reveals deeper cultural and governance failures that resist technical fixes; changing organizational culture and learning mechanisms is far more challenging than fixing individual bugs. The **FCA** and **customers** would strongly agree this represents failure. **Barclays management** might defensively argue complex systems inevitably experience incidents.

**Word Count: 196**

---

### Part (b) - Systems Map (10 marks)

**Sociotechnical system selected**: Barclays Banking Delivery System
![[../../../../03_Reference/Pictures/Pasted image 20251203154502.png]]
**Rationale and Insights**:
I selected Barclays **Banking Service Delivery**, drawing the boundary around components Barclays directly operates. I positioned **UK Mainframe System Infrastructure straddling the boundary** because ownership is ambiguous. Barclays depends entirely on it but cannot control it. This represents a **critical architectural error**: tight coupling to partially-controlled infrastructure. 

I placed the 33 previous incidents within the external environment, as it is historical pattern that the system failed to learn from. The key insight: this dependency creates systemic vulnerability—when the Mainframe fails, cascading collapse occurs across all services, yet accountability for prevention is unclear between Barclays and Mainframe UK.

**Word count: 98**

---

### Part (c) - Influence Diagram (6 marks)
![[../../../../03_Reference/Pictures/Pasted image 20251203162911.png]]


**Transition and Further Insights**:

I transitioned from systems map to influence diagram by adding arrows, starting with obvious service delivery flows (technical infrastructure → customers), then mapping operational dependencies and external influences. 

The key insight: **the UK Mainframe Infrastructure's central position with arrows radiating to all technical components demonstrates single-point-of-failure vulnerability**—when it fails, cascading collapse occurs. 

The **dotted arrow from 33 previous incidents to IT Team** shows this influence should exist but is weak—the system fails to learn from failure history. This reveals how tight coupling and broken organizational learning combine to enable recurring incidents.

**Word Count: 92**

---

### Part (d) - Lessons and Prevention (6 marks)

The 33 recurring incidents reveal systematic organizational failure, not just technical problems.

The **three root causes**: architectural vulnerability from tight coupling to single infrastructure, ambiguous product ownership, and insufficient learning to prevent recurrence.

Prevention occurs within two main factors:
- **Architectural**
	- Implement redundancy eliminating single points of failure; establish clear ownership boundaries with Mainframe UK Provider defining responsibilities and testing protocols before production deployment.
- **Organisational**
	- Mandate post-incident reviews ensuring lessons directly influence testing procedures and implementation; foster learning culture where failure analysis drives improvement.

Technical bug fixes will fix the symptoms, where as organisational change will prevent reoccurrence.

**Word count: 101**

---

## Question 3: Systems Concepts (20 marks)

Understanding and modelling **complexity** was a critical issue within Barclays, as they treated their infrastructure as a **simple system** when it exhibited characteristics of a **complex system**. (Casti, 1994) identifies four factors distinguishing complex from simple systems: **predictability**, **interactions**, **control**, and **decomposability**. The case study particularly demonstrates complexity through **interactions** and **control**.

The **interactions** within Barclays' IT infrastructure spanned numerous interdependent components. The critical incident demonstrates this: the initial Mainframe failure cascaded through mobile/web applications, debit cards, and payment processing, an unpredictable cascade characteristic of complex systems. **Control** was fragmented between Barclays (institutional knowledge) and Mainframe UK (technical expertise). This distributed control reduced **decomposability**. Barclays could not easily isolate or fix individual components during the outage, demonstrating that the system's complexity required more coordinated management across organizational boundaries.

**Emergence** refers to properties that arise from interactions between system components that are not present in the components themselves (Open University, 2025, p.137-139). The Barclays case demonstrates emergence through **organizational learning failure**. The inability to prevent recurring incidents emerged from interactions between technical complexity, organizational culture, and fragmented responsibilities.

No single component contained this failure; it arose from how technical systems' complexity overwhelmed organizational capacity for effective response and learning. Similarly, **system fragility** emerged from the interaction of tightly-coupled components, insufficient redundancy, and accumulated technical debt. Thus, creating **brittleness** not predictable from examining individual components.

**Adaptation** refers to how systems change in response to their environment to maintain viability (Open University, 2025, p.142-143). The Barclays case reveals **inadequate adaptation** despite environmental pressures. Following each incident, Barclays implemented technical controls and process changes which demonstrated attempted adaptation to failures. However, the **recurring nature** of incidents between 2023-2025 indicates these adaptations were insufficient. The adaptations were primarily **reactive and technical** (fixing immediate causes) rather than **proactive and systemic** (addressing underlying organizational and cultural factors).

Effective adaptation requires not only technical change, but cultural and organizational change too. Which is much harder to achieve, as without external challenge or a devil's advocate. Fixing systemic problems with people is more challenging, as there is no social cost of fixing a bug, but changing an organisation or people has a high social cost.

**Co-evolution** describes how interconnected systems mutually influence each other's development over time (Open University, 2025, p.149). The Barclays case demonstrates **problematic co-evolution** across multiple dimensions. Technical systems and organizational capabilities should have co-evolved harmoniously, but instead the **technical infrastructure evolved faster than organizational capacity** to manage it—creating a capability gap that contributed to failures. Similarly, customer expectations co-evolved with digital banking technology, increasing pressure on system reliability while Barclays' infrastructure remained fragile. Third-party relationships co-evolved with Barclays' operations, creating interdependencies that distributed knowledge and control.

The core insight is that when co-evolution is mismatched between parties, it's similar to a three legged race - where one person speeds off and other gets dragged, resulting in them both falling. Successful IT systems require alignment and co-ordination within technical, organizational, and environmental domains to ensure harmonious co-evolution.

**Word count: 496**

---

## Question 4: External Context Analysis (20 marks)

**Scenario**: Planning team for small IT consultancy expanding to support digital transformation in rural healthcare settings.

### Part (a) - Identification (7 marks)

| Dimension      | Factor 1                                      | Factor 2                   | Description                                                                                                                                                             |
| -------------- | --------------------------------------------- | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Socio-cultural | Aging Population                              | Digital Literacy levels    | Rural populations often have lower digital skills, meaning strong UI/UX design is key. Aging populations often exacerbate this.                                         |
| Technology     | Broadband Infrastructure                      | Cybersecurity Threats      | Remote rural can still have limited internet connectivity/speeds, solutions that are low bandwidth or have offline functionality help.                                  |
| Economic       | Cost of Implementation                        | Rural economic conditions  | High upfront implementation costs, create a cost-effective solution to suit the budget.                                                                                 |
| Environmental  | Geographical Challenges with remote locations | Climate impact             | Scattered population makes it difficult to access physical support systems. Rural citizens highly value climate/green space, so minimize climate impact where possible. |
| Political      | Government healthcare policy                  | Funding priorities         | Government policy can provide either opportunity or challenges, depending on how they are aligned within the area.                                                      |
| Legal          | Data protection (GDPR)                        | Accessbility requirements  | Healthcare data is very sensitive, so sufficient encryption and protection of data is necessary for regulatory compliance                                               |
| Ethical        | Digital divide                                | Equal access to healthcare | Need to be careful to not exclude those who are vulnerable. As a digital solution could exclude those who need it most, ensure robust accessibility features.           |

**Word Count: 125**

---

### Part (b) - Analysis (5 marks)

**Opportunities**: 

**Government Funding:** Government investment in healthcare digitalisation provides grants and contracts, creating revenue opportunities for transformation projects in under-invested rural areas.

**High Value Proposition:** Successfully delivering digital healthcare to rural populations enhances consultancy reputation and demonstrates real impact, boosting the reputation and potential clients for a consultancy firm.

**Threats**: 

**Poor Broadband Infrastructure:** Rural areas often lack modern connectivity, requiring additional resources to design low-bandwidth or offline-capable solutions, increasing development costs and complexity.

**GDPR Compliance/Cybersecurity:** Healthcare data regulations create significant compliance burdens, extending development timelines and costs. Cyber threats require robust security measures, increasing operational expenses and liability risks.

**Word Count: 99**

---

### Part (c) - Prioritisation (5 marks)

Chosen Factor: **Impact on the organisation and stakeholders**

The most critical opportunity is: **Government Funding**. Without this factor, public facing rural organisations cannot afford a digital transformation or maintenance of one. Without working together with the government, the project will not even get its feet off the ground.

The most critical threat is: **GDPR Compliance/Cybersecurity**. Non-compliance poses a severe risk due to fines, legal liability, and reputational damage. Which harms the rural healthcare organisations and the reputation of the consultancy group. Data breaches affect vulnerable patients, cause ethical harm, and destroy trust with stakeholders.

**Word Count: 95**

---

### Part (d) - Reflection (3 marks)

As a systems planner, Personally I'm biased in a cynical direction. I'm looking at this project in terms of risk, and where as developing a strong IT system for a rural population can have an enormous positive impact. Simultaneously, it is a very risky and difficult endeavour for consultants.

This highlights how important aspects outside of technical aspect, such as social, economic, and political environments/states wildly affect the success/failure of IT systems. In the future, when planning or building projects, I'd ensure to focus and understand what these external factors are, to increase the chance of success.

**Word Count: 99**

---

## References

Aliaj, O. (2025) 'Barclays app outage deprives customers of banking services', *Financial Times*, 31 January. Available at: <https://www-ft-com.libezproxy.open.ac.uk/content/ffb1b828-0f58-431b-893a-c39284ea2d88> (Accessed: 1 December 2025).

Maru, V. (2025) *Letter to Treasury Committee of the UK Parliament*, 26 February. Available at: <https://committees.parliament.uk/publications/46937/documents/242221/default/> (Accessed: 1 December 2025).

**Casti, J.L. (1994)** *Complexification: Explaining a Paradoxical World Through the Science of Surprise*. New York: HarperCollins.

**The Open University (2025)** *TM353 IT Systems: planning for success*, Milton Keynes: The Open University.
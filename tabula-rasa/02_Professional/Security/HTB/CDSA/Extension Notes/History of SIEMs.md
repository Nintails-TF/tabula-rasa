---
date created: Wednesday, October 15th 2025, 2:07:45 pm
date modified: Wednesday, October 15th 2025, 2:08:06 pm
Parent Link: "[[../Academy Modules/Security monitoring and SIEM Fundamentals#The Evolution and History of SIEM | SIEM Fundementals]]"
---

# History of SIEMs

### First Gen SIEMs (2000s-2010s):
- On premises architecture
	- Expensive and slow, annoying to setup, etc.
- Rule-based corrections
	- Built upon static rules, novel attacks couldn't be detected.
- Log-centric collection
	- Flat text log file collection, no insight.
- Manual tuning
	- Analyst had to spend large amounts of time filtering noise and adjusting rules. Meaning high false-positive rates, and fatigue from alerts.
- Limited Context
	- SIEMs didn't understand relationships between assets, users or applications.
	- This meant that alerts lacked depth, you understood that something was happening, but not why or how critical it was.
- Mostly compliance-driven
	- PCI DSS, SOX, HIPAA, and auditing.
	- Companies needed logs and reporting not real time detection, security was secondary to hitting compliance.

### 2nd Gen SIEMs (2010s-Now):
- Cloud architecture
	- Hybrid or cloud deployments, environment where fully accounted for.
- Behavioural analytics and ML
	- User and entity behaviour was analysed rather than just rule-based.
	- This helped reduce false positives and uncover insider threats or slower breaches.
- Integrated SOAR
	- Automated repetitive tasks (enrichment, ticket creation, IP blocking, etc.)
	- Playbooks could run automatically after certain alerts and triggers
	- Speeds up response times and reduces workloads for analysts.
- Contextualization
	- Correlates logs with asset databases. So "Who, What, Where, and business impact".
	- Improves understanding of risk and what to prioritize.
- Threat Intelligence integration
	- Gives live information of known malicious IPs, hashes, and domains
	- Correlates events with known threats. Helps identify attackers quicker.
- Supports hybrid environments
	- See everything from one pane of glass.
- Easier to use.
	- Improved dashboards and more accessible.

### 3rd Generation SIEMs (2025-2030+ Onwards):
- Generative AI and Advantage ML
	- Uses LLMs to summarise alerts and automatically generate queries.
- Strong automation and orchestration
	- Low level threats are handled autonomously. 
	- Full integration with SOAR, XDR, and data lake environments.
	- SOC analysts only need to deal with complex, high impact threats.
- Adaptive Behavioural analytics
	- Baselines adapt based on feedback loops.
	- Combines network, endpoint, identity, and cloud details into a unified model.
- More context provided
	- Risk-based prioritization, analysts see why something matters instantly.
- Assistive Tech
	- Co-pilots summarise incidents, give next actions, generate reports and explain reasoning.
	- Can communicate with SIEMs in natural language.
- Integration with other security tools
	- Deep integration across other security tech ecosystems.
		- EDR, NDR, IAM, CSPM, XDR
- Risk-based alerting
	- Low-value is filtered automatically. 
	- Alerts are scored by business impact and exploitability.

### My Take:
 The purpose of 3.0 is to make 2.0 SIEMs more automatic and easy to digest, let automated systems or AI deal with smaller alerts, and give humans the tools they need for bigger alerts.

2.0 SIEMs will have more of these 3.0 tools or ideas placed into them. There will be bugs and issues and fuckups, but the tech will get there eventually.

Issues are that data privacy is hard to enforce, models can be biased and screw up, the skills aren't there, it's expensive, people can blindly trust AI, and in regulated environments auditing is a nightmare for AI.

Big issue is that security professionals and auditors need to explain WHY something happened, they can't just trust an black box AI answer.

Regulated industries and governments will likely being using SIEMs 1.0 or 2.0 depending on how agile they are for the next decade or so.

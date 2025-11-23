---
date created: Wednesday, November 12th 2025, 10:09:10 am
date modified: Saturday, November 22nd 2025, 2:58:44 pm
---

# 1. Introduction:

Success and failure are two sides of the same coin in IT systems. In order to produce high quality systems we need to consider the following:

1. How to plan systems for success and how critical success is in it systems. Consequently, we need to look at failures as well.
	1. What is our definition of success? How does that look different for a wide range of stakeholders.
	2. How do we win/lose, as a systems designer?
2. Why IT systems are always sociotechnical and what does this mean? Why are all IT systems sociotechnical.
	1. e.g. Different groups interact with the system, different people have opinions on the system, people need to fund or maintain the system, etc.
3. How can we model IT systems using system design concepts and techniques.
	1. Practically, how do we display and use the knowledge about system design.
	2. System diagrams are key here.

***

# 1.1. The Importance of Success and Failure in IT Systems:

IT systems are used to describe the systems at play, *software* doesn't full encapsulate these ideals. This is for two main factors:

1. Business or Organisational IT solutions are often a mix of hardware, software, networks, cloud, and other technical systems.
2. IT systems also include human, cultural, and organisational factors too.

> IT systems are not just software, but are hardware, organisational, and human systems.

Another core idea, is that what is meant by success and failure within IT systems. This answer depends on who you talk to within the chain of system design. A project manager cares if the system is completed in time and on budget, a programmer cares if the code is high-quality and the system runs well, an end user cares if the system helps them with their job.

For now, the following definitions are enough:

**Successful IT systems** are systems that meets the needs of the organisation or company as well as other relevant stakeholders that are related to the organisation but may be external.

**Failed IT systems** are systems that do not meet the needs of stakeholders within and org and doesn't help other key stakeholders.

Large IT systems failures are often talked about, but designing small systems well is also critical as the pave the road and act as a platform in which greater systems can be launched. In the public sector, large failures get massive press. In private if a system works well, it gets published if it does poorly then it is forgotten.

***

## Case Studies of Success and Failure within IT Systems:

### Success - Mitchells and Butlers:

M&B is a pub brand chain, but the IT systems were outdated and struggling after a growth. A new acquisition signalled change.

Over a five-year course, the company did the following:

- Moved their infrastructure to the cloud to be all in once place ran by Fujitsu.
- Created a data store to collect more data and present it to the head office within minutes.
- All the hardware running on mid-tier IBM servers was either virtualized and ported or scrapped and migrated.
- They worked with EquaTerra on how to benchmark the system. Enabling them to figure out capabilities before hand and running costs.
- All elements of IT systems were condensed down into 6 factors: *data centre, network, outlets, end-users, central services, and applications.*
	- The outputs of each area was looked at, and they figured out what they wanted to focus on first.
- The data centre and network were prioritised first, as they were the backbone that supported the whole system.
- They standardised payroll systems, human resources, property systems for each bar or end-user.
	- They provided tweaks and changes in edge-cases.

### Failures - BBC Digital Media Initiative:

The BBC DMI was an £100m bust. It intended to make the digital archive tapeless.

From 2007 to 2013, the project did the following:

- A production system linked to the BBC broadcasting archive didn't function as intended. Reporters couldn't get access to old archive media to use for their reports and news articles.
	- They had to drive around in taxis with old tape recordings from office to office.
- The money wasn't spent carefully and considerately, money was being thrown around.
- The scope of the project was too big and got out of hand.
- John Linwood the CTO is being kicked out temporarily and had previously worked at Microsoft and Yahoo.
	- He was being paid well, and had a bonus last year.
- An issue with the system was that much of the software used could only be used if the system was fully completed.
- PrincewaterhouseCoopers is investigating what went wrong in terms of project management, control, and governance.  
- Tools and systems were made by private corporations that could of done heavy lifting for the system, but weren't used.
- The systems that were developed, Fabric archive database, was far slower than existing libraries that used tape copies.
- No technology was delivered from 2008-2009 and the funding contract was terminated, the BBC then brought the project in-house. But couldn't make the project profitable.

### Differences - Why Did M&B Succeed and BBC Fail:

The three main differences were the following:

1. B&M worked with other organisations and got them to fulfil tasks that they couldn't do. The BBC DMI did not leverage new tools or systems.
2. B&M produced more modular systems that could get off the ground and help stakeholders right away with data centre and network operations being focused on first. The BBC DMI only worked if the whole project succeeded, which resulted in poor deliverables.
3. B&M had better sociotechnical practices in place, which resulted in higher quality decisions being made. BBC DMI had poor leadership and sociotechnical practices.

The learning opportunities are:

- Bespoke systems carry additional technical debt and risk, if other existing tools can help, use them. The public sector can often demand these without understanding the drawbacks.
- Organisational structure and practices matter a huge amount. Departments working together rather than technical folk working in isolation, working with other companies to come to solutions.
	- Maintaining trust and success with stakeholders is very important, give them some wins whilst the product is compounding, and they'll remain happy and cooperative. Make their work harder and make them struggle and cooperation and trust will dry up.
- Waterfall methods require very diligent understanding of scope and clear deadlines and timelines, they can carry great amounts of risk if the management or leadership keeps promising more and more.
	- There must be ruthless prioritisation on what a system does and what is important to stakeholders.

### Conclusion:

Case studies offer a great insight into developing your own processes into designing quality systems, by looking and the successes and failures and why they happened. You can leverage strengths and minimize weaknesses.

**Activity -** Look at another two case studies, one of success and one of failure and talk about it in the group form.

***

# 1.2 Sociotechnical Nature of IT Systems:

An IT system is much more than a computer system. It's a mix or a stew of: software, hardware, organisational culture, and psychology.

We can refer to other systems outside of computing, such as the financial system, or healthcare system, or the environmental system, energy system, etc. These may seem disconnected but all of these fields require the attribute of [[../Glossary#^st-def|Systems Thinking]].

Systems aren't real entities, but they are more abstract. These systems are made by people or groups of people to reach a goal or outcome (Either consciously/subconsciously or actively or inadvertently). 

Boundaries of a system can be fuzzy, different people working within and outside said system may have different opinions of where to draw the line. For example: 

The **healthcare system:** You've got doctors, GPs, Pharmacists, admins, insurance companies, dentists, opticians, patients, government regulators, alternative medicine, supplementation. And more and more. *We break this up by splitting the components of the system: Public health, private health, government systems, primary care, secondary care, etc.*

Different people have different perspective on what the healthcare system actually is, in essence.

Within the module, there are four main approaches to system thinking addressed:
1. **Systems diagrams** - The systems engineer approach to create large-scale systems. Soft system methodology of Peter Checkland is ascribed to here.
2. **Socialtechnological Systems Thinking** - General systems theory, but introducing social aspects that come with technological changes and how to address them.
3. **Complexity Theory** - Cybernetics and how they've boosted understanding of natural sciences such as Biology.
4. **Control Engineering** - Reliability and dependability within hardware systems mainly.

A core concept is that all IT systems are [[../Glossary#^SoTech-def|Sociotechnical]]. Ken Eason, describes the importance of this:

> Understanding how people work and co-operating with tools and technology to get work done. What is the reality for working life within an organisation to achieve their goals? What are the dependencies between people and tech, a new change within a system may be technically brilliant but may be a disaster organisationally, the change in environment may harm people or the company.
> 
> A successful system has to adapt to the needs of an organisation and people, in a perfect world, both are flexible and eager, but we cannot guarantee that an organisation or people are, so we must ensure that the system can bend and twist as needed to suit people. Or they may come to resent or undermine a rigid system that has ruined their current working approach.

We can illustrate the concepts of an IT system like so:
![[../../../../03_Reference/Pictures/IT system flow.png]]
***
### 1.2.1 IT Systems in Evolution:

It is very rare for IT systems to be developed from scratch, most of what happens is closer to an evolutionary approach, we take what works and is useful and bring it to the next generation of IT systems.

- Custom setups and configs of 3rd party tools
- Modification of existing systems
- Bolting together components to create a original whole
- Agile software development morphing to suit rapidly changing needs and requirements.
- Cloud used for data storage and processing, decreasing need for in-house solutions but increasing needs for strong network connectivity.

This [[../Glossary#^evo-def|Evolutionary]] approach is different than the Classical, life cycle method - IT systems followed a standard lifecycle, models like the SSADM, followed the six model structure of:

1. Feasibility study
	1. Can this be done?
2. System investigation
	1. What is currently happening?
3. System analysis
	1. Why is this happening?
4. System design
	1. What can we change to make it better?
5. Implementation
	1. Actually making the system
6. Maintenance.
	1. Keeping the engine running.

This model assumes a step-by-step approach, this waterfall flow is useful to know, but isn't practical for ever solution to follow. Take for example maintenance: This can be between 40%-90% of a system's process depending on what's being made, but it isn't weighted heavily in this model.

**The Agile methodology has been the dominant approach in the modern era of IT systems design.**
### Activity - Experiences of IT Systems and Approach Analysis:

**Q:** What are the strengths and weaknesses of the evolutionary model and the life cycle model? Give some examples for each.

**A:** A life cycle approach would be better in environments where the requirements are more static and aren't going to change rapidly, an example of this would be hospitals or aeronautics - since you have to get things right on the first try and there are strict standards, you can't afford to move fast and break things.

I do feel as if the evolutionary approach works better in a more modern setting: clients can communicate rapidly with providers and ask for changes, teams are bigger - some work remote or in office, it provides a business advantage to make your clients happy and shift to their desires. You can show process, build up trust, and get real feedback from users quicker to build a better system.

Where the evolutionary approach falters could be in the lack of structure or direction which could lead to incorrect prioritisation of needs, feature creep, and unnecessary strain on developers. It can be hard to trace who wants what, without strong technical leadership and architectural knowledge, you can run into pitfalls that hurt your own team and clients.

***

## 1.2.2. What is Technology?

### Activity - How to Define and Understand Technology:

**Q:** Answer the following bullet points:
- Why is it important to understand technology?
- What is the essential purpose of technological innovation?
- What distinctions are drawn between technology and science?
- What kinds of interaction are said to be involved in technologies and innovation?
- What outcomes and consequences are associated with technologies?
- In your view, is Andy Lane's definition of technology use or an accurate one, how would you rephrase it or define it yourself?

**A:** [[../Glossary#^tech-def|Technology]] has an enormous impact on the lives of people, people shape technology but also technology shapes the behaviour of people as well. For this reason, people view tech as positive/neutral/negative depending if it enriches or damages their life.

Technology differs from science; Science deals with the understanding of the natural world. Technology is about meeting a human need. Though, technology does leverage and work in tandem with science. Technological innovations occur because of advances in physics and advances in technology can help physicists learn more.

Technology is an organised process of doing things, it often has large supply chains - similarly to how a coffee shop converts a coffee bean in Kenya to a polystyrene cup of joe. There are many direct and indirect processes at play.

***
## 1.2.3 Systems and Context:

Within IT systems there can be asymmetrical flows of influence between multiple areas. Because these systems are dynamic and change over time (though at differing speeds - technology develops more rapidly than legal policy.)

![[../../../../03_Reference/Pictures/it-systems-influence-flow.png]]

So when designing systems, we should consider the **contextual factors** - what influenced the development of the IT system with the environment and culture at the time?
### Activity - How Was the World Wide Web Created?

## Contextual Factors and Reciprocal Relationships

**1. Socio-cultural ↔ IT System**
- **Context influenced system**: Human social nature drove unexpected uses (email instead of remote computing)
- **System influenced context**: The internet created "a complete transformation in our communications environment, absolutely total, as revolutionary as print"
**2. Technological ↔ IT System**
- **Context influenced system**: Incompatible mainframe computers necessitated networking solutions
- **System influenced context**: The internet sparked "a wave of innovation, sometimes very disruptive innovation"
**3. Economic ↔ IT System**
- **Context influenced system**: Need to efficiently use "very expensive and scarce resources" drove initial development
- **System influenced context**: "undermined and taken the music industry somewhat by surprise" and "created whole industries that never existed before"
**4. Ethical ↔ IT System**
- **Context influenced system**: Designer trust and cooperation led to authentication-free email protocols
- **System influenced context**: Spam disproportionately affects poor countries, creating ethical inequities

## List of Key Contextual Factors
1. **Politico-legal**: Pentagon/ARPA funding, government vs. private control debates, absence of software liability laws
2. **Economic**: Cost of mainframe computers, resource scarcity, new business model creation
3. **Socio-cultural**: Human social nature, trust among researchers, communication preferences over computing
4. **Technological**: Incompatible systems, packet-switching capability, software vulnerability
5. **Ethical**: Security concerns, spam targeting vulnerable populations, hacker ethics
6. **Environmental**: Bandwidth limitations in developing regions, global infrastructure disparities

## Deep Dive: Socio-cultural Factor Relationship

**Initial Context → System Design:** Engineers designed ARPANET for resource sharing (remote login to expensive mainframes), reflecting a utilitarian, efficiency-focused cultural mindset typical of 1960s computing.

**Unexpected Contextual Reality → System Use:** As Naughton explains: "human beings are fundamentally compulsively social individuals and if you give them a really good communications tool they will use it for communicating with one another." Users immediately repurposed the network for email, which designers initially viewed as "frivolous."

**System Response → Cultural Transformation:** This social use wasn't just adopted—it became dominant. The system's fundamental design principle of being "ownerless" and "not optimised for any particular application" actually **enabled** this social appropriation. The "dumb network" philosophy meant "anybody could play, anybody could use it, for whatever purpose they thought of."

**Reciprocal Long-term Effect:** The internet then transformed society itself, creating communication patterns unprecedented in human history. Naughton compares it to the printing press—a technology whose full social implications took centuries to understand. Just as printing "transformed the entire world" over 400 years, the internet is only "less than two decades" into reshaping human social behaviour, and "we have no idea sitting here what that means in the long run."

**Key Insight:** This relationship demonstrates that **socio-cultural contexts can fundamentally redirect technological systems**, and systems designed with flexibility (the "stupid" network principle) are more likely to be successfully appropriated by users in unexpected, socially-driven ways.

***

## 1.2.4. Theoretical Perspectives:

There are four perspectives of technology covered here, as we know technology is more than just a program or hardware piece.
#### Technological Determinism:
In the most extreme form, this refers to technology being the prime driving forces in human development, technological progress is inevitable and will reshape the social world and understanding as we know it.
#### Social Construction of Technology:
This is the opposite of determinism. Technology is shaped by the needs of the people and market, as the social powers and technology are linked. Technology isn't autonomous and a progressive phenomenon

#### Techno-scepticism and Optimism:
Techno-optimism is related to the deterministic position, as it views tech in a positive light. Technology is a benefit and aid to people, rather than a detriment.

Techno-scepticism is the opposite, questioning if technology is helpful and the ownership and control of technology.
### Activity - What is the Relationship between Technology and People?:

**Determinism**:
- **Core belief**: Technology develops inevitably; human/social factors merely mediate timing, not direction.
- **Critical flaw**: Evaluations designed under this bias never question whether technology *should* be developed or if non-tech alternatives would be better.
- **Example**: Manufacturing computerisation (1980s) - union resistance delayed but couldn't prevent adoption; framed as "inevitable progress."

**Social Construction:**
- **Core belief**: Technology is not inevitable; social processes shape technical development.
- **Critical flaw:**
- **Contrast with determinism**: Actively questions whether technologies should exist rather than accepting their inevitability.

**Techno-optimism (Dominant position):**

**Claims**:
- Technological direction is right and positive
- Benefits outweigh risks
- Future tech will compensate losers from earlier stages
- New tech will fix problems caused by old tech
- Technology is politically neutral and liberatory

**Quote**: "Material abundance from markets and technology opens the space for religion, for politics, and for choices of how to live" - Marc Andreesen

**Techno-scepticism:**

**Claims**:
- "Technological progress" is a flawed concept
- Current direction (driven by corporations/states) is wrong
- Cost-benefit balance often neutral or negative
- Belief in technological solutions to social problems is dangerous illusion
- Must address political/social causes, not just symptoms

**Definition**: Critically reflecting on what technologies do *and undo*; deliberating how to live well with technology.
**Example**: Water filter design - don't just solve technical problem; ask *why* filters are necessary, explore contamination causes, examine systemic inequalities.

***

# 1.3. Tools for Making Sense of Sociotechnical IT Systems:

To understand IT systems, we need to define what the system is and isn't. By placing [[../Glossary#^Bo-def|Boundaries]] we start to do this, it's very important choice when designing a system and its hotly contested. For example: Who decides what age you have to be to vote, or if prisoners can vote, etc.

Elements that are stored outside of a **boundary** can be referred to as the [[../Glossary#^Env-def|Environment]] of a system. The components of an environment can influence the system, but the environment cannot be fully controlled by the system.

For most systems, they can be referred to as [[../Glossary#^OS-def|Open Systems]] this means that the boundary between the system and environment is somewhat blurred. As both the environment and system cause each other to change and morph accordingly.

A key part of understanding systems is that - frequently - they are nested within existing systems. We refer to this as [[../Glossary#^subSys-def|Sub-systems]] and these can operate at different levels like a Matryoshka doll, each inner doll fits within a larger one. We can think of the [[../Glossary#^Hier-def|Hierarchy]] of a system, being the level in which you are operating at and exploring the most relevant points.

Systems thinking in this way requires grouping of many components together and calling them a system. You have to grasp how different elements interact and fit together.

Another concept to discuss within IT systems and systems thinking is [[../Glossary#^Em-def|Emergence]], for example a bike: you've got wheels, breaks, gears, etc. When you place them all together you've got something you can move around with - but a break by itself; is much less useful.
***

## 1.3.1 Diagrams and Models:

Models allow people to view a slice of a current situation to gain some kind of insight. Systems diagrams often look different depending on what time, what person, and what purpose they've been created for.

Another great benefit of models is that people can understand them clearly and create them quickly without requiring any up front skills or abilities. There are many different types of diagrams used to describe different things. Make sure to stick to the conventions of a diagram though!
## Systems Maps:

System maps are used to show the structure and key components within a system, they frequently include:

- Title of the system of interest
- Key components
- Boundaries
- Systems into which the components are grouped

It's key that you can write a paragraph to describe what decisions you've made when making said systems diagram, but what insights that you've gained from the process. **(Useful for TMA/EMA).**

Often when consulting a problem, you'll have to consider factors that haven't been directly implied by a client or problem statement. In this way, you can come up with new insights when building systems diagrams.
### Building Systems Maps:

The conventions of a system diagram can be seen within [[Conventions/System-Influence Diagrams|System Diagram Conventions]].

***
## Influence Diagrams:

Systems diagrams/maps are useful, but they only show components, not how they would interact. Influence diagrams as the same as systems maps, but have arrows showing flow between components.

The key conventions are:
- Do not use double headed arrows, use two separate arrows to denote flow in both directions.
- Rarely label arrows, you can use dotted arrows to denote differences.

This is where converting bullets into blobs would be helpful.
![[../../../../03_Reference/Pictures/influence-diagramjpg.jpg]]
## Feedback:

Feedback is when you get information about how what you've done and how the system/environment responds to it.

This can be done in two main ways:

**Balancing/Negative Feedback:** This is when the output is fed back into the input in order to dampen the effect of the input. Think of Cruise control - car hits a certain speed and then slows down to go back to a set speed.

**Reinforcing/Positive Feedback**: This is when the output is fed back into the input which enhances the input or effect. Think of a snowball rolling down a hill.

Sometimes this can be referred to as: **Virtuous/Vicious cycles.** Which describe either desirable developments or detrimental ones within positive feedback. 

Going to the gym could raise danger flags within your body, but be part of a virtuous cycle, where as a drug may lead to positive experience in the body, but be part of a vicious cycle.

## Multiple Cause Diagrams:

Single causality believes that a single act caused an event to happen, where as multiple causality expresses that many factors influence an act to occur. Systems thinkers usually try to see the broader picture; so multiple causality is favoured.

The way that this is typically done, is by breaking down big events into smaller problems. Since even with catastrophes, the writing was already on the wall. 
![[../../../../03_Reference/Pictures/Pasted image 20251122131044.png]]
(Maybe you could argue that you are pointing at events in hindsight to justify what has happened though.)

***
# 1.4. Understanding Success in IT Systems:

What is success within IT systems, how can we model this and understand this better? The Standish Group - IT consultants who monitored IT project performance from 1994 to 2020, with around 5000 IT projects per annum - have grouped the projects into the follow table:

| Year           | **2012** | **2013** | **2014** | **2015** | 2016 | **2018** | **2020** |
| -------------- | -------- | -------- | -------- | -------- | ---- | -------- | -------- |
| Successful (%) | 37       | 41       | 36       | 36       | 36   | 33       | 31       |
| Challenged (%) | 46       | 40       | 47       | 45       | 47   | 48       | 50       |
| Failed (%)     | 17       | 19       | 17       | 19       | 17   | 19       | 19       |
Successful = Project on time, on budget, delivered with satisfactory result.
Challenged = Project is late, over budget, delivered with unsatisfactory result.
Failed = Project is cancelled, not completed, and never used.

About a 1/3 of IT systems actually meet the requirements planned out during the analysis and design phase. Flyvberg and Budzier state that large enterprise projects overrun costs by about 27%.

Designing and developing IT systems are expensive, high-risk, and have serious consequences if failed in particular, a system that is a little late or a bit pricey is salvageable. It's important to get these things right.

**But what does success actually mean?**
***
## 1.4.1. What is a Successful System?:

A [[../Glossary#^SucSys-def|Successful System]] has multiple facets to be discussed. 

1. Requirements have to be identified accurately and translated into development blocks.
	1. These then need to be measured to check performance.
2. It's often assumed that people know and agree upon a development plan that includes **accurate** timescales and costs.
3. What constitutes a system as being operational, when can we be certain that it's been achieved, when everyone is happy?

There is two camps - one camp cares about the project being successful another can care about the actual project/product being quality. So a project can succeed but fail because the product is poor and a badly manged project can fail but succeed because the underlying product is worthwhile.

Usually, a well managed product AND a high quality product lead to success.

The definition becomes quite murky when you consider the: *project team being happy and users being happy with the result.* - It's hard to measure this, who's opinion do you value more dev/users, etc.

Then maintaining a project is a another beast, how often do you change or update things, who has ownership of it, etc.

### Using Failure as a Mirror of Success:

If we view avoiding system failure, as a success, then we can gain another perspective into success. Often failure is defined as: "*Something that has gone wrong, or not lived up to expectations.*"

Various types of failure can be identified:
- Objectives not being met
	- If objectives are not met, then the project sinks and its abandoned.
- Undesirable side-effects
	- If the side-effects are poor, then the project can be solid, but the outcomes can be deemed as too much. e.g. the System does more harm than good. Generates less profit than it takes.
- Incorrect objectives being set for the system.
	- If the original problems weren't defined by the founders well, then the project will sink, since it was a poor blueprint to begin with.

The 6 most key factors that businesses/people/managers take into account with IT systems are:

1. Meeting user requirements
2. Achieving purpose
3. Meets timescale
4. Meets budget
5. Happy users
6. Meets quality.

Often different job roles and stakeholders have different perspectives on a project. Which can make miscommunications or problems happen.

***

## 1.4.2. Modelling System Success:

The most widely used IT systems modelling is the **Information Systems Success Model** by DeLone and Mclean. It is one of the most important modelling techniques in the industry.

![[../../../../03_Reference/Pictures/Information_systems_success_model.png]]


### 1. Information Quality:

**Definition:** The extent to which the output information from an information system fulfils the requirements and expectations of its users, emphasizing the semantic aspects of the information generated by the system.

**Key Quality Dimensions:**
- **Accuracy** - Information is free from errors
- **Relevance** - Aligns with user tasks and needs
- **Timeliness** - Available when needed
- **Completeness** - Covers all necessary elements without omissions
- **Conciseness** - Presented without redundancy
- **Understandability** - Easy to comprehend
- **Consistency** - Uniform and coherent across outputs
- **Currency** - Up-to-date information

> Is the system reliable, does it service the user well?

### 2. System Quality

**Definition:** The desirable characteristics of the IS itself, focusing on technical performance, usability, and reliability. Concerned with whether or not there are "bugs" in the system, the consistency of the user interface, ease of use, and response times.

**Key Quality Dimensions:**
- **Ease of Use** - User-friendly interface and operation
- **Reliability** - Consistent and dependable performance
- **Flexibility** - Adaptability to changing needs
- **Response Time** - Speed of system operations
- **Functionality** - Features and capabilities available
- **Efficiency** - Resource optimization
- **Integration** - Works well with other systems
- **Data Accuracy** - Technical precision of system operations
- **Availability** - System uptime and accessibility

> At a technical level, is the system programmed and built well?
### 3. Service Quality

**Definition:** The quality of the service or support that system users receive from the IS organization and IT support personnel. Added to the updated 2003 model to reflect the importance of service and support.

**Key Quality Dimensions (SERVQUAL framework):**
- **Reliability** - Ability to perform the promised service dependably and accurately
- **Responsiveness** - Willingness to help customers and provide fast service
- **Assurance** - Knowledge and courtesy of employees and their ability to inspire confidence
- **Empathy** - Caring, individualized attention provided to users
- **Tangibility** - Appearance of physical facilities, equipment, personnel, and communication materials

> Are people or users supported and onboarded to use the system well?
### 4. Usage Intentions / System Use

**Definition:** "Intention to Use" is the user's belief about their likelihood to use the IS (an attitude), while "Use" is the actual consumption of an IS or its output in terms of actual or self-reported usage (a behaviour).

**Key Measurement Dimensions:**
- **Frequency of Use** - How often the system is accessed
- **Duration** - Connect time or length of sessions
- **Number of Functions Used** - Breadth of system features utilized
- **Intensity** - The quality and intensity of use (informed vs. ill-informed usage)
- **Voluntary vs. Mandatory Context** - Whether usage is required or optional affects interpretation
- **Actual Usage Patterns** - Real behavioural consumption of the system

**Note:** DeLone and McLean proposed "intention to use" as a viable alternative measure to "use" given the challenges in understanding the multi-dimensional nature of usage in certain contexts.


> Do people want to use the system? Are they using the system?

### 5. User Satisfaction

**Definition:** The emotional dimension of IS interaction, capturing users' degree of contentment with the information system after deployment, emphasizing affective responses that behavioural metrics may not capture.

**Key Measurement Dimensions:**
- **Overall Satisfaction** - General contentment with the system
- **Content Satisfaction** - Satisfaction with information provided
- **Format Satisfaction** - Satisfaction with presentation
- **Accuracy Satisfaction** - Confidence in system outputs
- **Ease of Use Satisfaction** - Satisfaction with usability
- **Timeliness Satisfaction** - Satisfaction with system responsiveness

**Common Instrument:** End-User Computing Satisfaction (EUCS) scale by Doll and Torkzadeh, which assesses five key components through 12 items rated on Likert scales.

> Are people happy with the current deployment of the system?
### 6. Net System Benefits

**Definition:** The positive outcomes resulting from IS use and user satisfaction, collapsing the original "Individual Impact" and "Organizational Impact" dimensions into a more parsimonious construct. The level of analysis must be specified - whether benefits are measured from the individual's, employer's, industry's, or nation's perspective.

**Key Measurement Dimensions:**

**Individual Level:**
- **Task Productivity** - Efficiency in completing work
- **Task Innovation** - Enhanced creativity in work
- **Decision-Making Performance** - Quality of decisions
- **Job Effectiveness** - Overall work performance
- **Individual Sense of Accomplishment**

**Organizational Level:**
- **Cost Reduction** - Decreased operational expenses
- **Revenue Growth** - Increased income
- **Time Savings** - Efficiency gains
- **Market Share** - Competitive advantage
- **Customer Satisfaction** - External impact

**Note:** Net benefits create a feedback loop - if benefits are positive from the sponsor's perspective, they influence and reinforce future usage intentions and satisfaction.

> Do the key stakeholders within the system benefit from it?

***
# 1.5. Stakeholders in Systems Success:

It is important to distinct the individual users and the shareholders, but what is meant by the term of **users?** Anyone can "use" an eCommerce platform, but not buy anything and leave because of site issues for instance.

This is why the term [[../Glossary#^Stakeholder-def|Stakeholders]] are often used. We can analyse stakeholders in three main ways:

1. Identifying who the stakeholders are.
2. Understanding and prioritising key stakeholders
3. Managing stakeholders.

***
## 1.5.1 Stakeholder Analysis:

To start to identify stakeholders, what is frequently done, is brainstorming. It's a simple approach to exchange and generate new ideas, a few guidelines are often good to follow to ensure that the brainstorming is productive and helpful.

- Work in small close groups of 5-6 in private and protected areas away from any interruptions.
- Create a safe, supportive, encouraging, building, fun, playful, energetic, enthusiastic, stimulating, and risk taking approach.
	- Depends on getting a good mix of people and environmental and organisational culture.
- Divide time into periods of relaxed privacy and rapid-fire group discussion.
- Write up all the ideas when they occur, so everyone can see them.
- Treat everyone as useful and equal, enable everyone to contribute, although having someone who can keep peace and pace is ideal.
	- Not every individual will be equal here, some people WILL have a better understanding of the system to be made or what to do - other will assert that they have a better understanding because of their title or position as well, so it can be difficult here.
- Continue whilst the excitement lasts, but stop at staleness or tiredness.
- When a good stock of ideas have been produced, be more controlled and look for ideas that overlap - condense down and form groupings.

My own perspective - The Top 3:
1. Making sure people are able to speak their mind and are safe and protected to do so, is the essence of brainstorming, ensure this above all.
2. Stop when people start to get tired, don't associate brainstorming with being painful or boring.
3. Be careful not to undermine certain people or their ideas, especially when condensing down, don't favour one over the other, but group similar ideas in a blob or class together.

In practice, good brainstorming is very tough, due to negativity and existing hierarchies. Self-discipline, understanding, and patience. 

**Brainwriting** can be advantageous, putting results into a hat or on a virtual wiki, so people can post ideas in their own time and work remotely as well as, sidestepping some issues of brainstorming.
## Identifying Stakeholders:

To identify stakeholders, it can be valuable to ask the following questions:

- Who is affected positively or negatively by the project to build the system?
- Who will gain from the system and who will lose from it across a range of material, financial, status, power, influence?
- Who might want the system to succeed and who might want it to fail?
- Who has the power to cause the project to succeed or fail?
- Who controls or provides the resources and facilities needed? What will be needed?
- Who are the key suppliers you will need to buy from?
- Who has the talent to make a project succeed?
- Who are the leaders in positive and negative thoughts?
- Who exercises influence over shareholders?
- Who are the less obvious shareholders who haven't been considered?

For example:



### Understanding and Prioritising Key Stakeholders

### Managing Stakeholders:


***

# 1.6. Power and Success in IT Systems:

***
## 1.6.1 Politics and Rationality:

***

## 1.6.2. The Causes and Value of Conflict:

***

## 1.6.3. The Politics of Stakeholder Identification:

***

## 1.6.4 Stakeholder Legitimacy and Conflict:

***

## 1.6.5 Expert Stakeholder Power:

***

## 1.6.6. Stakeholder Power Relations and System Success:

***

# 1.7. Summary:





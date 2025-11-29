---
date created: Tuesday, November 25th 2025, 11:14:25 am
date modified: Saturday, November 29th 2025, 10:41:26 am
---

# 2. Introduction:

Two things within IT systems are immutable. 

1. Systems failures will always occur
2. Many system failures that do occur, are avoidable.

Mainly, research points to the fact that same problems occur time and time again, this can be written down to the inability to look/learn from mistakes. Sociotechnical systems thinking enables us to learn from mistakes we wouldn't otherwise consider, e.g. Perspectives of users, leaders, commissioners, etc.

We then are able to deduce why a failure occurred, this means of learning approach is called the [[../Glossary#^SFA-def|Systems Failures Approach]]. Jung states this within psychology too:

> *The psychotherapist learns little or nothing from his successes. They mainly confirm him in his mistakes, whilst his failures are priceless experiences that open up a deeper way to the truth, but force him to change his views and methods.* - **C. Jung 2001**

Expanding upon this, we can learn from the mistakes of others by looking at case studies. Analysing, Reflecting, and generating insight.

***
# 2.1 The Systems Failure Approach - Overview:

The stages of a Systems Failure Approach can be depicted as the following:

![[../../../../03_Reference/Pictures/SFA-model.png]]

***

# 2.2 The Failures Analysis Cycle and the Pre-analysis Stage:

There are a few forms of diagramming, that can be used in the pre-analysis approach. The four key ones being:

1. Rich Pictures
2. Spray Diagrams
3. Relationship Diagrams
4. Multiple Cause Diagrams

Being able to structure, reason, and understand these diagrams will be critical for systems design and EMAs/TMAs.

### Case Study - Post Office Horizon Failure:

*The Horizon accounting system that was used by postmasters who operate Post Office services and other features was a large failure. It was introduced in 1999 and led to 100s of Postmasters and Sub-postmasters being prosecuted for fraud/theft. Often being treated very harshly by the Post Office investigators and senior management.*

*This was a huge case, where the Post Office pursued sub-postmaster and asserted that their system couldn't be wrong, when they actually concealed evidence of any wrongdoing and mounting evidence.*

*It's one of the biggest misjustices in the history of UK systems. Whilst most public accounts focus on the people, it's a great case study into IT system failures.*

*The Horizon system, produced by Fujitsu, had bugs within the system. Where SPMs noted that false reporting of shortfalls of multiple thousands of pounds where located within a system. Many people paid their own money into the system as their contract stipulated so. Today the system is still used and is **robust**.*

*Out of 700 prosecutions, only 93 have been overturned.* 

*Compensation from the **Group Litigation Order** (GLO) offered to repay legal fees, then a £75k bonus for wrongdoing. The **Overturned Convictions Scheme** allows those who were falsely convicted to gain a settlement fee of £600k with an upfront fee of £163k whilst money is processed. The **Horizon Shortfall Scheme** is for postmasters who weren't directly convicted by experience shortfalls and will have their case reviewed.*

*Nobody has ever been held accountable. An CBE was stripped, but there hasn't been any legal action taken upon the Post Office or Leadership.*

*The Fujitsu Horizon software was not robust during the first decade of operation. Bugs, errors, and defects posed a risk.*

*A big problem was the lack of proper documentation of the system. For instance: Improper error checking an API calls, Lack of design documents, access to source code. Many key components weren't delivered or had scope aggressively slashed.*
## 2.2.1 Rich Pictures:

Rich pictures were developed as a part of the **Soft Systems Methodology**. They are used to gather information about complex situations and present them clearly using a combination of drawings, pictures, symbols and text that represent a situation or issue from the viewpoint of the person that drew them.

They can show relationships, connections, influences, causes and effects. [[Conventions/Rich Pictures|Rich Pictures]] are summaries in the form of a picture to highlight the aspects of a system, which parts should be regarded as structure and which process.

## 2.2.2 Spray Diagrams:

[[Conventions/Spray Diagrams|Spray Diagrams]] show the connections between elements or concepts that are associated with a particular issue. They are similar to mind maps and are often employed even outside of IT systems.

- Exploring an issue from scratch
- Helping organise facts, issues or ideas into a structured form
- Taking notes
- Setting out the structure of the argument.

Spray diagrams work well in that they enable you to clarify your own understanding. Sprays can be used as a tool to visualise your understanding of a situation.

## 2.2.3 Relationship Diagrams:

[[Conventions/Influence Diagrams|Influence Diagrams]] are used to display the connections between related components and concepts, they help understand how a the elements or actors within a situation acted with each other. This is sometimes referred to as a **concept map.**

They don't have a central topic and are often quite complex.
## 2.2.4 Multiple Cause Diagrams:

[[Conventions/Multiple-Cause Diagrams|Multiple-Cause Diagrams]] as covered in block one are also key, if it's being written about in multiple blocks, it's likely important.
## 2.2.5 Summary:

The **pre-analysis stage** of the failures analysis cycle is very important and has different models for us to figure out the following details:

1. Define what the point of the analysis is and the viewpoints and perspectives from which it is being conducted.
2. Gather initial information and source material, examining from different viewpoints that are identified as important.
3. Organise the information into forms that will be usable and easy to digest.

In essence, modelling is about converting heavy, textual, reports into a form which is light and visual, so that either yourself or other people who you are working with can understand a topic/system/idea more.

Expanding from this, if you follow modelling conventions, there is no "wrong" way to build a model since it's mainly about your own perspective from the information you have, they won't be fully bias free, but they still can be factual and helpful.
***

# 2.3. Identification of Significant Failures and Modelling Systems:

The next phase of the Systems Failure Approach has two parts: The identification of a significant failure, then describing it as a system through various mediums. (Report, diagrams, system's thinking). 

Simply:
1. What went wrong?
2. Show how it went wrong.

In other words the: **Identification of failures**, **Selecting Systems** and **Modelling Systems.**
### Activity - CAPSA case Study:


The three distinct phases were:
1. The initial leadership and management who proposed the project.
	1. They had to look at and figure out the requirements that were needed for a new system to be made, and what the best approach would be to deliver a solution.
2. The implementation of the system phase
	1. Developers and managers had to work on the system and get it running.
3. The late development/release
	1. After a problem was admitted, consultants were brought in and the system with shipped.

Within the CAPSA case, The main failures were:
1. The need to deliver an accountancy system quickly, this lead to a poor product as staff or developers had to make software in poor conditions.
	1. This could be exacerbated by a lack of skills, training, or funding.
2. A lack of product/project ownership. Various executives such as the VC, Treasurer did not know who was actually in charge of the project.
3. There was a big delay and a scope cut, in which Oracle consultants had to come in and fix the system.
	1. But user feedback was negative and the costs were too high.

## 2.3.1. Input-output Diagrams:

Input-output diagrams are used to define and determine the inputs and outputs from either a physical process (Baking a pie), or an abstract process (Company hierarchy). They are a simple diagram, but require careful thought to not become confused with details.

The structure of an [[Conventions/Input-Output Diagram|Input-Output Diagram]].

This diagram is best used in the analysis of significant failures phase of the Systems Failure Approach (SFA). This is because it's good at scoping out projects, figuring out requirements, or identifying resource needs. Additionally, it's easy for any stakeholders to clearly see what the picture is.
## 2.3.2. Systems Maps:

Systems Maps, as shown within [[Part 1 - Successful IT Systems#Systems Maps|Block 1]]. Can be further enhanced by considering the following ideas:

1. Make sure that it's obvious what the system boundary is, emphasis it using a thicker line, or colour.
	1. You can use a dashed/dotted line when the boundary is somewhat unclear or tentative.
2. Consistency between components is a must, ensure that the system isn't being represented as properties.
3. Making certain elements larger or smaller can signify how valuable they are. Generally use a uniform style.
4. Place similar components close to each other.
5. Always have a little more space than you need.
## 2.3.3. Influence Diagrams:

[[Conventions/Influence Diagrams|Influence Diagrams]] as also shown within [[Part 1 - Successful IT Systems#Influence Diagrams|Block 1]]. Can be further enhanced by considering the following:

1. Avoid arrows from the features in the environment to the system boundary. As implicitly, the environmental factors effect the system.
	1. You can have them, but ensure that they terminate at a certain component, or if it's key to show a relationship.
2. Different thickness of lines can indicate strength of influence
3. If you want to show different types of influence, use a key and use colours or dashing to indicate this. Only do so if the factors aren't obvious.
4. Don't overload the diagram with information, keep it clean and readable.
5. Use spacing to indicate the closeness of relationships, you can also use thicker or thinner lines to highlight important or weak remote relationships.

## 2.3.4 Summary:

To summarise each section:
- *Identify Significant Failures:* Situations will already be labelled as failures or successes, but after analysing and looking at a system, you can further determine the exact specifics of the outcome.
- *Selecting Systems:* You can use trial boundaries to structure different aspects of the situation into a range of different systems, then pick the one that suits needs the most to be carried forward.
	- This means that the analysis of the significant failures is what will be brought forward to build a better a system.
- *Modelling the Systems:*
	- Clarify the nature of the new system, build models of it and represent the outer environment, possibly consider different perspectives and levels. Figure out how the wider system will sit in the big picture.

***

# 2.4. The Formal Systems Model:

This section deals with the **Comparison** and **Synthesis** stage of the SFA (System Failure Approach). Another model called the [[Conventions/Formal System Model|Formal System Model]] is used to contrast the SFA system.

The Formal Systems Model consists of a decision making sub-system that describes the transformations that need to happen to reach a goal, what resources are needed, what are the expectations of other sub-systems and components and what performance is expected through a **performance sub-system.**

The performance monitoring sub-system that observes the transformation process and reports results and deviations from the target expectations. Then corrective actions can take place, to ensure that the main subsystem can be corrected.

Other sub-systems will be designed to complete the tasks of the system and transformations of inputs into outputs.

Generally this represents the next level up from the system into being integrated in reality. It defines the following:

- The purpose and objectives of a system
- Influences decision makers
- Monitors performance
- Provides resources for the system to function.

This disturbs and shakes up the current systems in place, the wider system (e.g. company) will influence this stage and the in development system will influence the wider system.

The FSM and the actual systems in place will often differ between the following areas:
- Environment-wider systems
- Environment-system
- Wider system-system
- Interfaces between sub-systems.

***
# 2.5. Summary and Lessons for the Future:

So far, we've been looking at post-mortems of failed systems. But now we can develop approaches to preventing and mediating failures.
## 2.5.1. Preventing Failure:

There are two main approaches to preventing system failures:

1. Generate lessons from past failures that stop same/common mistakes from occurring again.
2. Compare a perfect or ideal system to the current plan, and look for holes or weaknesses.
	1. Comparing the FSM to actual system. Figure out what sub-systems, components need to function for the system needs/requirements to be met.
## 2.5.2. Learning Lessons from past Failures:

One technique we can use to learn from the past is: looking at previous attempts on how to build and modify systems and build an understanding of what has worked well and what hasn't. There is usually lots of data and research that need to go into this, but you can generate highly useful lessons that save lots of money and resources.

A shortcut we can use is to concentrate on the most common causes and prevent those, or the easiest causes to prevent. It's not ideal, but can work well at identifying and sorting errors in the moment, whilst further analysis is done, planned, or perhaps sadly of all forgotten.

Reoccurring themes that emerge when comparing an FSM/Perfect system to reality:
- There can be a lack of structure within the system. There may not be sufficient performance measuring, or a control/decision making sub-system.
	- **Solution:** Clearly define the point and purpose of all sub-systems, then build them with in mind the needs of the wider system and the system itself.
- No clear statements of purpose or goals are given to the system from the wider system or the communication is murky.
	- **Solution:** Keep ongoing communication with the wider system, get clear direction and goals from the wider system and people, have it in writing and confirm multiple times.
- Poor performance in one or more sub-systems, performance measuring may exist but be faulty or inadequate.
	- **Solution:** Consider devoting more resources of development time into fixing these issues. This is an execution, resource, or skills problem typically.
- Inadequate design of one or more sub-systems.
	- **Solution:** Look at the chunks of the system that work well, and the other aspects that are inadequate and modify the system as appropriate. YOU MUST UPDATE INTERNAL DOCUMENTATION OF THIS.
- Not enough consideration given to environmental factors, not enough resources to cope with the changing environment.
	- **Solution:** This is an organisational or a risk management issue. Having more resources in the tank, or planning for delays or issues to give buffer time is valuable in this case.
- Imbalances in resource allocation that lead to quality problems, cost, output, or delays.
	- **Solution:** Listening to expert stakeholders and giving out appropriate resources for the systems or designs in place is key. Management of resources within the wider system is key to ensure that a project/system has enough resources to actual push through.
## 2.5.3 Modelling the Future:

In modelling the future, you often look at the past and what has happened previously. You think about what will likely exist down the line and position accordingly. For example:

- What will then environment do or change over time?
- How can our system or wider system influence the environment in a favourable way?
- What will disturb out system that's out in the environment?

You can build formal models at different *levels* to determine this:
- Highest level - The architecture of the system
	- The main architecture and idea of the system.
- Middle level - The sub-systems of the system
	- Interfaces between the system and users
- Lower level - The sub-sub-system level
	- Hardware needed to run the system.
	- The performance monitoring sub-system.
## 2.5.4 Where Next?:

Next evaluating concepts such as: Complexity, Emergence, Adaptation, and Co-evolution and how these can be applied to IT systems to enhance chances of success.

***











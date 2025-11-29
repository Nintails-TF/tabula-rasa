---
date created: Thursday, November 27th 2025, 4:09:41 pm
date modified: Thursday, November 27th 2025, 4:17:39 pm
Parent Link:
  - "[[../Part 2 - Learning from Failure#2.4. The Formal Systems Model|Formal Systems Model]]"
---

# Purpose:

The FSM model works in the Comparison and Synthesis stages of the Systems Failure Approach. It serves as an idealized reference model to contrast against actual systems, helping identify gaps and inform the design of improved systems. It models how a system should function rationally and the relationships between its components.

# Elements:

**1. Decision-Making Sub-system**
- Determines what transformations are needed to achieve system goals
- Identifies required resources
- Sets expectations for other sub-systems and components
- Defines target performance levels

**2. Performance Monitoring Sub-system**
- Observes the transformation process in real-time
- Reports results and measures outcomes
- Identifies deviations from expected performance
- Triggers corrective actions when needed

**3. Transformation Sub-systems**
- Execute the actual work of converting inputs into outputs
- Carry out the tasks necessary to achieve system objectives

**4. Wider System Context**
- The environment in which the system operates
- Influences decision-making and provides resources
- Is influenced by the system's outputs and operation

# Conventions:
- Show clear boundaries between sub-systems
- Indicate feedback loops between performance monitoring and decision-making
- Represent the transformation process centrally
- Show the wider system/environment as the context
- Use arrows to indicate information flow and influence
- Distinguish between monitoring information and operational processes

# Guidelines:
1. **Define objectives clearly** - Start by establishing what the system is meant to achieve
2. **Identify all sub-systems** - Ensure decision-making, monitoring, and transformation components are all represented
3. **Show feedback mechanisms** - Performance monitoring must feed back to decision-making
4. **Consider the wider context** - Don't isolate the system from its environment
5. **Look for mismatches** - Compare the FSM to actual systems to find discrepancies in:
    - Environment-wider systems relationships
    - Environment-system interactions
    - Wider system-system connections
    - Interfaces between sub-systems

# Example:

**Hospital Patient Records System (FSM)**

_Decision-Making Sub-system:_
- Hospital management determines need for accurate, timely patient records
- Sets objectives: 99.9% uptime, <2 second retrieval times
- Allocates budget, staff, and technology resources

_Transformation Sub-system:_
- Medical staff input patient data
- System processes and stores information
- Outputs: accessible patient records for authorized personnel

_Performance Monitoring Sub-system:_
- Tracks system uptime and response times
- Monitors data entry errors and completion rates
- Reports monthly to decision-makers
- Triggers alerts when performance drops below thresholds

_Wider System:_
- NHS regulations and data protection laws
- Integration with other hospital systems (pharmacy, labs)
- Patient expectations for privacy and care quality

_Comparison to Actual System might reveal:_
- Decision-makers aren't receiving timely performance reports
- No corrective action mechanism when errors are detected
- Insufficient resources allocated for system maintenance
- Poor integration with the wider hospital ecosystem

This comparison helps identify where the actual system falls short of the rational ideal, guiding improvements.
![[../../../../../03_Reference/Pictures/Pasted image 20251127161007.png]]
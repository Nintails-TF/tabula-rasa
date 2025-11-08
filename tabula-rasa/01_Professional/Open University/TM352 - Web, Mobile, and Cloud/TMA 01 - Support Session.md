---
date created: Saturday, November 8th 2025, 10:18:55 am
date modified: Saturday, November 8th 2025, 11:57:05 am
---

# TMA 01 - Support Session:

## Introduction:
- Look at the coding session to get a grasp of what to do within the program code.
- Look at the TMA 01
	- Build a front-end prototype.
	- Framework comparison
	- Development report
	- Self evaluation
- After you've done a piece of practical work, work on the TMA, since it's fresh in your mind.

In reality, the ability to read code and understand how it works, can be more important that just writing raw code. Figure out how things work before you try to fix or change anything.

Stay 85% within the word count. Use Harvard CTR, be authoritative and confident. 

## Overview:

![[../../../03_Reference/Pictures/TM352-overview.png]]

**Block 1:**
Web development with common frameworks. Like Svelte and React. Web-markup, architectures, web services, accessibility, and security issues.

Fundamental concepts and tech choices, limited in depth and detail. Reading documentation, such as MDN or RFC to gain extra detail or reference to support reports and documents.

**Block 2:**
Figure out how to adapt webpages and such for mobile devices that have a much smaller screen size.

**Block 3:**
Learn about cloud technologies, explain advantages and disadvantages of cloud - break apart the marketing lingo.

***

# TMA 01:

## Question 1:

Q1: Build an app that passes automated tests, both using Svelte and React. Once you learn one language, you can speak in other languages. *If you can drive a car, you can drive a truck.*

Figure out how the skeleton code provided works.

**Requirements:**
- Fetch the current three tickets categories from the API.
- Show three categories to user.
- Let user choose category from list.
	- You can present this in anyway. Feedback to the user is important - show their selection if it was successful or not.
- Send selected category to server via API.
- Show user their selection was successful.

Submission checker will be used to test the application. You want to use the tests to check if you code meets requirements. Each test is worth a mark. If you fail tests, denote where you went wrong.

Generally, don't setup the tech locally, the open compute lab, is where the markers are going to test the front-end application. The open compute lab is a cloud instance that the OU uses.

To copy, use Linux commands. Swagger is used to document the API. Do not use the local deployment.

Dots mean it passes, and F means it fails, this can take up to ten minutes. **You can deliberately fail all tests, to get feedback then to work backwards from them.**
## Question 2:

Q2: Compare the advantages and disadvantages of each.

You need to adapt a technical report that compares two frameworks to make it suitable for a non-technical audience. You don't need to make a recommendation, but you do want to use citations and references.

Mention every point in the original. Work up until the word limit (700-750 words ideal), explain the module to the new student.

Using diagrams can be helpful, they don't count towards the word count, unless they contain lots of text.

## Question 3:

Q3: Write a report. How did you complete Question 1 - read this before question 1!

Explain what framework you used first and why? Explain which framework you preferred and why?

Consider which framework was easier and why? Use language that is suitable for a TM352 student, don't answer in the first person. Use formal and distinct 3rd person language. I.e. What would a typical student understand.

Link it to the scenario, include citations, and provide the world count.

## Questions 4:

Q4: Self-evaluation.

Write in the first person (175-200 words ideal). What did you find most challenging and why? How did you decide what to include/exclude in question 2. You don't lose marks by finding things hard.

Don't quote the course content, write it in your own words. You can use Turnitin to evaluate.

For submission, zip up the report and code together:
```Bash
tm352 tma01 test tma01-J6308626-q1.zip
```

***
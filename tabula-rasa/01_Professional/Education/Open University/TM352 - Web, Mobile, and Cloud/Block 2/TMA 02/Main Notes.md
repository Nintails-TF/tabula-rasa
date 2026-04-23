---
date created: Thursday, February 5th 2026, 2:31:47 pm
date modified: Thursday, February 5th 2026, 2:55:44 pm
---

# Scenario:

The Roman town of Isca Augusta consists of the fortress of the II Augusta Legion, the public baths, the amphitheatre and the surrounding civilian settlement. The legion has recently embarked on a digitisation drive and outsourced the development of a number of web and mobile applications. Your next assignment in the IAMC team is to design and build a mobile-app-based ticketing application, which will be used by the inhabitants of Isca Augusta to pay for access to the amphitheatre. Unfortunately, the outsourcing company contracted to do the work has ceased to trade and the IAMC have assigned you to undertake some of the outstanding work.

The TMA consists of three main parts:
- Question 1: A practical task to continue to develop a prototype application.
- Question 2: A report task to evaluate the use of React Native libraries to support the application.
- Question 3: A report task evaluating the use of mobile devices.

Additionally, you are expected to provide:
- Question 4: A short report assessing your own learning experience

# Question 1:

Build a Reactive Native App that passes the tests.

# Question 2:

Use a library that shows a QR code, pick two of them and figure out the strengths and weaknesses of both.

## Initial Draft:


When picking QR code, I decided to go with the react-fancy-qrcode for a few reasons:
1. It was recommended in the testing suite as a potential option
2. `react-fancy-qrcode` has lower dependencies, peer dependencies, and development dependencies than the `react-native-qrcode-svg`
	1. Dependencies 2 VS 3
	2. Peer Dependencies 1 VS 3
	3. Development Dependencies 5 VS 10
3. This means that there is fewer setup and configuration which needs to be done, it also ensures that the build process is simpler and has less future version conflicts.
4. It is also smaller (38.56kB VS 958.34kB), this results in a smaller bundle size and less code to maintain or worry about.
	1. This is particularly beneficial if the application scales to handle more features.


## Step 1:

Write a first draft of a report that evaluates the **strengths and weaknesses of at least two React Native libraries** that you have identified and which could be used to complete the coding project.

This report requires:
- an introduction which lists the libraries you will compare
- a discussion that compares the libraries, supported by in-text citations and references
- a conclusion which identifies the recommended library.

You should recommend the library you decide to use in Question 1.

Among other things you could consider is whether the library is well supported, whether it is current, whether other users report issues with it, if it provides appropriate features, and if there is appropriate documentation.
## Step 2

Post your draft report to the ‘TMA 02 – My Report’
## Step 3

Look at the draft reports uploaded by other students. Identify two other proposals that have less than two pieces of feedback and give them constructive feedback on their report. You should base your feedback on the mark scheme provided below. In particular highlight any discussion that you feel is not sufficiently linked to the scenario. Your aim is to help the other students maximise their marks.

## Step 4

Read the feedback made by fellow students on your own report, their reports and other feedback. Then introduce any changes you wish to your report based on what you have read and submit as your report in the solution document.

## Marking Scheme:

| **Marking Aspect** | **Marks** | **Description / Application to Scenario**                                        |
| ------------------ | --------- | -------------------------------------------------------------------------------- |
| **Application**    | 0–2       | Basic or no application to the scenario/practical work.                          |
|                    | 3–7       | Applied to aspects mentioned in the TMA/resources with some detail on relevance. |
|                    | 8–14      | Deep application beyond provided resources with full justification of relevance. |
| **Coverage**       | 0–4       | Based on how much of the required content is addressed.                          |
| **Detail**         | 0–1       | No or very limited detail provided.                                              |
|                    | 2         | Some parts of the answer are detailed.                                           |
|                    | 3–4       | Most of the answer is detailed.                                                  |
| **Language**       | 0–1       | Language is not at the appropriate academic/technical level.                     |
|                    | 2         | Some language is used at the appropriate level.                                  |
|                    | 3–4       | Most or all language used is at the appropriate level.                           |
| **Citations**      | 1 (max 4) | Per relevant in-text citation and reference that supports the argument.          |
# Question 3:

## Step 1:

Write a technical report considering the implications of mobile device use for the IAMC. The focus is on your comparative experience of building all three prototypes: Svelte, React and React Native, for this scenario and not on the general technical aspects. 

You are required to address the following two questions:
1. What changes would be needed to your prototype in TMA 01 to take advantage of mobile devices?
2. What are the benefits and risks of a mobile web approach, verses a mobile app approach?
    
To answer these questions, you will need to complete the following steps:

Step 1: Use generative AI interactively or via the three example Co-pilot prompts, provided in the TMA 02 Section on the [Assessment](https://learn2.open.ac.uk/mod/oucontent/olink.php?id=2549636&targetdoc=Assessment)  page, to outline an answer to the question set.
Step 2: Check the AI output and identify supporting references.
Step 3: Write your final report that links to the specifics of the scenario.

## Step 2

Chat GPT has been reported to be a bullshit generator (Hicks, Humphries, and Slater, 2024). Your next task is therefore to verify the output of the Generative AI and provide in-text citations and references to support your argument. You **must** verify links and references provided by the AI, as well as to check the content of the discussion against the module materials and other sources on the internet.

Include an appendix with your prompts and responses as per the best practice described in the Open University guidance linked to in Step 1.

## Step 3

Write your final answer using information taken from the AI responses and your own research. Link your argument to the specifics of the scenario and your work in TMA 01 Question 1 or TMA 02 Question 1.

# Question 4:

## Step 1

In your self-evaluation, you must answer the following two questions:

- a. Which parts of the Block 2 learning did you find most challenging and why?
- b. Compare and contrast the effectiveness of using OpenStudio for feedback from your peers in Question 2 versus using an AI assistant in Question 3.

## Step 2

Post your answer to Step 1b in OpenStudio in the Final Reflection slot and include your answers to both Steps 1a and b in your solution document.

Your tutor will mark the version in the solution document, the version in OpenStudio will allow you to compare your experience with that of other students.

|**Marking Aspect**|**Marks**|**Description**|
|---|---|---|
|**Coverage**|0–4|Awarded based on how much of the required content is covered.|
|**Detail**|0–6|Awarded based on the level of depth and detail provided in the text.|

---
date created: Friday, November 14th 2025, 2:47:21 pm
date modified: Friday, November 14th 2025, 2:51:20 pm
---

# Problem Statement:

You need to build a web-based ticketing prototype for the Isca Augusta public baths in both React and Svelte frameworks, compare them, and write reports about your experience.

## Main Checklist

### **Part 1: Practical Development (Question 1) - 30 marks**

#### Setup Steps:

1. **Get the skeleton files** either from:
    - Download `tma01-resources.zip` from Assessment page, OR
    - Find in VCE at `block_1/skeletons/tma01`
2. **Set up environment:**
    - Copy `block_1/skeletons/tma01` to `block_1/tma01`
    - Install dependencies in all 3 folders with `npm ci`:
        - `svelte-frontend`
        - `react-frontend`
        - `api`
3. **Start development:**
    - Terminal 1: Start API server (`npm run dev` in api folder)
    - Terminal 2: Start frontend dev server (`npm run dev` in svelte or react folder)
    - Copy API URL into `serverBaseUrl` variable in App files

#### Required Features (implement in BOTH frameworks):
- [ ] Fetch 3 ticket categories from API (`GET /api/categories`)
- [ ] Display categories to user as buttons
- [ ] Let user select a category
- [ ] Send selection to API (`POST /api/pay/{id}/{cardno}`)
- [ ] Show success message

#### Exact UI Requirements:
- [ ] H1 heading: "Isca Augusta Public Baths"
- [ ] H2 heading: "Ticket category"
- [ ] 3 buttons with format: "{title} {price}"
- [ ] After selection, hide unselected buttons
- [ ] Show H2 "Payment"
- [ ] Input field labelled "Card number"
- [ ] Input field labelled "Validation"
- [ ] "Pay now" button (initially disabled)
- [ ] Validate: 8-digit card number, sum equals validation field
- [ ] Show appropriate error/success messages
- [ ] Final message: "You have paid for access for one {title}."

#### Testing:
- [ ] Run `npm run assess` in each frontend folder
- [ ] All tests must pass for full marks

### **Part 2: Framework Comparison Report (Question 2) - 30 marks**

**Word limit: 750 words**
- [ ] Adapt the provided Box 1 text
- [ ] Make it scenario-specific (relate to Isca Augusta)
- [ ] Adjust language to TM352 teaching level
- [ ] Add in-text citations for provided sources
- [ ] Include reference list (Cite Them Right Harvard format)

### **Part 3: Development Experience Report (Question 3) - 30 marks**

**Word limit: 750 words**

Answer these questions:
- [ ] Which framework did you work on first and why?
- [ ] Which framework would you prefer and why?
- [ ] Apply all arguments to the scenario and your practical work
- [ ] Include citations and references

### **Part 4: Self-Evaluation (Question 4) - 10 marks**

**Word limit: 200 words**

Answer:
- [ ] What parts of Block 1 were most challenging and why?
- [ ] How did you decide what to include/exclude in Question 2?

## Submission Requirements

### For VCE Users:

```bash
$ tm352 tma01 submit YOUR_STUDENT_PI
```

### For Local Development:

1. Delete all `node_modules` folders
2. Compress as `tma01-YOUR_STUDENT_PI-q1.zip`

### Final Submission:

- [ ] Create `TMA01.zip` containing:
    - Written report (.doc/.docx/.rtf) with Questions 2, 3, 4
    - Practical application zip file
- [ ] Include on title page:
    - Your name
    - Personal identifier
    - Module code (TM352)
    - Assignment number (TMA 01)
    - Date

### Testing before Submission:

```bash
$ tm352 tma01 test tma01-YOUR_STUDENT_PI-q1.zip
```

## Important Notes:

- **Deadline:** 20 November 2025, 12 noon (UK time)
- **Keep notes while coding** - you'll need them for Question 3
- **Test values must be exact** (including capitalization and punctuation)
- **Generative AI:** Category 2 - can use but must cite properly
- **Each prototype worth 15 marks** (30 total for practical)
- **References don't count toward word limit**

This assignment essentially tests your ability to implement the same simple web application in two different frameworks and then critically compare your experience with both.

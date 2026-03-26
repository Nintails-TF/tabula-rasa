---
date created: Saturday, November 15th 2025, 11:50:16 am
date modified: Monday, November 17th 2025, 12:40:21 pm
---

# Development Notes


## Introduction:

I first made sure to download the new tests and patches then the run the dev servers, starting with svelte.

I made sure to start testing data using a static first approach, and introducing the API calls and dynamic data once I was ready.

I worked backwards, I first starting by running the testing suite using:
```Bash
npm run assess # Run from within svelte/react front-end.
```

I got the tests wrong, and looked at the feedback and started to work my way through them.

## Question 1: Prototype Web Applications:

For the H1 and H2 tags, I did not use `role="heading" aria-level="1"` as it was redundant. As the MDN suggests not to and to only use the native h1 to h6 tags. <https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role>

I found svelte nice, because I could include my HTML, CSS, and any script writing into a single place, and use a one page design.

I styled the CSS by using Tailwind CSS. I went with a bluish type theming.

I decided to separate the each function into separate components. So the Ticket generation, Payment generation, etc. Are all modular, and can be reused if needed. I believe that this is ultimately best practice when writing code, make things re-usable and self-contained. Yes, these could of been written as anonymous functions or all within `App.svelte`, but it's ugly and difficult to read.

The program flow was API -> Populate Component -> Display within App

On button click for the buttons, I need to know which button has been pressed, but with the visibility of the payment window, I can just use Boolean as on any button click, I can cause the payment area to appear.

When doing the card validation, I made sure to stay with strings, as if I had made it a number, I wouldn't be able to easily find the length of it and I would lose leading zeros. This is similar to why credit card details are kept as strings. You need to be critical on the data that you are carrying, as even numbers, if you aren't going to perform maths on them, you don't need to store them as numbers.

I used reduce to add values together: [TypeScript Array reduce() Method - GeeksforGeeks](https://www.geeksforgeeks.org/typescript/typescript-array-reduce-method/)

I used a reactive statement to check if both of the functions where true or not, if they were both true, the button would be activated and the acceptance message would be displayed.

I had issues during the validation of numbers, my solution depended on parseInt(), and when you try to parse an empty string, you get NaN. So I had to include an extra if check when proving validation.

I had more issues with the reactive statement, the issue that I had was that I was overwriting my card number validation with the valid check:

```typescript
$: {
    let cardValid = validateCardNumber();
    let validationValid = validateValidation();

    if (cardValid === true && validationValid === true) {
      validationMessage = "Your card number is valid.";
      isFormValid = true;
    } else {
      isFormValid = false;
    }
  }
```

I had issuers with the HMR, where the HMR wouldn't fully reload my payment processing component and I was trying to debug things that didn't exist.

***
## React:

First I decided to copy the TypeScript functions from my svelte application over to React, those being the Category and Payment components. I split my code into `components`, `hooks`, `types`, and `utilities`.

I liked this because I could keep all my code in once place and then call them or export them when I needed to, I found with svelte, I had times where I would duplicate definitions.

useMemo was nice, as I could only recalculate any reactive components when a change was made.






## Question 2: Framework Comparison:

## Question 3: Development Report:

## Question 4: Critical Self-evaluation:

---
date created: Tuesday, November 18th 2025, 5:20:31 pm
date modified: Tuesday, November 18th 2025, 5:20:49 pm
---

# Question 2: Framework Comparison Report

The Isca Augusta Management Company (IAMC) is an example of a web-based ticketing system designed for a bathhouse. By comparing Svelte and React to each other, we can better come to an understanding of both frameworks work by analysing features such as: _build-time_ versus _runtime_ approaches, state management patterns, component architecture, and template syntax.

The key difference is how each framework transforms source code into instructions which a browser can digest. Svelte uses a compiler that analyses your code during the build process and generates optimised JavaScript that directly manipulates the DOM (Svelte.dev, 2019). When someone selects a ticket category or enters card details, Svelte's pre-compiled code already knows which DOM elements need to be updated. For example, with a user inputting card details, we need to update input box values, validation messages (success or failure), and the submit button status (disabled or enabled) (Glen, Payment.svelte Lines | 92-96, 100-105, 117-126). It just executes those specific instructions without extra processing overhead.

React works differently, using a virtual DOM - a bit like checking a recipe to make sure you're putting in the right ingredient. When users interact with the interface, React updates this in-memory representation first, compares it against the actual DOM, then applies only the detected changes (Hackernoon, 2020). This adds processing overhead, but it means developers don't need to manually declare which parts are reactive or track dependencies between data and display elements. React handles this automatically through its runtime library.

For customers on various devices, Svelte's approach offers better performance on worse hardware or embedded systems since there's minimal overhead (Svelte.dev, 2019). But React's approach gives developers a more predictable and consistent experience.

How data is tracked and managed in both frameworks differs as well. Svelte provides built-in state management through stores and reactive statements that let you share data between components (Svelte.dev, 2024). The selected ticket category can exist in once place and be accessed by both the ticket selection and payment components. Simple variable assignments become reactive automatically, so when `cardResult`changes (Glen, Payment.svelte | Lines 25-37), the error or success message updates immediately. The compiler tracks these dependencies at build time and generates the necessary update code.

React takes a component-based approach where data typically exists within individual components and must be explicitly passed between them through properties or lifted up to shared parent components (Blackhound Agency, 2025). This follows atomic design principles, treating components almost like Lego blocks that modular and start off small, but construct a greater page (Frost, 2016). For the Ticket Category system, this means ticket selection state is stored in a parent component and is passed to children as needed. While this requires more explicit data flow management, it creates clear boundaries that make it easier to understand where data lives and how it moves through the application. This is helpful, since developers can reuse existing components by connecting them with different data sources, reducing development time and maintaining consistency and functionality.

Writing HTML code differs too. Svelte uses standard HTML enhanced with their homemade runes, stores and reactive statements (Svelte.dev, 2025). The ticket category buttons would be written using familiar HTML button elements, with Svelte's templating syntax handling dynamic content like titles and prices. Conditional logic for showing or hiding the payment form uses HTML-like blocks and structure (Glen, App.svelte | Lines 71-77). This makes it easier for those familiar with HTML, reducing the learning curve making Svelte more accessible to beginners.

React uses JSX, which embeds HTML-like markup directly within JavaScript code (React, 2025). This means that you can store JavaScript and HTML together. Showing ticket categories uses a JavaScript map function to convert IAMC's API data into buttons (Glen, App.tsx | Lines 48-57). JSX gives you JavaScript's full programming capabilities within the markup, so you can use any JavaScript technique to control rendering. This provides flexibility for complex interface logic but requires thinking in JavaScript rather than HTML, demanding more JavaScript proficiency but enabling sophisticated behaviours as the system grows.

Ultimately, React and Svelte represent different approaches: Svelte optimises at build time for runtime performance, while React provides runtime flexibility and consistency. For the ticketing system, both work, with the choice depending the business needs of IAMC and the any existing code bases in a real project. Sometimes raw performance and smaller code bundles might be the choice or established community support and component reusability patterns could work better. In my opinion, a start-up might choose Svelte, whilst an established company might go with React.

---

## References

Blackhound Agency (2025) _Component-based development for more performance and less costs_. Available at: [https://blackhoundagency.com/en/guides/component-based-frontend](https://blackhoundagency.com/en/guides/component-based-frontend) (Accessed: 18 November 2025).

Frost, B. (2016) _Atomic design methodology_. In: _Atomic design_. Available at: [https://atomicdesign.bradfrost.com/chapter-2/](https://atomicdesign.bradfrost.com/chapter-2/) (Accessed: 18 November 2025).

Hackernoon (2020) _Understanding React's virtual DOM_. Available at: [https://hackernoon.com/virtual-dom-in-reactjs-43a3fdb1d130](https://hackernoon.com/virtual-dom-in-reactjs-43a3fdb1d130) (Accessed: 18 November 2025).

React (2025) _Writing markup with JSX_. Available at: [https://react.dev/learn/writing-markup-with-jsx](https://react.dev/learn/writing-markup-with-jsx) (Accessed: 18 November 2025).

Svelte.dev (2019) _Svelte 3: Rethinking reactivity_. Available at: [https://svelte.dev/blog/svelte-3-rethinking-reactivity](https://svelte.dev/blog/svelte-3-rethinking-reactivity) (Accessed: 18 November 2025).

Svelte.dev (2024) _Stores_. Available at: [https://svelte.dev/docs/svelte/stores](https://svelte.dev/docs/svelte/stores) (Accessed: 18 November 2025).

Svelte.dev (2025) _Runes._ Available at: [https://svelte.dev/docs/svelte/$state](<https://svelte.dev/docs/svelte/$state>) (Accessed: 18 November 2025).

Glen (2025) TM352 TMA01 Q1 React and Svelte Front-end Project.

## Question 3: Development Report:

I started with Svelte, as I decided that it offers a much cleaner and more intuitive approach for beginners than React and since I'm rusty with writing solid good I wanted to leverage Svelte's built-in reactivity that works simply by assigning to variables, rather than relying on hooks or complex state patterns. The rationale was that it is going to be easier for me to get something up and running with Svelte first, then moving towards React once I've got the code and architecture down in Svelte. The praxis here, is that developing with an easier framework first would facilitate faster progress on a more challenging once.

In a real business problem it would really depend on the size of IAMC if a Svelte approach or React approach would be my first choice in business. Larger enterprise solutions would benefit from the ecosystem of React and developer familiarity, where as Svelte would have an edge to spin something up quicker and more efficient. You have to consider the needs of your team, organisation, and what your client wants. Being framework flexible in this way is highly useful in business teams.

I preferred React, with it's superior separations of concerns, I was able to create more discrete, functional units. For example, you have your components that construct the front-end, the hooks that communication between APIs and data sources, the types that define the blueprint of my custom objects, and utilities for the custom logic required for the card validation. (Glen | React folder structure) In this way, it felt much clearly what I had to do, it was almost as if the structure present within React enabled me to split my problems into smaller chunks which made it easier to tackle, it taught me more about modular programming since it's stricter structure demanded it.

Both systems use modular programming but within React there is a separation of concerns based on the function of a module, so Ticket construction was done within `Ticket.Svelte` within svelte and then API call it within my `App.svelte`, It was frustrating that the API call was stuck within the `App.svelte`, since it's less reusable and better to have the API calls that are encapsulated. Where as within React, I had to use both the Ticket prop (Glen, Ticket.tsx | Lines 1-17 ) then to link it up with the API call logic (Glen, useTicketCategories.ts | Lines 4-24). I found this structure to be more as the cleaner division based on functionality leads to better code maintainability and testability.

Within Svelte I had ended up duplicating code. In Payment.svelte for example, the `selectedCategory` prop. I ended up passing the prop from App -> Payment -> App (Glen, Payment.svelte | Lines 4-10). Which wasn't ideal as the data wasn't actually used within the Payment section so it was redundant, this is why I preferred the more strict layers of abstraction in React - whilst it was more verbose and clunky. It enabled me to have a cleaner picture of what was going on and to better encapsulate my code within reusable chunks. I tried doing the same thing when I was working in Svelte. But it didn't seem to go as well, but I'm not sure if this is because I had a better idea of what I was making since it was my 2nd go with React or if the framework hindered me.

In conclusion I'd say that with React, the more mature nature of it and ecosystem provided better guardrails and put me down the path of making a more concrete and solid application and building better architecture rather than Svelte, where I was forced to either manually handle or come up with a dirtier solutions to solve problems.

**Reference List:**  
Glen (2025) TM352 TMA01 Q1 React and Svelte Front-end Project.

## Question 4: Critical Self-evaluation:

I found the pace of the course to be most challenging. Trying to learn two frameworks at once, each having a different approach but with some similarities. I found it hard to strike a balance between depth and width, going forward, I'll have to be more time conscious and hone in on skills that are assessed and are in TMAs/EMAs.

I looked at the main structure of the consulting agency text, I looked at each section and boiling it down into four key concepts.

1. Architecture: Build-time vs. Runtime Transformation
    1. How Svelte has less overhead because it isn't running a virtual DOM.
2. State Management
    1. Svelte uses built-in reactivity, React uses states within individual components
3. Component Architecture and Data Flow
    1. React more strict, Svelte more flexible
4. Template Syntax
    1. The difference in syntax (JSX vs HTML-like with Svelte keyword enrichment)

I then gradually expanded upon these points after reading the documents listed and analysing my own personal notes to come up with better judgments, after I had completed my first draft, I wrote a second draft including code examples where appropriate to highlight my points.
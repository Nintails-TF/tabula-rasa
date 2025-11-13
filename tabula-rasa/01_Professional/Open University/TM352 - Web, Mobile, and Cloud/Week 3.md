---
date created: Thursday, November 13th 2025, 12:17:30 pm
date modified: Thursday, November 13th 2025, 1:03:12 pm
---

# Week 3:

# 1. Introduction:

Before learning about modern web app structure, it's key to understand the idea of **user interaction logic** within web technologies (HTML, CSS, JavaScript).

**User interaction logic** refers to *the code handles user interactions and how a website should respond.* Basically it's designing your website so that it's interactive rather than static.

However, in the modern era - we don't design websites using pure HTML, CSS, and JavaScript - this is because it is laborious to do so. We use various frameworks to speed up the process, so that features can be made faster.
# 2. Aims:

**This weeks aims are:**
- To understand the core architectures of frontend frameworks.
- What factors to take into account when picking a frontend framework.
- How to build a basic React web application.
- How to build a basic Svelte web application.

# 3. Core Front-end Concepts:

As websites have grown in power and interactivity with the growth of HTML 5, more powerful web apps can now be made, but development is more complex. This introduced a problem: *Lots of time was spent re-implementing functionality.* To fix this the first frameworks were invented.

The core aspects of frameworks are the following.

### Core Framework Features:

- **State change detection and re-rendering** - Automatically detects when application state changes and efficiently updates only the necessary parts of the UI.
- **Component composition** - Provides structure for combining multiple components into a complete application.

### Common Additional Features:

- **Data fetching** - Simplified integration for retrieving data from servers.
- **Routing** - URL-based navigation that preserves user location and enables bookmarking/sharing.
- **Advanced state management** - Handles shared state across components, complex state logic, and consistency validation.
- **Event handling** - Custom event systems for component communication.

## 3.1. Single Page Applications:

The primary structure for most modern front-end frameworks is the idea of a **single page application.** The idea is that a single HTML file is used to load the application, then JavaScript is used to update it.

Basic Flow:
![[../../../03_Reference/Pictures/week3-TM352-flowchart.png]]

Depending on the framework and technologies used, the URL may updated to reflect changes in the application. However, like traditional navigation in a HTML site, the browser does not need to fetch a new URL. JavaScript will fetch any new data needed and update the HTML.
## 3.2. Server-side Rendering:

However, single page applications (SPA) run into a significant problem. Because content is hidden behind JavaScript interactions, search engines cannot access the page content as well as traditional HTML.

The process of **Server-side Rendering** (SSR) tries to fix this issue. The idea is that you use the SPA structure for users, whilst the server runs the front-end application and generates HTML for all screens/interactions that the search engine can then look at.

In web browsers, SSR applications have another step, after a browser has loaded the HTML and JS. The JavaScript then adds all event handlers into the static HTML - this ensures that the application is fully functional.

This process is called **rehydration.** Where a dry, static HTML page is given context and made to be interactive and consumable.

SSR is a form of caching basically, one constraint with SSR is that it can only be applied to the same context that is available for each user. So if a user is logged in, the application wouldn't know what content to serve, as the server side rendering wouldn't work globally.
## 3.3 Web Bundlers:

**Web Bundlers** combine multiple application files (HTML, JavaScript, CSS, images) into fewer, larger files for efficient browser delivery, since establishing network connections is slower than transferring data.

**Common Processing Steps:**
- **JavaScript extensions** - Converts framework-specific JavaScript syntax into standard browser-compatible JavaScript.
- **CSS processing** - Transforms CSS extensions into standard CSS.
- **Transpiling** - Converts newer JavaScript features (or languages like TypeScript) into widely-supported JavaScript for older browsers.
- **Compression/Minification** - Removes whitespace and shortens variable names to reduce file size while maintaining functionality.

Modern development tools provide default bundler configurations that work without manual setup, hiding the underlying complexity.

# 4. Choosing a Framework:

The most used modern frameworks are:
- React - by a wide margin
- Vue
- Angular
- Svelte

You can build a functional web app

# 5. Svelte

# 6. React

***

# Weekly Tasks:

# 1. Basic Svelte Application:

## 1.1. Development Server:

## 1.2. Basic Structure:

## 1.3. Using Components:

## 1.4. Conditionals:

## 1.5. User Interaction:

# 2. Basic React Application:

## 2.1. Basic Structure:

## 2.2. Using Components:

## 2.3. Loops:

## 2.4. Creating a Component:

## 2.5. Conditionals:

## 2.6. User Interaction:





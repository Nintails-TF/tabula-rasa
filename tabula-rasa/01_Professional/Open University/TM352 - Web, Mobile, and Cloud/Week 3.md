---
date created: Thursday, November 13th 2025, 12:17:30 pm
date modified: Thursday, November 13th 2025, 2:41:16 pm
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

You can build a functional web app with any frameworks. They have advantages and disadvantages for a developer. Though, most of these decisions are non-technical. Such as:

- **Technical constraints** come first - existing codebases and client requirements typically lock you into a specific framework. If your team already has experience with a framework, leveraging that expertise makes sense for consistency and knowledge transfer.
- **Framework capabilities** matter for specialized needs, particularly around tooling for specific use cases like offline functionality.
- **Security factors** are critical - you should evaluate the framework's security track record, how it handles vulnerability reports, and its history of patching issues, since framework vulnerabilities directly affect your application.
- **Community support** is essential for long-term success. Look at responsiveness to bug reports, the number of open issues, and how welcoming the project is to external contributions, as you'll inevitably need help with framework-specific problems.
- **Installation complexity** can signal underlying code complexity, which correlates with potential issues down the line.
- Finally, **strategic skill development** might influence your choice if the business wants to expand into new technical areas.

It isn't enough to just understand and know one framework, even if it is super popular - it may work for now, but not forever.

# 5. Svelte:

Svelte takes a different approach than other frameworks. It combines the **application code** and **framework code.** In React, the application code and framework library code is both ran by the browser.

The framework then would call the application code and re-render the page based on application changes made by the application code.

Svelte does most of the work at build time. Svelte compiles application code, and inserts JavaScript code from the Svelte library to update details to the user.

This structure can simplify code, but can run into problems in the lifecycle for code. In practice, this makes little difference and large-scale complex web apps can be built in Svelte.

# 6. React

***

# Weekly Tasks:

# 1. Basic Svelte Application:

## 1.1. Development Server:

The web bundler software used throughout this module is called: [Rollup](https://rollupjs.org/). The following process is used when we build our application:

1. **Svelte** is used to compile our application code, creating the necessary JavaScript and CSS code
2. **Tailwind** is used to identify which CSS classes are used in the application code and output the necessary CSS
3. **Rollup** writes the JavaScript and CSS code to one or more files.

To see this in action, we can build our code - normally this is only done for a final deployment:

```Bash
npm ci
npm run build

Server available at http://localhost:5173/

vite v5.3.5 building for production...
✓ 31 modules transformed.
dist/index.html                 0.46 kB │ gzip: 0.30 kB
dist/assets/index-D94lVMts.css  6.62 kB │ gzip: 1.93 kB
dist/assets/index-BKUxqrnq.js   9.27 kB │ gzip: 4.06 kB
```

As we can see, Vite then runs Rollup to build our app. The builder can split files into separate CSS and JS files, to improve loading speed, but that isn't required here.

### 1.1.1. Hot Module Replacement:

As our project grows, build processes can take longer and longer, this is fine for the production build, but if we are testing or developing, this can be troublesome.

**Hot Module Replacement** (HMR) enables a build to inject extra code into the JavaScript. When a file is modified by a developer, only that file is rebuilt. 

This significantly speeds up the development process.

### 1.1.2. Vite:

Vite handles lots of manual configuration of Rollup and HMR, it gives us a development server and runs the other libraries and software we need to build our app.

Vite is typically configured using `vite.config.ts`, in our project this refers to:

```TypeScript
import { defineConfig } from 'vite'
import { svelte } from '@sveltejs/vite-plugin-svelte'

let base = process.env.JUPYTERHUB_SERVICE_PREFIX || "/";
let app_path = "http://localhost:5173";
if (process.env.VSCODE_PROXY_URI) {
  const url = new URL(process.env.VSCODE_PROXY_URI);
  app_path = url.protocol + "//" + url.host;
  base = base + "proxy/absolute/5173";
}
app_path = app_path + base;
console.log("\nServer available at " + app_path + "\n");

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [svelte()],
  base: base,
})
```

**Code Summary:**
- **Basic setup**: Uses Vite's `defineConfig` with the Svelte plugin to handle Svelte-specific build processing
- **Base path configuration**: The `base` parameter tells Vite where the app is hosted (e.g., root `/` vs sub-path `/path/to/app`) so it generates correct URLs
- **Automatic environment detection**: The code intelligently determines the correct `base` path by checking:
    - If running in OCL (Online Coding Lab): uses `JUPYTERHUB_SERVICE_PREFIX` environment variable
    - If running in VCE (VS Code Environment): detects `VSCODE_PROXY_URI` and appends `"proxy/absolute/5173"` to route through VCE's proxy
- **User convenience**: Calculates and displays the full server URL so users don't have to manually construct it themselves
## 1.2. Basic Structure:

```Bash
npm run dev
```

The basic structure of a Svelte Application is the component. The `src/App.svelte`component is the default main component. 

Within Svelte each file defines one component which has three elements:

1. A `<script>` tag at the top of the file into which you will place all of the TypeScript code.
2. One or more HTML tags that define the HTML that is rendered in the browser
3. A `<style>` tag for defining CSS rules that are applied only to this component. Due to using Tailwind, we generally won’t use this, but it can be useful when using CSS directly or using other CSS frameworks.

The case study of **Sounds Good! - Music Streaming Service.** Is how we are going to show and expand knowledge of Svelte.

#### Header:
```HTML
<header class="max-w-screen-md mx-auto bg-pink-600 text-2xl font-bold p-3">
  <h1>Sounds Good! - Epic Playlist</h1>
</header>
```

The challenge of writing a new web app, is not writing the code, but splitting the big problems into smaller chunks so that you can handle them.

#### List:
```HTML
<main class="max-w-screen-md mx-auto">
  <ol class="border-4 border-pink-600">
  </ol>
</main>
```


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





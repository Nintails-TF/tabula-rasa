---
date created: Thursday, November 13th 2025, 12:17:30 pm
date modified: Friday, November 14th 2025, 2:31:12 pm
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

#### List Structure:
```HTML
<main class="max-w-screen-md mx-auto">
    <ol class="border-4 border-pink-600">
      <li class="flex flex-row px-3 py-2 space-x-4 mb-2">
        <div
          class="w-12 h-12 text-neutral-400 p-2 border border-neutral-400"
          aria-hidden="true"
        >
          Art
        </div>
        <div class="flex-1 flex flex-row items-center">
          <div class="flex-1">
            <h2 class="font-bold">Track title</h2>
            <p>Track artist - Track album</p>
          </div>
          <p class="text-neutral-200">Track length</p>
        </div>
        <button class="w-12 h-12 p-2">Pause</button>
      </li>
```

## 1.3. Using Components:

So the current approach only uses code that is defined within the `src/App.Svelte` this isn't scalable so we need to start to build components which can be reused.

### Specifying Component:

```HTML
<script lang="ts">
  // Importing icons from the Material Design Icons
  import { mdiMusic, mdiPause } from "@mdi/js";
  import Icon from "./lib/Icon.svelte";
</script>

<div>
	<Icon path={mdiMusic} />
</div>
```

As we can see, we've importing the Icon component into the and we pass the parameters of `mdiMusic` and `mdiPause` into the prop.

Result:
![[../../../03_Reference/Pictures/Pasted image 20251113150322.png]]

## 1.4. Loops:

```HTML
<script lang="ts">
  import { mdiMusic, mdiPause } from "@mdi/js";
  import Icon from "./lib/Icon.svelte";
  
  const TRACKS = [
    {
      id: 1,
      title: "Midnight Dreams",
      artist: "The Echoes",
      album: "Night Sessions",
      length: "4:23",
    },
    {
      id: 2,
      title: "Summer Vibes",
      artist: "Coastal Sound",
      album: "Beach Days",
      length: "3:45",
    },
  ];
</script>

...SNIP...

<ol class="border-4 border-pink-600">
  {#each TRACKS as track}
    <li class="flex px-3 py-2 space-x-4">
      ...SNIP...
      <h2 class="font-bold">{track.title}</h2>
      <p>{track.artist} - {track.album}</p>
      ...SNIP...
    </li>
  {/each}
</ol>

...SNIP...

```

In order to create our application so far, we've duplicated code, now if a user wants to set a certain amount of songs to their playlist, this implementation doesn't work too well.

Solutions to this type of problem is as followed:
1. First we need to move track data outside of the HTML.
	1. We move this data into some kind of array structure.
2. We use a loop to generate HTML, but dating the data from the array.

This is a common design practice. **First design using static data, then introduce dynamic data.**
## 1.5. Creating Our Own Components:

All of the code that we've made is stored within a single component, excluding the Icon component that came with the skeleton. This structure is fine in smaller applications, but in larger web apps this structure is unsustainable.

The solution? **Split the application into multiple components.**

It is difficult to recognise what should and should not be a component, we generally consider two main factors:

1. Any functionality that is used in multiple places should be a component.
2. Any functionality that is clearly defined and separated from other functionality should be a component.

When decided to implement this (refactoring), you can create candidates of what can or should be made into a function, then operate at your digression. Storing components is also a challenge, but in this module: `src/lib` location is generally enough.

### Building a Playlist Item Component:

```HTML
<!-- Within /basic-svelte/src/lib/PlaylistItem.svelte -->
<script lang="ts">
  import { mdiMusic, mdiPause } from "@mdi/js";
  import Icon from "./Icon.svelte";

  export let track: Track;
  export let state: "playing" | "paused";
</script>
```

This code will initially cause errors, as we have not defined what `Track` is. We need to define the type of data that the Track type will hold.

```JSON
<!-- Within /basic-svelte/vite-env.d.ts -->
type Track = {
  id: number,
  title: string,
  artist: string,
  album: string,
  length: string,
};
```

Then you would add the content of this module to the `vite-env.d.ts` file:

```TypeScript
<li class="flex flex-row px-3 py-2 space-x-4 mb-2">
  <div
    class="w-12 h-12 text-neutral-400 p-2 border border-neutral-400"
    aria-hidden="true">
      <Icon path={mdiMusic} />
  </div>
  <div class="flex-1 flex flex-row items-center">
    <div class="flex-1">
      <h2 class="font-bold">{track.title}</h2>
      <p>{track.artist} - {track.album}</p>
    </div>
    <p class="text-neutral-200">{track.length}</p>
  </div>
  <button class="w-12 h-12 p-2">
    <Icon path={mdiPause} />
  </button>
</li>
```

Finally, we can import the new module and call it within our loop:
```HTML
<script lang="ts">
  import PlaylistItem from "./lib/PlaylistItem.svelte";
  
...SNIP...

{#each TRACKS as track}
  <PlaylistItem {track} state="paused"/>
{/each}
```

## 1.6. Conditionals:

In addition to looping, the second structural element used are conditional statements, these are represented using `if` statements. In order to start this, we need to track the `id` of the currently playing track.

```JavaScript
<!-- within src/App.svelte in the script tag. -->
let currentTrack = -1;
```

At the moment, the `PlaylistItem` track, will always set the state to paused. Now that we have a variable to indicate if a track is playing or not, we can dynamically calculate the value of the state and update if a track is playing or not.

```HTML
<!-- Within App.svelte, loop section-->
<PlaylistItem
  {track}
  state={track.id === currentTrack ? "playing" : "paused"}
/>
```

If the state is true, we set the state of the track to playing, otherwise, we set it to paused. However for this to work, we need to make use of the state prop within our `PlaylistItem`:

```HTML
  <button
    class="w-12 h-12 p-2"
    aria-label={state === "playing" ? "Pause this track" : "Play this track"}
  >
    {#if state === "playing"}
      <Icon path={mdiPause} />
    {:else}
      <Icon path={mdiPlay} />
    {/if}
  </button>
```
## 1.7. User Interaction:

## Core Concepts

User interaction in Svelte consists of two parts:
1. **Event handler function** - defines what happens when interaction occurs
2. **Event listener attachment** - connects the handler to the DOM element

## Basic Event Handling

### Creating an Event Handler

```javascript
function playPauseTrack() {
  dispatch("click");
}
```

### Attaching to Elements

```svelte
<button on:click={playPauseTrack}>
```

The syntax follows: `on:eventName={handlerFunction}`
## Custom Event Dispatching

Components don't benefit from DOM event bubbling, so custom events must be dispatched manually.

### In Child Component (PlaylistItem.svelte)

```javascript
import { createEventDispatcher } from "svelte";

const dispatch = createEventDispatcher();

function playPauseTrack() {
  dispatch("click");
}
```

### In Parent Component (App.svelte)

```JavaScript
<PlaylistItem
  {track}
  state={track.id === currentTrack ? "playing" : "paused"}
  on:click={() => {
    track.id === currentTrack
      ? (currentTrack = -1)
      : (currentTrack = track.id);
  }}
/>
```

## Key Implementation Details
- **Anonymous functions** are used when each component instance needs different behavior
- Svelte automatically recalculates and updates the DOM when reactive variables change
- Setting `currentTrack = -1` effectively "pauses" by making no track match the current state
- The ternary operator checks if clicking an already-playing track (to pause) or a paused track (to play)

## Reactivity Flow
1. User clicks button
2. Child dispatches custom event
3. Parent handles event, updates state variable
4. Svelte recalculates dependent values
5. Props update, triggering DOM re-render only where needed
# 2. Basic React Application:

React was initially created within Facebook, but it has been made open source and is the most widely used framework. React is only concerned with the user interface, so we would need other libraries to different URLs for a more complex application state.

React Native can be used to develop mobile apps.
## 2.1. Basic Structure:

**To Setup:**
```Bash
npm ci
npm run dev
```

In React, unlike Svelte. Any component specific CSS is placed into a separate file with the same name but with the `.css` extension. So `App.tsx` would have `App.css`. In this case we won't be using the CSS file as we're using Tailwind CSS.

```React
export default function App() {
  return (
    <header>
      <h1>Sounds Good! - Epic Playlist</h1>
    </header>
  );
}
```

Components in React are defined using TypeScript or JavaScript and are [defined as functions]([Your First Component – React](https://react.dev/learn/your-first-component)). Within the curly braises we use TSX code, which accepts HTML and Typescript.

Note that TypeScript, must contain only a single top level `div` tag to function:
## 2.2. Using Components:
### 2.2.1 Importing Components and Icons

React allows us to import and use external components from libraries. For icons, we use the Material Design Icons library:

```tsx
import { Icon } from '@mdi/react';
import { mdiMusic, mdiPause } from '@mdi/js';
```

- `@mdi/react` provides the `Icon` component (unlike Svelte where we created our own)
- `@mdi/js` provides the icon path data
### 2.2.2. Using the Icon Component

Components in React are used like HTML tags. Pass props using curly braces `{}`:

```tsx
<div className="w-12 h-12 text-neutral-400 p-2 border border-neutral-400"
     aria-hidden="true">
  <Icon path={mdiMusic} />
</div>
```

The `path` prop receives the imported icon data (`mdiMusic`) to display the correct icon.
### 2.2.3. Key Differences from Svelte

- React uses `className` instead of `class`
- Props are passed directly with curly braces: `{value}` instead of Svelte's `{value}` or `prop={value}`
- Component imports come directly from the library package rather than creating wrapper components

## 2.3. Loops:
### 2.3.1. State Management with useState

Unlike Svelte where variables in `<script>` are automatically reactive, React requires explicit state management:

```tsx
import { useState } from 'react';

const [items] = useState([
  {
    id: 1,
    title: 'Track title',
    artist: 'Artist Name',
    album: 'Album Name',
    length: '4:23',
  },
  // ... more items
] as Track[]);
```

**Key points:**
- `useState` takes the initial state as a parameter
- Returns `[currentState, updateFunction]` - we're only using `currentState` here
- Destructuring `[items]` captures the current state, discards the update function

### 2.3.2. Type Definition

Define types in `src/vite-env.d.ts`:

```tsx
type Track = {
  id: number,
  title: string,
  artist: string,
  album: string,
  length: string,
};
```

### 2.3.3. Looping with `.map()`

React has no template control structures like Svelte's `{#each}`. Instead, use JavaScript's `.map()` function:

```tsx
const ITEMS_LIST = items.map((track) => {
  return (
    <li className="flex flex-row px-3 py-2 space-x-4 mb-2">
      <h2 className="font-bold">{track.title}</h2>
      <p>{track.artist} - {track.album}</p>
      <p className="text-neutral-200">{track.length}</p>
    </li>
  );
});
```

**How `.map()` works:**
- Takes a function as parameter
- Runs the function for each array item
- Returns a new array with the results
- Converts `Track[]` → `JSX.Element[]`

### Rendering the List

Insert the mapped JSX array using curly braces:

```tsx
<ol className="border-4 border-pink-600">
  {ITEMS_LIST}
</ol>
```

React's rendering engine automatically converts the JSX array into HTML elements.

## Key Differences from Svelte

|Svelte|React|
|---|---|
|Variables are reactive by default|Must use `useState`|
|`{#each items as item}`|`items.map((item) => ...)`|
|Template-based loops|JavaScript function-based loops|

## 2.4. Creating a Component:

Create a new component file (e.g., `src/PlaylistItem.tsx`):

```tsx
export default function PlaylistItem() {
  return (<div></div>)
}
```

### 2.4.1. Props and Type Safety

#### 2.4.1.1. Define Props Type

Add to `src/vite-env.d.ts`:

```tsx
type PlaylistItemProps = {
  track: Track
};
```

#### 2.4.1.2. Receive Props with Destructuring

```tsx
export default function PlaylistItem({ track }: PlaylistItemProps) {
  return (
    <li>
      <h2>{track.title}</h2>
      <p>{track.artist} - {track.album}</p>
    </li>
  )
}
```

**Destructuring benefits:**
- `{ track }: PlaylistItemProps` extracts `track` directly from props
- Access fields as `track.title` instead of `props.track.title`
- Cleaner, less verbose code

### Using the Component

#### Import the Component

```tsx
import PlaylistItem from './PlaylistItem';
```

#### Map with Key Prop

```tsx
const ITEMS_LIST = items.map((track) => {
  return (
    <PlaylistItem
      key={track.id}
      track={track}
    />
  )
});
```

### The `key` Prop

**Critical for lists:**
- Not defined in your props type - it's a special React prop
- Must be unique for each item in the list
- Helps React identify which items changed/added/removed
- Enables efficient updates without comparing full HTML
- Use a stable unique identifier (like `id`)

### Key Differences from Svelte

|Svelte|React|
|---|---|
|`export let track`|`{ track }: PlaylistItemProps`|
|Props auto-declared|Props passed as function parameter|
|No key requirement|`key` prop required in lists|
## 2.5. Conditionals:

## State with Update Function

Unlike earlier examples, here we capture both the state value and its update function:
```tsx
const [currentTrack, updateCurrentTrack] = useState(-1);
```

- `currentTrack` = current state value
- `updateCurrentTrack` = function to change the state
- Initial value: `-1` (no track playing)

## Conditional Props

Update the props type in `src/vite-env.d.ts`:
```tsx
type PlaylistItemProps = {
  track: Track,
  state: 'playing' | 'paused',
};
```

Pass conditional values using ternary operator:
```tsx
const ITEMS_LIST = items.map((track) => {
  return (
    <PlaylistItem
      key={track.id}
      track={track}
      state={track.id === currentTrack ? 'playing' : 'paused'}
    />
  )
});
```

## Conditional Rendering

React has no template syntax like Svelte's `{#if}`. Use inline ternary operators:
```tsx
export default function PlaylistItem({ track, state }: PlaylistItemProps) {
  return (
    <button
      aria-label={state === "playing" ? "Pause this track" : "Play this track"}
    >
      <Icon path={state === 'playing' ? mdiPause : mdiPlay} />
    </button>
  )
}
```

### Alternative Approach (for Complex conditionals)

For more complex differences, use JavaScript variables:
```tsx
let icon = (<Icon path={mdiPlay} />);
if (state === 'playing') {
  icon = (<Icon path={mdiPause} />);
}

return <button>{icon}</button>
```

**Note:** This approach adds verbosity—only use for significant conditional differences.
## Key Differences from Svelte

|Svelte|React|
|---|---|
|`{#if condition}...{/if}`|Ternary: `condition ? a : b`|
|Template-based conditionals|JavaScript expression-based|
|Explicit conditional blocks|Inline expressions in JSX|
## Best Practice

Use inline ternary operators for simple conditionals directly in JSX. Reserve variable assignment with `if` statements for complex conditional logic with significant differences.

## 2.6. User Interaction:

## Event Handling Pattern

**Key difference from Svelte:** Instead of creating custom events in child components, React passes event handler functions as props from parent to child.

## Define Event Handler Prop

Add to `src/vite-env.d.ts`:
```tsx
type PlaylistItemProps = {
  track: Track,
  state: 'playing' | 'paused',
  onClick: () => void,  // Function with no params, returns nothing
};
```

## Pass Handler from Parent

In `src/App.tsx`:
```tsx
const ITEMS_LIST = items.map((track) => {
  return (
    <PlaylistItem
      key={track.id}
      track={track}
      state={track.id === currentTrack ? 'playing' : 'paused'}
      onClick={() => { updateCurrentTrack(track.id) }}
    />
  )
});
```

Anonymous function calls `updateCurrentTrack` with the track's ID when clicked.

## Attach Handler in Child

In `src/PlaylistItem.tsx`:
```tsx
export default function PlaylistItem({ track, state, onClick }: PlaylistItemProps) {
  return (
    <button
      onClick={onClick}
      className="w-12 h-12 p-2"
    >
      <Icon path={state === 'playing' ? mdiPause : mdiPlay} />
    </button>
  )
}
```

## React Event Loop
1. **Initial render:** Component runs, creates state with initial value
2. **User interaction:** Button clicked → `onClick` handler executes
3. **State update:** `updateCurrentTrack()` changes state value
4. **Re-render:** React re-runs component function with new state
5. **DOM update:** React efficiently updates only changed parts of DOM

## Toggle Pattern (Play/Pause)

To implement pause functionality:
```tsx
onClick={() => { 
  track.id === currentTrack 
    ? updateCurrentTrack(-1)      // Pause: set to -1
    : updateCurrentTrack(track.id) // Play: set to track ID
}}
```

## Standard React Pattern

**"Define → Handle → Update":**
1. Define state variable with `useState`
2. Add event handler prop
3. In handler, update state variable
4. React automatically re-renders with new state

## Key Differences from Svelte

| Svelte                     | React                          |
| -------------------------- | ------------------------------ |
| Child creates custom event | Parent passes handler function |
| `createEventDispatcher()`  | Props with function type       |
| `dispatch('event')`        | `onClick={handler}`            |
| Event bubbles up           | Function called directly       |

***



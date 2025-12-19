---
date created: Friday, November 14th 2025, 2:41:11 pm
date modified: Friday, November 14th 2025, 2:44:55 pm
---

# Remote Data in Svelte - Practical Guide

## Overview

This guide demonstrates how to connect a Svelte frontend application to a backend server using the Fetch API to exchange data.

## Setup

### Project Structure

```
work/
├── remote-svelte/     # Frontend Svelte app
└── remote-backend/    # Express.js backend server
```

### Installation Commands

```bash
# Frontend (in work/remote-svelte)
npm ci
npm run dev

# Backend (in work/remote-backend)
npm ci
npm run server
```

## Backend Server Implementation

### Server Structure (`server.ts`)

```typescript
import * as express from "express";

type Track = {
  id: number,
  title: string,
  artist: string,
  album: string,
  length: string,
};

const APP = express();
const TRACKS = [
  {
    id: 1,
    title: "Track title",
    artist: "Artist Name",
    album: "Album Name",
    length: "4:23",
  },
  // ... more tracks
] as Track[];

// GET endpoint - retrieve playlist items
APP.get("/api/playlist/items", (request, response) => {
  response.setHeader("Content-Type", "application/json");
  response.setHeader("Access-Control-Allow-Origin", "*");
  response.send(JSON.stringify(TRACKS));
});

// POST endpoint - play a track
APP.post("/api/playlist/play/:track_id", (request, response) => {
  response.setHeader("Access-Control-Allow-Origin", "*");
  const track_id = Number.parseInt(request.params.track_id);
  let found = false;
  
  for (const track of TRACKS) {
    if (track.id === track_id) {
      console.log("Playing " + track.title);
      response.status(204);
      found = true;
      break;
    }
  }
  
  if (!found) {
    response.status(404);
  }
  response.end();
});

APP.listen(5172, () => {
  // Server URL configuration
  console.log("\nAPI server available at http://localhost:5172\n");
});
```

### Testing the Server

```bash
# Test the GET endpoint
curl http://localhost:5172/api/playlist/items
```

## Frontend Implementation (Svelte)

### 1. Basic Setup with Empty Tracks

```svelte
<script lang="ts">
  import { onMount } from "svelte";
  import PlaylistItem from "./lib/PlaylistItem.svelte";

  // Change from const to let for updating
  let tracks: Track[] = [];
  const serverBaseUrl = "http://localhost:5172"; // Your server URL
  let currentTrack = -1;
</script>
```

### 2. Fetching Data on Mount

```svelte
<script lang="ts">
  import { onMount } from "svelte";
  
  onMount(() => {
    // Fetch playlist items when component mounts
    const request = window.fetch(serverBaseUrl + "/api/playlist/items");
    
    request.then((response) => {
      response.json().then((data) => {
        tracks = data; // Update tracks with server data
      });
    });
  });
</script>
```

### 3. Sending Data to Server

```svelte
<PlaylistItem
  {track}
  state={track.id === currentTrack ? "playing" : "paused"}
  on:click={() => {
    // Only send POST request when starting to play
    if (track.id !== currentTrack) {
      window.fetch(serverBaseUrl + "/api/playlist/play/" + track.id, {
        method: "POST",
      });
      currentTrack = track.id;
    } else {
      currentTrack = -1; // Pause without server notification
    }
  }}
/>
```

### 4. Complete Component

```svelte
<script lang="ts">
  import { onMount } from "svelte";
  import PlaylistItem from "./lib/PlaylistItem.svelte";

  let tracks: Track[] = [];
  const serverBaseUrl = "http://localhost:5172";
  let currentTrack = -1;

  onMount(() => {
    const request = window.fetch(serverBaseUrl + "/api/playlist/items");
    request.then((response) => {
      response.json().then((data) => {
        tracks = data;
      });
    });
  });
</script>

<div class="min-h-screen bg-slate-800 text-white">
  <header class="max-w-screen-md mx-auto bg-pink-600 text-2xl font-bold p-3">
    <h1>Sounds Good! - Epic Playlist</h1>
  </header>
  <main class="max-w-screen-md mx-auto">
    <ol class="border-4 border-pink-600">
      {#each tracks as track}
        <PlaylistItem
          {track}
          state={track.id === currentTrack ? "playing" : "paused"}
          on:click={() => {
            if (track.id !== currentTrack) {
              window.fetch(serverBaseUrl + "/api/playlist/play/" + track.id, {
                method: "POST",
              });
              currentTrack = track.id;
            } else {
              currentTrack = -1;
            }
          }}
        />
      {/each}
    </ol>
  </main>
</div>
```

## Key Concepts

### Fetch API Pattern

```javascript
// GET request
fetch(url)
  .then(response => response.json())
  .then(data => {
    // Handle data
  });

// POST request
fetch(url, {
  method: "POST",
  // Optional: body, headers, etc.
});
```

### REST API Structure

- **GET `/api/playlist/items`** - Retrieve all tracks
- **POST `/api/playlist/play/:id`** - Play specific track

### Important Notes

1. **Server Restart Required**: After modifying `server.ts`, restart the server (`Ctrl+C` then `npm run server`)
    
2. **CORS Headers**: The server includes `Access-Control-Allow-Origin: *` to allow cross-origin requests
    
3. **State Management**: Changed from `const TRACKS` to `let tracks` to enable updates
    
4. **Lifecycle Hooks**: Use `onMount()` to fetch data when component loads
    
5. **Conditional Requests**: Only send POST request when playing, not pausing
    

## Workflow Summary

1. **Server starts** → Provides API endpoints
2. **Frontend loads** → `onMount()` triggers
3. **Fetch data** → GET request to `/api/playlist/items`
4. **Update UI** → Assign response to `tracks` variable
5. **User interaction** → Click play button
6. **Send action** → POST request to `/api/playlist/play/:id`
7. **Server logs** → "Playing [track title]"

## Extensions for Production

- Add error handling for failed requests
- Implement auto-refresh/polling
- Add loading states
- Cache responses
- Handle network failures gracefully
- Add authentication tokens
- Implement optimistic updates

***

# Remote Data in React - Practical Guide

## Overview

This guide demonstrates how to connect a React frontend application to a backend server using the Fetch API, following the same patterns as the Svelte implementation.

## Setup

### Project Structure

```
work/
├── remote-react/      # Frontend React app
└── remote-backend/    # Express.js backend server (same as Svelte)
```

### Installation Commands

```bash
# Frontend (in work/remote-react)
npm ci
npm run dev

# Backend (in work/remote-backend) - if not already running
npm ci
npm run server
```

## React Implementation

### 1. Import Required Hooks

```tsx
import { useEffect, useState } from 'react';
import PlaylistItem from './PlaylistItem';
```

### 2. Setup State Variables

```tsx
export default function App() {
  const [serverBaseUrl] = useState("http://localhost:5172");
  const [items, updateItems] = useState([] as Track[]);
  const [currentTrack, updateCurrentTrack] = useState(-1);
```

### 3. Fetch Data with useEffect

```tsx
useEffect(() => {
  const request = window.fetch(serverBaseUrl + "/api/playlist/items");
  request.then((response) => {
    response.json().then((data) => {
      updateItems(data);
    })
  });
}, [serverBaseUrl]);
```

**Key Points about useEffect:**

- First parameter: Callback function for synchronization
- Second parameter: Dependency array
- Runs once on mount and when dependencies change
- In React Strict Mode (dev), effects run twice intentionally

### 4. Send Data to Server

```tsx
const ITEMS_LIST = items.map((track) => {
  return (
    <PlaylistItem
      key={track.id}
      track={track}
      state={track.id === currentTrack ? 'playing' : 'paused'}
      onClick={() => {
        // Only send POST when starting to play
        if (track.id !== currentTrack) {
          window.fetch(serverBaseUrl + "/api/playlist/play/" + track.id, { 
            method: "POST" 
          });
          updateCurrentTrack(track.id);
        } else {
          updateCurrentTrack(-1); // Pause without server notification
        }
      }}
    />
  )
});
```

### 5. Complete Component

```tsx
import { useEffect, useState } from 'react';
import PlaylistItem from './PlaylistItem';

export default function App() {
  const [serverBaseUrl] = useState("http://localhost:5172");
  const [items, updateItems] = useState([] as Track[]);
  const [currentTrack, updateCurrentTrack] = useState(-1);

  useEffect(() => {
    const request = window.fetch(serverBaseUrl + "/api/playlist/items");
    request.then((response) => {
      response.json().then((data) => {
        updateItems(data);
      })
    });
  }, [serverBaseUrl]);

  const ITEMS_LIST = items.map((track) => {
    return (
      <PlaylistItem
        key={track.id}
        track={track}
        state={track.id === currentTrack ? 'playing' : 'paused'}
        onClick={() => {
          if (track.id !== currentTrack) {
            window.fetch(serverBaseUrl + "/api/playlist/play/" + track.id, { 
              method: "POST" 
            });
            updateCurrentTrack(track.id);
          } else {
            updateCurrentTrack(-1);
          }
        }}
      />
    )
  });

  return (
    <div className="min-h-screen bg-slate-800 text-white">
      <header className="max-w-screen-md mx-auto bg-pink-600 text-2xl font-bold p-3">
        <h1>Sounds Good! - Epic Playlist</h1>
      </header>
      <main className="max-w-screen-md mx-auto">
        <ol className="border-4 border-pink-600">
          {ITEMS_LIST}
        </ol>
      </main>
    </div>
  )
}
```

## React Vs Svelte Comparison

|Aspect|React|Svelte|
|---|---|---|
|**Data Fetching Hook**|`useEffect`|`onMount`|
|**State Management**|`useState` returns `[value, updater]`|Direct variable assignment|
|**Dependencies**|Explicit dependency array|Automatic reactivity|
|**Re-rendering**|Manual via state updater|Automatic on assignment|
|**Fetch API Usage**|Identical|Identical|

## Key React Concepts

### useEffect Hook

```tsx
useEffect(() => {
  // Side effect code
}, [dependencies]);
```

- Synchronizes React with external systems
- Cleanup happens automatically
- Dependency array controls when effect runs

### useState Hook

```tsx
const [value, setValue] = useState(initialValue);
```

- Returns current value and updater function
- Triggers re-render when updated
- Immutable updates required

## Important Notes

### React Strict Mode

- In development, effects run twice
- Helps identify side effect issues
- Not a bug - it's intentional
- Production builds run effects once

### Common Patterns

**Conditional Requests:**

```tsx
if (track.id !== currentTrack) {
  // Send request only when playing
  window.fetch(url, { method: "POST" });
}
```

**Promise Chaining:**

```tsx
fetch(url)
  .then(response => response.json())
  .then(data => updateState(data));
```

## Workflow Summary

1. **Component mounts** → `useEffect` runs
2. **Fetch data** → GET request to server
3. **Update state** → `updateItems(data)`
4. **React re-renders** → UI updates
5. **User clicks play** → Conditional POST request
6. **Server responds** → Logs action
7. **State updates** → UI reflects change

## Production Considerations

- Add error handling with `.catch()`
- Implement loading states
- Handle cleanup in useEffect return
- Add request cancellation
- Consider using libraries like:
    - React Query / TanStack Query
    - SWR
    - Axios for better error handling
- Implement optimistic updates
- Add request debouncing

## Testing the Implementation

1. Start backend server
2. Note server URL in console
3. Update `serverBaseUrl` in React app
4. Start React dev server
5. Verify data loads automatically
6. Click play buttons
7. Check server console for "Playing..." logs
8. Verify pause doesn't send requests
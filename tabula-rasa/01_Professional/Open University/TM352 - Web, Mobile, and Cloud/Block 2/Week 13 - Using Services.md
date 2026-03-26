---
date created: Friday, December 19th 2025, 12:08:55 pm
date modified: Friday, January 30th 2026, 4:30:44 pm
Gen: "1"
---

# Week 13 - Using Services:

# 1. Introduction:

The goal of this week's module is to learn how web services are integrated into mobile web and React Native applications. This involves exploring backend frameworks that allow services to be constructed in JavaScript, and connecting these services to React apps using asynchronous communication features including Fetch and Promises.

---

# 2. Aims:

**Learning Outcomes:**
- Build a simple web service using ExpressJS
- Explore a web service using Visual Studio Code and Postman
- Use Fetch to connect a React Native application to the service
- Understand asynchronous execution and the use of Promises in JavaScript

---

# 3. Asynchronous Services:

When accessing a web service, a request is sent to a webserver and then a response is received. This takes a short period (normally seconds), but this is enough time for an application to appear unresponsive - annoying users who may think it has crashed.

To avoid this, **asynchronous execution** is utilised, allowing the application to continue responding to user input while waiting for the response.

**Real-world example:** Apps like Facebook show a holding screen (empty message placeholders) while loading data from web services. During this period, the app still responds to user input. Once loaded, data is cached and only reloaded if the app is relaunched or after a short period - this reduces API calls and data costs.

## 3.1. Callback Functions:

Asynchronous functions allow us to schedule a task to be completed while the main program code continues to execute. Once the task is complete, it calls a function with the result - this supplied function is called a **callback function**.

**Example of callback function defined as a variable:**

```javascript
const weatherForecast = function(city, country) {
    if (country == "UK") {
        return "rainy";
    } else {
        return "sunny";
    }
}

const callBack = function(fn) {
    return fn("London", "UK");
}

// Usage: callBack(weatherForecast) returns "rainy"
```

**Alternative: Arrow function syntax:**

```javascript
const callBack = function(fn) {
    return fn("London", "UK");
}

// Using arrow function inline
callBack((city, country) => {
    if (country == "UK") {
        return "rainy";
    } else {
        return "sunny";
    }
})
```

**Asynchronous execution with setTimeout:**

```javascript
const [report, setReport] = useState();

setTimeout(function() {
    setReport(weatherForecast("London", "UK"))
}, 10000); // Executes after 10 seconds
```

The execution continues immediately after `setTimeout`, and the callback is only executed after the specified period.

## 3.2. Promises:

Developers often get confused about asynchronous functions. To overcome this, the concept of a **Promise** was introduced to JavaScript.

A Promise is a JavaScript object with a helpful interface:

- `.then()` - takes a callback function to be called when the Promise completes successfully
- `.catch()` - takes a callback function to be called when there is an error

**Creating a delay function with Promises:**

```javascript
function delay(t) {
    return new Promise(resolve => setTimeout(resolve, t));
}

// Usage with .then()
delay(1000)
    .then(() => setReport(weatherForecast("London", "UK")));
```

## 3.3. Async/Await:

Sometimes you want asynchronous code to appear synchronous for easier reading/debugging. The `async` function declaration allows this when Promises are used - the call to the Promise is prefixed with `await`.

```javascript
const getReport = async function() {
    await delay(1000);
    setReport(weatherForecast("London", "UK"));
}

getReport();
```

**Important notes about async/await:**

1. While it looks synchronous, the code is still executed asynchronously
2. When `await` is hit, code continues to the next line outside the async function before the awaited operation completes
3. The function `getReport` becomes asynchronous in relation to the rest of the application, but lines within it execute synchronously
4. Not all functions can use async (e.g., React's App function)
5. **Common error:** Forgetting to include `await` when calling a function that includes a Promise

---

## 3.4. Using Fetch:

JavaScript provides two asynchronous methods to make web service requests:

1. **XMLHttpRequest** - older, uses callback approach
2. **Fetch** - newer (August 2015), uses Promises, provides additional functionality

**Simple GET request with async/await:**

```javascript
async function fetchExample() {
    const response = await fetch("http://example.com/movies.json");
    const movies = await response.json();
    console.log(movies);
}
```

**Same example without async function:**

```javascript
function fetchExample() {
    fetch("http://example.com/movies.json")
        .then(response => response.json())
        .then(movies => console.log(movies));
}
```

**Key point:** In both versions, `movies` cannot be directly returned as a result of the function because the async operation hasn't completed when the function returns.

---

## 3.5. Handling Errors:

When connecting to a web service, three classes of errors need to be handled:

### 3.5.1. Failures with Fetch:

The call to the web service fails and fetch throws an error. Common causes:

- Connection timeout (device not connected to internet)
- Server being down
- Incorrect IP address or domain

**Handling with try...catch:**

```javascript
async function fetchExample() {
    try {
        const response = await fetch("http://example.com/movies.json");
        const movies = await response.json();
        console.log(movies);
    } catch (error) {
        console.log(error);
    }
}
```

### 3.5.2. Failures with the Server:

The fetch succeeds, but the server returns an error. Check `response.ok` property - if the server responds with a code outside 200-299, this property is `false`.

```javascript
async function fetchExample() {
    try {
        const response = await fetch("http://example.com/movies.json");
        if (!response.ok) {
            console.log("Error accessing service: " + response.status);
        } else {
            const movies = await response.json();
            console.log(movies);
        }
    } catch (error) {
        console.log(error);
    }
}
```

### 3.5.3. Failures with the Web Service:

Web services may provide unexpected output or information in the response itself. This could be due to:

- Design of the service
- Misconfiguration or error in the service
- Unexpected valid output (e.g., no movies listed)

**Solution:** Check the documentation and validate the parsed JSON object before further processing.

### 3.5.4. The Happy Path:

Don't forget to tell the user when the interaction has been successful!

### 3.5.5. Improving the Design:

In real applications, place user interaction code as close to the user interface as possible. This makes code reusable across different platforms.

**Improved design separating concerns:**

```javascript
// Reusable function for web service
async function fetchExample() {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
    if (!response.ok) {
        throw("Error accessing service: " + response.status);
    }
    const movies = await response.json();
    return movies;
}

// User interface function handles all errors
async function userExample() {
    try {
        movies = await fetchExample();
        alert(movies);
    } catch(error) {
        alert(error);
    }
}
```

**Note:** Use `alert` for quick debugging and module assessments - the React Native Alert doesn't work when the app is run in a web browser.

---

# 4. Writing a Service in Express.js:

Express is a fast, unopinionated, minimalist web framework for Node.js. Benefits:

- Quick assembly of simple services
- Built-in scalability of Node.js
- Ideal for example services
- Uses the same JavaScript language as React Native

## 4.1. Basic Express.js Service Structure:

```javascript
const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors());
app.use(express.json());

var weatherReports = {};

const port = 3000;
app.listen(port, () => {
    console.log(`API server listening on port ${port}`);
});

// GET route
app.get('/weather/:city', (request, response) => {
    cityname = request.params.city;
    console.log(`get: City: ${cityname}`);
    response.send({
        city: cityname,
        report: weatherReports[cityname]
    });
});

// POST route
app.post('/weather/:city', (request, response) => {
    cityname = request.params.city;
    report = request.body.report;
    weatherReports[cityname] = report;
    response.send({
        city: cityname,
        report: weatherReports[cityname]
    });
});
```

**Code breakdown:**

- Lines 1-2: Load Node.js modules for Express.js and CORS (uses `require` instead of `import`)
- Line 3: Initialise Express.js
- Lines 5-6: Enable CORS and JSON parsing
- Line 8: JavaScript Map used as a simple in-memory database
- Line 10-12: Define port and start server
- Line 15: Define GET route with `:city` parameter
- Line 24: Define POST route

**Running the service:**

```bash
node app.js
```

## 4.2. Route Template:

```javascript
app.method('/path/:paramname', (request, response) => {
    paramname = request.params.paramname;    // Read URL parameter
    bodyname = request.body.bodyname;        // Read body value
    // Add code to process the input
    response.send({
        name: value
    });
});
```

Replace `method` with the required HTTP method (get, post, put, delete). Use `:` prefix for URL parameters.

---

## 4.3. Experimenting with a Web Service:

Unlike FastAPI, Express.js has no built-in documentation generator. Third-party tools are required:

### 4.3.1. Using VS Code (REST Book Extension):

REST Book is a VS Code extension that allows exploration of REST web services.

### 4.3.2. Using Postman:

Postman is a commercial tool (free version available) for exploring REST APIs.

**Key Postman features:**

- Import/export API collections
- Set query parameters
- Configure body data (raw JSON, form-data, etc.)
- View response data

**Nominatim Service:** A geocoding service that converts location names/addresses into latitude and longitude coordinates.

**Warning:** Nominatim has a strict usage policy - if you send lots of requests or more than one request per second, your IP address will be blocked.

---

# 5. React Native:

React Native provides a library alongside standard JavaScript functions. Since web browsers provide suitable functionality via `fetch`, there's no additional React Native functionality for handling services directly - the same approach works for React, Svelte, or any other JavaScript framework.

## 5.1. Using a Web Service:

### 5.1.1. Imports:

```javascript
import { Button, Text, View, TextInput } from 'react-native';
import React, { useState } from 'react';
```

No additional libraries required for REST web services - they use standard JavaScript features.

### 5.1.2. App Function:

```javascript
export default function App() {
    const [report, setReport] = useState('');

    return (
        <View>
            <Text>The weather in London is {report}</Text>
            <Button
                title="Check weather in London"
                onPress={check}
            />
            <Text>Submit a weather report</Text>
            <TextInput onChangeText={text => setReport(text)} />
            <Button
                title="Submit weather in London"
                onPress={submit}
            />
        </View>
    );
}
```

**Important:** The App function cannot be set to async because it must return the JSX definition of the user interface. If defined as async, it would return a Promise object instead.

### 5.1.3. Event Handling Functions:

Separate async functions are needed to integrate with the web service:

```javascript
const check = async function() {
    try {
        setReport(await getWeather('london'));
    } catch (error) {
        alert(error);
    }
}

const submit = async function() {
    try {
        await setWeather('london', report);
    } catch (error) {
        alert(error);
    }
}
```

These "glue" functions use the report state hook with reusable web service functions. Errors are reported using `alert`.

### 5.1.4. Using a GET Verb:

```javascript
async function getWeather(city) {
    const response = await fetch(base + "/weather/" + city);
    if (!response.ok) {
        const message = "An error has occurred: " + response.status;
        throw(message);
    }
    const json = await response.json();
    return json.report;
}
```

GET is the default verb for fetch, so only the URL is needed.

### 5.1.5. Using a POST Verb:

```javascript
async function setWeather(city, report) {
    const details = {
        "report": report
    };

    const response = await fetch(base + "/weather/" + city, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(details)
    });

    if (!response.ok) {
        const message = "An error has occurred: " + response.status;
        throw(message);
    }
    const json = await response.json();
    return json.report;
}
```

**Key differences from GET:**

- An options object is required as the second argument
- `method`: specifies the HTTP verb (POST)
- `headers`: content type is 'application/json'
- `body`: the data being sent, converted using `JSON.stringify()`

---

## 5.2. Improving the Design:

Three improvements can be made for better maintainability and code reuse:

1. **Convert to TypeScript** - identifies hidden errors, provides better IDE hints
2. **Separate web service code** - place in a reusable library file
3. **Create custom components** - allows easy reuse across multiple locations/screens

### 5.2.1. WeatherService.ts:

```typescript
type WeatherReport = {
    report: string;
    city?: string;  // ? indicates optional
};

export async function getWeather(city: string): Promise<string> {
    const response: Response = await fetch("http://localhost:3000/weather/" + city);
    if (!response.ok) {
        const message: string = "An error has occurred: " + response.status;
        throw(message);
    }
    const json: WeatherReport = await response.json();
    return json.report;
}
```

**Key points:**

- Type definition describes the WeatherReport JSON object
- `export` statement makes functions importable
- Types added to arguments, constants, and functions
- Async function returns a `Promise<string>` even though it appears to return a string
- File extension is `.ts` (no JSX content)

### 5.2.2. WeatherView.tsx:

```typescript
import { Text, Button, View } from 'react-native';
import React, { useState } from 'react';
import { getWeather } from '../libraries/WeatherService';

type WeatherViewProps = {
    city: string;
};

const WeatherView = function(props: WeatherViewProps) {
    const [report, setReport] = useState('');

    const check = async function() {
        try {
            setReport(await getWeather(props.city));
        } catch (error) {
            alert(error);
        }
    }

    return (
        <View>
            <Text accessibilityLiveRegion="polite">
                The weather in {props.city} is {report}
            </Text>
            <Button
                title={"Check weather in " + props.city}
                onPress={check}
            />
        </View>
    );
};

export default WeatherView;
```

**Import notation:** `..` moves up a directory. Example: `'../libraries/WeatherService'` means go up one directory, then into libraries folder. File extensions (.ts, .tsx, .js) are assumed.

### 5.2.3. App.jsx:

```javascript
import { Button, Text, View, TextInput, StyleSheet } from 'react-native';
import React, { useState } from 'react';
import { setWeather } from './libraries/WeatherService';
import WeatherView from './components/WeatherView';

export default function App() {
    const [report, setReport] = useState('');

    const submit = async function() {
        try {
            await setWeather('london', report);
        } catch (error) {
            alert(error);
        }
    }

    return (
        <View style={styles.container}>
            <WeatherView city="london" />
            
            <Text accessibilityRole="text">Submit a weather report</Text>
            <TextInput 
                accessibilityLabel="Submit a weather report" 
                onChangeText={text => setReport(text)} 
            />
            <Button
                title="Submit weather in London"
                onPress={submit}
            />
        </View>
    );
}
```

**Benefits of this structure:**

- WeatherView component can be reused for multiple cities
- Web service functions can be shared across React web and React Native apps
- TypeScript catches errors at development time
- Clear separation of concerns

---

# 6. Summary:

In this part we learned about:

- Using the 'Fetch' command to make web requests
- Handling asynchronous execution in JavaScript (callbacks, Promises, async/await)
- Developing web services using ExpressJS
- Exploring web services using VS Code REST Book and Postman
- Integrating web services into React Native applications
- Improving code structure through TypeScript, separation of concerns, and custom components

**Key takeaways:**

- Asynchronous execution prevents apps from freezing while waiting for responses
- Promises provide a cleaner interface than callbacks
- Async/await makes asynchronous code look synchronous
- Three types of errors need handling: fetch failures, server errors, service errors
- TypeScript helps identify errors and improves maintainability
- Separate concerns between UI code and service code for reusability

---

# 7. Further Reading:

- [MDN: Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [MDN: Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [Express.js Documentation](https://expressjs.com/)
- [Postman Getting Started Guide](https://learning.postman.com/docs/getting-started/introduction/)
- [Nominatim Documentation](https://nominatim.org/release-docs/latest/)

---
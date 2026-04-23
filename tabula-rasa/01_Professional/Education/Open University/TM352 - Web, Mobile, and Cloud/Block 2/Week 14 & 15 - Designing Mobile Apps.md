---
date created: Friday, December 19th 2025, 12:08:55 pm
date modified: Friday, January 30th 2026, 4:34:24 pm
Gen: "1"
---

# Week 14-15 - Designing Mobile Apps:

# 1. Introduction:

In these weeks you will learn how to design and build a functional and fully featured mobile app using TypeScript. This includes requirements analysis, implementing business logic, using React Native libraries for mobile-specific features (GPS, camera), and exploring AI code assistants.

Additionally, you'll learn about documentation generation with TypeDoc and testing with Jest.

---

# 2. Aims:

**Learning Outcomes:**

- Define functional requirements and decompose them into design parts for implementation
- Understand the basic usage of React Native Libraries and their role in bridging JavaScript/TypeScript programs with Android/iOS platform-specific APIs
- Understand the differences between consuming services and consuming data
- Understand how to use AI tools to produce code and their limitations
- Use TypeDoc to generate documentation for your code
- Understand testing with Jest in React Native Expo projects

---

# 3. App Requirements and Design:

## 3.1. Requirements Analysis:

Mobile apps inherit general software development models but address unique user needs that differ from desktop applications. The typical needs for mobile apps can be broadly characterised into:

1. **Monitoring context of use** through sensors (cameras, GPS, accelerometers, etc.)
2. **Specialising in a single domain** with unique functionality to stand out from millions of apps
3. **Collaborating with other apps or online services** for common functionalities

### Finding a Niche:

The key to analysing whether a mobile requirement is worthy of development is through research on app stores for similar apps. You should:

1. Search app stores using keywords associated with your mobile requirement idea
2. Create a **feature table** comparing candidate apps
3. Identify gaps that may be worth further development

**Example Feature Table (Running Timer Apps):**

|App|Timer|Running|Map|Photo|
|---|---|---|---|---|
|Interval Timer|Yes|Yes|No|No|
|Runtastic Workout|Yes|Yes|No|No|
|Runtastic Running|Yes|Yes|Yes|No|
|Running Distance Tracker+|Yes|Yes|Yes|No|
|StopWatch & Timer|Yes|Yes|No|No|
|WalknRun|Yes|Yes|No|No|

**Key insight:** A feature gap identified may not necessarily be a niche (e.g., does a running timer app really need to take photos?). Sometimes less is more in app development.

### Functional Vs Non-Functional Requirements:

- **Functional requirements (FRs):** Mandatory features the app must have to meet users' needs
- **Non-functional requirements:** Quality attributes like usability, customisability, responsiveness - these subtle differences are important when making design choices

**Example Functional Requirements for a Running/Walking Timer App:**

|FR|Name|Description|Obstacle|
|---|---|---|---|
|FR1|Timer start|Reset clock to 0, activate and display elapsed time upon 'Start'|Application may not be given run time for accurate updates|
|FR2|Timer stop|Stop clock and display final elapsed time upon 'Stop'|Delay between button press and code stopping timer|
|FR3|Initialisation|Display description of user's current geolocation|GPS signal may not be available indoors|
|FR4|Achievement|Take photo using camera when timer stopped|Application may not have camera permission|

---

## 3.2. Design and Development:

### Model-View-Controller (MVC) Pattern:

Web applications typically follow the MVC pattern:

- **Model:** The business logic and data store, operated by the controller
- **View:** The presentation to users, updated by the model (data output)
- **Controller:** Listens for user input and forwards it to the model (data input)

Different frameworks adapt this pattern in different ways. It may also be duplicated with a local model on a device and a remote model as part of a web service.

### Flux Architecture:

React famously stated "React isn't an MVC framework", but patterns within MVC architecture (Observer, Composite, Strategy) are central to how React and React Native allow developers to build applications at scale.

**Key patterns in React:**

1. **Composition Pattern:** Combining components together. Basic components in React are HTML tags; in React Native, they're native widgets
2. **Façade Pattern:** Implemented through Props, allowing abstraction and reusable blocks of UI functionality

**Flux's main innovation:** Ensures changes in the data model are handled such that consistency is maintained across updates that might otherwise suffer race conditions (where different components independently attempt to update values in contradictory ways).

---

## 3.3. Creating the View with JSX:

Presentational design includes implementing the app's view (user interface design). For mobile apps, users have additional means of interaction beyond just the screen.

**For the timer app UI, we need:**

- Controls for 'starting' (FR1) and 'stopping' (FR2) the timer
- Display for timer updates showing running/walking progress
- Display for street address of device location (FR3)
- Display for photo taken at destination (FR4)

### UI Skeleton Steps:

1. Add `Image` and `Button` to the import statement
2. Add required `Button`, `Text`, and `Image` components to the View
3. Place Start and Stop buttons in a View with `flex-direction: row` to sit side by side
4. Set Image style with height and width

**Mock-up UI structure:**

```
┌─────────────────────┐
│   Start Location    │
├─────────────────────┤
│       00:00         │
├──────────┬──────────┤
│  Start   │   Stop   │
├──────────┴──────────┤
│                     │
│      [Photo]        │
│                     │
├─────────────────────┤
│    Take Photo       │
└─────────────────────┘
```

---

## 3.4. Creating the Business Logic:

React Native implements business logic in JavaScript/TypeScript, unlike native apps in Java (Android) or Objective-C/Swift (iOS). TypeScript helps catch errors and provides better IDE hinting.

**File extensions:**

- `.tsx` - If the file contains embedded JSX (code that looks like HTML) as part of a component
- `.ts` - For TypeScript files without JSX

### Understanding Classes and Objects:

A simplistic view:

- **Classes:** Prototypes or recipes to create objects (instances of classes)
- **Objects:** Specific instances with populated properties

**Example:** An "office chair" class describes common properties (is wheeled, adjustable back, colour). An object describes a specific chair (no wheels, adjustable with Allen key, purple colour). Classes bundle properties with functions like `adjustBack()`.

**Note:** JavaScript doesn't implement classes the same way as Java, though principles are similar. JavaScript is at its core a functional language.

### Stopwatch Implementation Structure:

To implement business logic:

1. Create a `libraries` directory for business logic files
2. Create a `components` directory for presentation files
3. Separate the stopwatch logic (Stopwatch.ts) from the view (StopwatchView.tsx)

---

# 4. Mobile-Specific Development:

The major difference between React Native apps and web apps lies in mobile-specific parts - sensors (GPS) and devices (cameras). React Native hybridises underlying mobile platforms by interfacing platform-dependent APIs with platform-independent JavaScript APIs.

## 4.1. Mobile APIs:

React Native provides platform independence by hybridising web programming with mobile platform-specific libraries.

**Without React Native, you would need:**

- **iOS:** Swift using Apple's Programming Guide for camera API
- **Android:** Java using Android Developers Camera API documentation, plus manifest permissions:

```xml
<uses-permission android:name="android.permission.CAMERA" />
```

React Native abstracts this complexity - developers only need to write JavaScript or TypeScript.

---

## 4.2. React Native Libraries:

Using plugins makes app creation modular:

- Only include code libraries for functionality you need
- Helps control app size
- Users more inclined to download smaller apps

**Installing a library:**

```bash
npx expo install expo-camera
```

---

## 4.3. Using Library APIs:

Once installed, library APIs can be accessed "natively" through JavaScript APIs. This provides the "write once, run everywhere" capability.

**Camera Plugin Example (FR4):**

- Allow user to take photo by pressing "Take Photo" button
- User controls timing rather than automatic photo when timer stops

---

# 5. Completing the Exercise Tracker App:

## 5.1. Adding Geolocation:

Use the `expo-location` library for implementing FR3 (display start location).

**Installation:**

```bash
npx expo install expo-location
```

**Key considerations:**

- Chrome may ask permission for the page to "know your location" - click Allow
- If location is never reported or you see "Permission to access location was denied", use Chrome developer tools to set a geolocation using the sensors tab

### Location Tracking Strategy:

For the running app:

1. Track the device's location over time
2. Location may be `undefined` initially while GPS sensor obtains location
3. Useful to track until a real location is found
4. Could be extended for a map feature and distance calculation

---

# 6. Summary (Part 7):

What you've learned is an example iteration of incremental mobile app development:

1. Identify a functional requirement
2. Implement it to your project's code base
3. Repeat for all requirements

**Key points:**

- Fully featured apps typically have dozens of functional requirements
- Don't develop everything from scratch - many useful web services exist
- Web services can identify user location and provide other functionality
- This is different from just consuming data

---

# 7. Exploring AI Code Assistants:

Language models are a class of AI based on the probability of words and phrases being associated with each other. They are trained on large amounts of public or private data.

**Important considerations:**

- They reflect biases and mistakes in source material without understanding
- May generate code with errors, particularly security issues not immediately obvious
- May produce offensive results (though providers actively filter these)

## 7.1. Ethics and Learning to Code:

AI code assistants raise many ethical dilemmas:

- As AIs become more powerful and replace human roles, significant workplace changes will occur
- BT announced in 2023 that 55,000 jobs would be lost before end of decade, with a fifth to AI tools

---

## 7.2. GitHub Copilot:

GitHub Copilot is a language model based on Codex from OpenAI, trained on GitHub code.

**Purpose:** Spend less time on boilerplate and repetitive code, allowing focus on novel elements.

**How it works:**

- Developer begins writing a comment or code
- Tool suggests the next line of code
- Developers accept suggestions ~26% of the time
- ~27% of final code file generated by Copilot

**Risks:**

- Trained on varying quality code with limited scope
- Many errors will be generated, some subtle but dangerous
- **Plagiarism risk:** ~1% for sections longer than 150 characters (filter available)

**Key insight:** Copilot is correctly marketed as an assistant to a trained developer, not a replacement.

---

## 7.3. OpenAI Codex:

The technology behind GitHub Copilot. Unlike Copilot, Codex focuses on providing a block of code at a time by passing instructions describing what you want.

---

## 7.4. ChatGPT:

ChatGPT is a conversational AI where users provide prompts for the AI to answer, with ability to ask follow-on questions.

**Advantages over Copilot:**

- Can tell it to create code for you
- Can create entire applications with little input
- Can explain code it produces (or code you provide)

**Limitations:**

- Not connected to internet (factual information often outdated)
- Prone to making up facts
- Generated code may have errors requiring human interaction

---

## 7.5. ChatGPT Transcript Example:

**Request:** "Design a React Native mobile app for runners to time their run"

**ChatGPT's suggested features:**

1. User authentication (email, Google, Apple)
2. Home screen with 'Start Run' button and run history
3. Running tracker (timer, GPS distance, pause/stop)
4. Run history (date, duration, distance, path)
5. Run statistics (total distance, time, average pace)
6. Settings (units, audio cues)
7. Social sharing
8. Accessibility and UI/UX
9. Offline support
10. In-app purchases (optional)
11. Privacy and data security
12. Testing and bug fixes

**Generated directory structure:**

```
RunTimer/
├── src/
│   ├── components/
│   │   ├── Timer.tsx
│   │   ├── RunHistory.tsx
│   │   └── RunStats.tsx
│   ├── screens/
│   │   ├── HomeScreen.tsx
│   │   ├── RunScreen.tsx
│   │   └── RunHistoryScreen.tsx
│   ├── navigation/
│   │   └── AppNavigator.tsx
│   └── utils/
│       ├── authService.ts
│       └── runService.ts
├── App.tsx
├── types.ts
├── package.json
└── tsconfig.json
```

**Example Timer.tsx from ChatGPT:**

```typescript
import React, { useState, useEffect } from 'react';
import { Text, View, TouchableOpacity } from 'react-native';

const Timer: React.FC = () => {
    const [isRunning, setIsRunning] = useState(false);
    const [seconds, setSeconds] = useState(0);

    useEffect(() => {
        let interval: NodeJS.Timeout;
        if (isRunning) {
            interval = setInterval(() => {
                setSeconds((prevSeconds) => prevSeconds + 1);
            }, 1000);
        }
        return () => {
            clearInterval(interval);
        };
    }, [isRunning]);

    const handleStartStop = () => {
        setIsRunning((prevIsRunning) => !prevIsRunning);
    };

    const handleReset = () => {
        setSeconds(0);
    };

    return (
        <View>
            <Text>Time: {seconds} seconds</Text>
            <TouchableOpacity onPress={handleStartStop}>
                <Text>{isRunning ? 'Pause' : 'Start'}</Text>
            </TouchableOpacity>
            <TouchableOpacity onPress={handleReset}>
                <Text>Reset</Text>
            </TouchableOpacity>
        </View>
    );
};

export default Timer;
```

---

## 7.6. State of the Art:

AI is a fast-moving area - tools will have further developed since writing. Developers keep up by:

- Trying out new tools
- Following tech news sources
- Evaluating tools as they develop

---

## 7.7. AI Summary:

**Key takeaways:**

- Language models are transforming code creation
- Can generate significant design, code, and documentation
- **Risks include:** security issues, unexpected biases
- Used effectively, they can reduce software development costs
- Human developers are still needed, particularly for novel solutions
- Skill is in taking provided code, correcting issues, implementing missing features, and testing

---

# 8. Using TypeDoc:

TypeDoc generates documentation for TypeScript code using specially formatted comments.

**Installation:**

```bash
npm install typedoc --save-dev
```

**Comment format (similar to JavaDoc):**

```typescript
/**
 * A queued/cached call to the OpenStreetMap REST API to look up a location.
 * See: https://nominatim.org/release-docs/develop/api/Search/
 * This is a Promise based function that returns a promise resolving to parsed JSON.
 *
 * @param address - the address to look up
 * @returns the JSON response from nominatim
 *
 * @author Autumn Thomson
 * @version 2.0 July 2023
 */
```

**Key elements:**

- Comments immediately above the item to be documented
- Start with `/**`
- Include description
- `@param` tags for each parameter
- `@returns` tag for return value
- Optional tags like `@author`, `@version`

TypeDoc generates entries for public and exported items (functions, types, variables, classes) listed in `tsconfig.json` entry points.

---

# 9. Introduction to Jest in React Native Expo Projects:

Jest is a widely adopted JavaScript testing framework known for simplicity, speed, and powerful features. Developed and maintained by Meta (formerly Facebook).

## 9.1. Role of Testing in Software Development:

Testing serves multiple purposes:

- Verifies code behaves as expected
- Prevents regressions
- Facilitates refactoring

**Testing types:**

- **Unit testing:** Focuses on individual components/functions
- **Integration testing:** Examines interactions between components
- **Snapshot testing:** Captures rendered output and compares against stored reference

TM352 mostly uses Jest for **integration testing** - ensuring code in different components works together as expected. Also uses **static analysis** to look for partial implementations (inspects code without running it).

---

## 9.2. Overview of Jest:

Jest is a zero-configuration testing framework supporting:

### Mocking:

Provides alternative implementation of complex components during testing. Useful for testing UIs without testing third-party components.

### Code Coverage Analysis:

Checks that all code paths have been tested. Helps identify unreachable code. Does not identify edge cases - boundary tests still important.

### Parallel Test Execution:

Important for large projects as testing can take long. Allows tests to execute using multiple threads.

**Basic Jest syntax:**

```typescript
test('adds 1 + 2 to equal 3', () => {
    expect(1 + 2).toBe(3);
});

// Equivalent using 'it':
it('should add 1 + 2 to equal 3', () => {
    expect(1 + 2).toBe(3);
});
```

**Test file organisation:** Place tests in `__tests__` directory or alongside components they test.

---

## 9.3. Setting Up Jest in an Expo Project:

**Installation:**

```bash
npx expo install jest-expo jest @types/jest --dev
```

**package.json configuration:**

```json
"jest": {
    "preset": "jest-expo"
}
```

**Note:** Additional configuration like `transformIgnorePatterns` may be required to transpile third-party modules.

---

## 9.4. Writing Unit and Snapshot Tests:

### Unit Tests with React Native Testing Library:

```typescript
import { render } from '@testing-library/react-native';
import HomeScreen from './HomeScreen';

test('renders welcome message', () => {
    const { getByText } = render(<HomeScreen />);
    getByText('Welcome!');
});
```

- `render` causes the component to be rendered
- Returns functions like `getByText` to search the component

### Snapshot Tests:

```typescript
import renderer from 'react-test-renderer';
import HomeScreen from './HomeScreen';

test('matches snapshot', () => {
    const tree = renderer.create(<HomeScreen />).toJSON();
    expect(tree).toMatchSnapshot();
});
```

- First run stores snapshot under `__snapshots__/HomeScreen.test.tsx.snap`
- Subsequent runs compare against stored snapshot
- Update snapshots with `jest --updateSnapshot`

**Warning:** Excessive reliance on snapshots can lead to brittle tests that easily fail when UI changes.

---

## 9.5. Mocking:

Jest's mocking capabilities isolate components and simulate external dependencies:

```typescript
jest.mock('react-native-video', () => 'Video');
```

This replaces actual implementation with a **stub** - a simplified implementation used during testing to isolate the unit being tested.

---

## 9.6. Code Coverage:

Enable code coverage in Jest configuration:

```json
"jest": {
    "collectCoverage": true,
    "collectCoverageFrom": [
        "**/*.{ts,tsx,js,jsx}",
        "!**/node_modules/**"
    ]
}
```

Generates HTML reports visualising coverage metrics.

---

## 9.7. Interpreting Jest Output:

**Running tests:**

```bash
npm run test                    # Run all tests
npm run test App.test.jsx       # Run specific test suite
npx jest                        # Alternative if package.json not configured
```

**Successful output shows:**

- PASS for each test file
- Number of test suites and tests passed
- Time taken

**Failed output shows:**

- FAIL for the failing test file
- Name of the test that failed
- Error encountered
- Rendered component
- Code of the failing test

This information helps developers locate and fix errors - they may need to correct the test or the component under test.

---

## 9.8. Use in TM352:

- Activities in Block 2 have Jest tests for verification
- Module team uses tests to ensure VCE continues to operate as expected
- TMA 02 uses Jest tests to assign grades
- Tests help guide learning without relying on Generative AI

---

## 9.9. Jest Summary:

**Key takeaways:**

- Testing ensures code is reliable and maintainable
- Critical in mobile environments where consistency across devices matters
- Unit, integration, and snapshot testing verify behaviour and detect regressions
- Mocking, code coverage, and parallel execution make testing efficient
- Understanding Jest output helps debug failing tests

---

# 10. Summary (Part 8):

**What you've learned:**

- How AI can create program code
- AI tools will disrupt the computing industry significantly
- Human developers still needed for novel solutions
- Documentation and maintainability are important skills
- TypeDoc creates useful documentation with minimal effort
- Jest provides comprehensive testing capabilities for React Native

**Key insight for assessments:** The skill of the developer is to take provided code, correct any issues, implement missing features, and test it to ensure it meets the specification.

---

# 11. Further Reading:

**AI and Coding:**

- ACM Digital Library: "The robots are coming: exploring the implications of OpenAI codex on introductory programming" by Finney-Ansley et al. (2022)
- TechCrunch: "Code-generating AI can introduce security vulnerabilities, study finds"
- Wall Street Journal: "AI-Powered coding assistant aims to help, not replace developers"

**Testing:**

- Jest Documentation: <https://jestjs.io/>
- Expo Unit Testing Guide: <https://docs.expo.dev/develop/unit-testing/>
- React Native Testing Library: <https://github.com/callstack/react-native-testing-library>

**TypeDoc:**

- TypeDoc Documentation: <https://typedoc.org/>

---
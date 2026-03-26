---
date created: Friday, December 19th 2025, 12:08:55 pm
date modified: Friday, January 30th 2026, 4:13:13 pm
Gen: "1"
---

# Week 10 - React Native Mobile Apps:

## 1. Introduction:

This week builds on the React Native development environment setup from Week 8 and the concepts learned with React in Block 1. The focus is on developing a basic mobile application that can be run in a browser, emulator, Expo Go app, or compiled directly for a device.

While TM352 doesn't go deeply into practical app development due to study time constraints, completing this week should provide a firm understanding of the major concepts that will make other documentation accessible. The TMA 02 assignment requires building a mobile app using React Native.

**Note:** Running the application on a physical device often provides the most satisfaction, so if this route is available, it is strongly recommended.

---

## 2. Aims:

**Learning Outcomes:**
- Understand how simple web applications are developed for a mobile platform
- Install and run a mobile app
- Create custom components in React Native
- Apply stylesheets to style mobile app components
- Use libraries to extend app functionality
- Understand accessibility considerations for mobile apps
- Use browser developer tools to simulate mobile devices

---

## 3. Building Your First Application:

Before proceeding, ensure you have completed Block 2 Part 1, Activity 3 which covers creating your first React Native application.

**Running the App:**
- If using the VCE: Go to Block 2 activities
- If running locally: Open command line, navigate to project directory with `cd`, then run `npm run start`
- Once Metro is waiting, press `w` to launch the app in your web browser
- Optionally, to run on your phone: Install Expo Go on your mobile device, then scan the QR code shown in the terminal after running `npm run start`

**Development Tip:** You can make changes to your application whilst it is running. This is a productive development technique - making small changes and verifying the app still works helps avoid making big changes and being unsure what caused a failure.

**Important:** Expo and React Native release new versions quarterly, so module material can quickly fall out of date. Use the provided forum with other students to collaboratively identify changes required to instructions. The Expo documentation is recommended throughout the block.

### 3.1. Anatomy of React Native Apps:

A basic React Native application structure (from App.jsx):

```javascript
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

**Key Components:**
- **Lines 1-2:** Import relevant libraries from Expo and React Native. Additional libraries are added as more functionality is required.
- **Lines 4-11:** Define what happens when the app starts. Uses JSX formatting (encountered in Block 1). The `{curly braces}` define values read from JavaScript.
- **Lines 13-20:** Define styles using `StyleSheet.create()`.

**Libraries Used:**
- `StatusBar` - Part of Expo, sets up a status bar for the application
- `StyleSheet` - From React Native, used to style the UI similar to CSS
- `Text` - From React Native, similar to the `<p>` tag in HTML
- `View` - From React Native, allows components to be grouped together, similar to `<div>` in HTML

**Note:** All TM352 examples use a single screen, but React Native supports multiple screens in a single application.

---

### 3.2. Using Components:

React Native allows mobile apps to be built from core components. These are similar to React components but relate to typical widgets seen in native mobile apps.

**Common React Native Components:**

|Component|HTML Equivalent|Description|
|---|---|---|
|`<View>`|`<div>`|A container that supports layout|
|`<Text>`|`<p>`|Displays strings of text|
|`<Image>`|`<img>`|Displays images|
|`<ScrollView>`|`<div>`|A scrolling container|
|`<TextInput>`|`<input type="text">`|Allows the user to enter text|

A typical screen layout consists of a `View` with several components placed on it. For applications requiring multiple screens, multiple views can be used and navigated between.

**Extension:** React Native components can respond to touch events and gestures. Review the React Native documentation on interaction for more detail (beyond TM352 scope).

#### 3.2.1. Custom Components:

Custom components reduce code duplication, just as in React from Block 1. They are composed of several components on a View (either core components or other custom components).

**Example: Weather Component**

```javascript
import {Text, View} from 'react-native';

const Weather = (props) => {
  return (
    <View>
      <Text>
        The weather in {props.city}, is {props.weather}.
      </Text>
    </View>
  );
};

export default Weather;
```

**Breakdown:**

- **Line 1:** Imports relevant libraries - each library used in the component must be included
- **Line 3:** Defines the component with `props` parameter. Props values used are `props.city` and `props.weather`
- **Lines 4-10:** Define the component's appearance by composing `View` and `Text` components. JSX allows values to be written including the city name and weather report
- **Line 13:** Exports the Weather component, making it visible to any code that includes it

**Note:** Components can wrap up more complex operations to make them easier to use. The Weather component will be expanded later to use a service.

---

### 3.3. Using Stylesheets:

React Native uses stylesheets to style components. The style formatting and options typically follow CSS conventions from Block 1.

**Key Difference:** Names are written using camelCase instead of kebab-case:

- CSS: `background-color`
- React Native: `backgroundColor`

**Example StyleSheet:**

```javascript
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  weatherText: {
    fontSize: 18,
    color: '#333',
    padding: 10,
  },
});
```

**Applying Styles:**

```javascript
<View style={styles.container}>
  <Text style={styles.weatherText}>Weather information here</Text>
</View>
```

---

### 3.4. Using Libraries:

Libraries provide additional functionality to a React Native app, offering additional components or reusable functions. They help produce apps quickly and maintain them more easily by reusing code.

**Finding Libraries:** The React Native Directory (<https://reactnative.directory/>) provides a central point to discover existing libraries.

**TM352 Recommendation:** Only use libraries included in Expo Go that work with the web target. This ensures:

- Ability to follow provided instructions
- Tutors can mark work using provided environments

**To find appropriate plugins:**

1. Go to React Native Directory
2. Click the 'filters' button
3. Check the 'web' and 'expo go' filters
4. Use the search box to narrow down choices

**Installing Libraries:** Libraries need to be installed locally as part of your development environment. For example, to include the expo-camera library:

```bash
npx expo install expo-camera
```

**Choosing Libraries - Considerations:**

- Number of downloads/popularity
- Maintenance status (recently updated?)
- Documentation quality
- Community support
- Compatibility with your Expo version

---

### 3.5. Accessibility:

Both Apple and Google have invested significant effort making their platforms and apps accessible. However, there is no universal standard for mobile app accessibility, meaning features are implemented differently on each platform.

**React Native Accessibility:**

- Implemented through props of components
- Many properties are platform-specific, requiring variety of props for different platforms and user needs
- By default, applications implement key accessibility requirements
- Props follow similar approach to web accessibility (from Block 1)

**Key Accessibility Props:**

- `accessible` - When true, indicates the view is an accessibility element
- `accessibilityLabel` - Text read by screen readers
- `accessibilityHint` - Helps users understand what will happen when they perform an action
- `accessibilityRole` - Communicates the purpose of a component

**Testing Accessibility:**

- **Android:** Use TalkBack
- **iOS:** Use VoiceOver

**Evaluation Questions:**

- Can you navigate the app with your eyes closed?
- What features make navigation easier or harder?
- What recommendations would you make to developers?

---

## 4. Web Browsers:

Mobile web browsers were derived from desktop browsers but grew into unique products due to low-energy profiles and limited screen sizes. Mobile browsers handle additional user interactions and device sensor inputs (e.g., portrait/landscape orientation via accelerometers).

The mobile browser market is constantly changing. Browsers are built on a smaller number of rendering engines - for example, the open-source WebKit engine (Safari) is gaining popularity.

### 4.1. Practical Activity: Simulating Mobile Browsers in Google Chrome:

Chrome Developer Tools (DevTools) provides a useful simulator to mimic screen width, resolution, and input methods of various mobile devices. This is convenient for testing without requiring physical devices and works with both mobile websites and React Native apps running in the browser.

#### 4.1.1. Getting Started with Device Mode:

**Opening DevTools:**
1. Open the [OU website](www.open.ac.uk) in Google Chrome
2. Click the three vertical dots (⋮) at top right → More tools → Developer tools
3. Or use keyboard shortcuts:
    - Windows: `Ctrl+Shift+I`
    - Mac: `Cmd+Opt+I`

**DevTools Layout:**
- Browser window splits into two panels (web page and DevTools interface)
- Customise layout by clicking the vertical ellipsis (⋮) in DevTools → Dock side
- Options: undocked, docked bottom, docked left, docked right
- Large widescreen: docked right often preferred
- Narrow display: docked bottom may be better

**Toggling Device Mode:**
1. In DevTools menu, ensure 'Elements' tab is selected
2. Click the device toolbar icon (to the left of 'Elements')
3. Device mode menu appears at top of main browser panel
4. Default is 'Responsive' - allows resizing to any dimensions
5. Click dropdown to select preset devices (e.g., iPhone 6)
6. Rotation icon allows switching between portrait and landscape

#### 4.1.2. Adding Your Own Simulated Mobile Device:

**To add a custom device:**
1. Open DevTools and enable device mode
2. Click device dropdown → Edit...
3. Click 'Add custom device...'
4. Enter device details:
    - Device name (descriptive)
    - Width and height (in portrait mode)
    - Device pixel ratio
    - User agent string

**Finding Device Specifications:**

- Visit mydevice.io on your device to detect settings
- Or use Blisk browser website for device capability lists
- Search for `user agent string <device name>` to find user agent

**Example - Galaxy Note 4:**

- Resolution: 360 × 640
- Pixel density: 4
- User agent string: `Mozilla/5.0 (Linux; Android 4.1.2; GT-N7100 Build/JZO54K) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/29.0.1547.72 Mobile Safari/537.36`

**Note:** If pixel ratio > 1, divide resolutions by pixel ratio before inputting.

**User Agent Strings:** Mobile device simulation works by sending a spoof mobile user agent string. This is why sites like YouTube redirect to their 'm.' mobile version when using device mode.

Example mobile user agent format:

```
Mozilla/5.0 (Linux; <Android Version>; <Build Tag etc.>) AppleWebKit/<WebKit Rev> (KHTML, like Gecko) Chrome/<Chrome Rev> Mobile Safari/<WebKit Rev>
```

#### 4.1.3. Network Throttling:

Network throttling simulates different network conditions mobile devices experience when not on WiFi. Mobile networks typically have lower bandwidth and higher latency than WiFi, resulting in slower page loading.

**Accessing Network Throttling:**
1. In DevTools, go to 'Network' tab
2. Find 'Network conditions' in the pull-down menu (usually shows 'Online')
3. Select different conditions:
    - Online (default)
    - Fast 3G
    - Slow 3G
    - Offline

**Testing:**
- Select 'Slow 3G' and load a content-heavy website (e.g., The Guardian)
- Notice significantly slower loading, especially for images

**Closing DevTools:** Click the close icon (X) at the extreme right of the DevTools menu.

---

### 4.2. Mobile Emulators:

Device mode in Chrome simulates mobile browsers, but emulators provide an even closer experience. An emulator is a desktop application that executes the exact same code as a mobile device, including running the exact same web browser.

**Available Emulators:**
- **iOS:** Xcode IDE includes iOS Simulator (Mac only)
- **Android:** Android Studio includes Android Emulator, Genymotion (third-party)

**Emulator Drawbacks:**
- Very resource intensive
- Require powerful processor and at least 6GB RAM
- Can take several minutes to initialise
- Can be tricky to set up (hardware/OS requirements)

**TM352 Approach:** Expo Snack provides access to an emulator without local setup, and Expo Go allows running apps on real devices. This approach provides mobile context with minimum hassle.

**Extension Activity:** If time permits, Android Studio (from Google) includes both an emulator and native development environment. Be warned: getting the emulator running can be challenging and time-consuming.

---

## 5. Summary:

This week covered:
- Creating a simple mobile app using React Native
- Understanding React Native app anatomy (imports, components, stylesheets)
- Building custom components
- Using stylesheets for styling
- Extending functionality with libraries
- Accessibility considerations
- Testing with Chrome DevTools device mode
- Understanding mobile emulators

**Important:** If you struggled to get the development environment working, contact your tutor now as this is essential for TMA and EMA.

In a future part, you will learn how to integrate a service and store data in your app.

### 5.1. Next Steps Beyond TM352:

TM352 aims to enable creation of a prototype mobile application utilising cloud resources, not to be a detailed React Native introduction.

**Recommended Resources:**
- React Native documentation: <https://reactnative.dev/docs/getting-started>
- Expo documentation: <https://docs.expo.dev/>

**OU Library Resources:**
- Search `react native` on OU Library homepage
- Filter to eBooks using `Resource Type` sidebar
- Prioritise recent publications (React Native evolves rapidly)
- At time of writing (early 2023), 11 relevant books from 2022 were available

**Note:** Academic sources tend to lag behind professional publications for specific technologies, so journal articles may be less useful.

---

## 6. Hints and Tips:

### React Native Web Error:

If using a local install and getting an error on first web launch showing "It looks like you're trying to use web support...":

1. Press `Ctrl+C` to stop
2. Run the suggested command:

```bash
npx expo install react-native-web react-dom @expo/webpack-config
```

3. Follow version-specific instructions shown on screen

**Vulnerabilities Message:** At the end of install, you may see a message about vulnerabilities. Unless running in production, this is not a concern and is typical of npm package installation where packages quickly become outdated.

---

## 7. Further Reading:
- React Native Documentation: <https://reactnative.dev/>
- Expo Documentation: <https://docs.expo.dev/>
- React Native Directory: <https://reactnative.directory/>
- Chrome DevTools Documentation: <https://developer.chrome.com/docs/devtools/>
- Apple Accessibility Documentation: <https://developer.apple.com/accessibility/>
- Google Android Accessibility: <https://developer.android.com/guide/topics/ui/accessibility>

---

## 8. Key Commands Reference:

```bash
# Build and run activity in VCE
tm352 block2 build <part> <activity>
tm352 block2 build 1 3  # Example: Build part 1 of activity 3

# Alternative if block2 command not found
node ~/block_2/resources/scripts/build.js 1 3

# Copy skeleton files and setup
cp -r ~/block_2/skeletons/reactnative my-app
cd my-app
npm clean-install

# Run the development environment
npm run dev
# or
npm run start

# Install additional libraries
npx expo install <library-name>
npx expo install expo-camera  # Example
npx expo install expo-location  # Example

# Install web support (if error occurs)
npx expo install react-native-web react-dom @expo/webpack-config
```

---
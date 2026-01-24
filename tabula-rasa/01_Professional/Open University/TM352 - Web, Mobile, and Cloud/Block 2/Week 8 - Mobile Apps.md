---
date created: Friday, December 19th 2025, 12:08:55 pm
date modified: Friday, January 23rd 2026, 1:14:05 pm
OU-date-range: 22nd-28th November
---

# Week 8 - Mobile Apps:

# 1. Introduction:

The goal of this weeks module is to learn about the different types of mobile apps and how they are developed, along with how to setup a development environment and build a simple mobile application.

The TMA 02 assignment involves building a mobile app using React Native.

***
# 2. Aims:

**Learning Outcomes:**
- Compare and contrast approaches, tools and techniques used to create mobile apps
- Install and configure a hybrid mobile app software build environment.

***
# 3. Mobile Apps:

Mobile apps have two main types:

1. **Native**
	1. Native mobile apps are apps that are hosted on the Google Play Store or the Apple App Store; they are platform dependant.
2. **Web-based**
	1. Web-based mobile apps run within a browser and simulate the functionality of a mobile app.

From these approaches, different forms of mobile development have formed:

3. **Hybrid**
	1. Hybrid mobile apps use web-based technologies (JS, CSS, HTML, etc) but place this content within a native app container.
	2. So a container is written in Swift/Objective-C for iOS or Java/Kotlin for Android. These containers then run a **WebView** component which runs the web-based code.
		1. This container acts as a bridge between web code and native device features.
4. **Progressive Web Apps** (PWAs)
	1. PWAs are enhanced web apps that can be installed without app stores, and have native feel and functionality. They are also platform independent.
5. **Cross-platform native**
	1. Technologies like React Native & Flutter compile code to native. Meaning you get native UI whilst being platform independent.
	2. Unlike hybrid apps, You don't interact via a browser but actual native phone UI components and widgets.
## 3.1. Native Apps:

The core advantages of native apps is that: they can be distributed through proprietary application stores, thus have quality control through rating and feedback. Additionally, they are more likely to work efficiently and utilise the full features of the target OS (GPS, microphones, accelerometers, etc).

The main disadvantage of native apps is that the are more time consuming to port to other platforms and are more difficult to develop than web apps.

Native applications are best suited to providing a rich client experience. As they can support more widgets than a browser can, they allow user experience not possible via web apps, provide standardisation of UI controls this enables for them to achieve a look which is accepted and feel like that of the operating system's applications.

Web applications can have a common look across all devices, whereas Native apps offer additional security and privacy settings, such as restricting the number of permissions needed for the app to function. For instance: a web app needs internet access where as a Native app may not need it.

Another feature of native apps is needing to interface with the major mobile app platforms (Android and iOS phones) both of which require specialised skillsets.

### Android:

Writing apps for Android is easier, less expensive, and less time-consuming then for android. The following steps are:

1. Sign up for a Google Play developer account
2. You can use your own Integrated Developer Environment (IDEs), but Google has **Android Studio** which works on Windows, Mac, and Linux.
3. Apps can be built in various programming languages but **Java** is one of the most popular.
4. Android Studio also helps developers monetize their creations. By pricing the download or putting ads into the software.
5. Generally has less restrictive rules than iOS
6. A new app must be reviewed by Google, this takes under 24 hours usually and then the app is able to be published using the Google Play Developer Console.

### iOS:

Writing apps of iOS is much harder, as Apple discourages generic and hybrid apps. Along with this, they have a much more strict set of rules (**Cupertino Rules**) for writing and deploying native iOS apps. The following steps are:

1. Enrol in the Apple Developer Program via apples website.
2. Download XCode as the development tool. XCode has been designed to only run on MacOS machines, so iOS development requires an all-Apple environment.
3. Code your app. Originally, this was done using Objective-C, but because of the difficulty of the language - many developers weren't interested. Apple built Swift in 2014 to remedy this, which is a much more straightforward programming language that can be used instead of or alongside Objective-C
4. Testing your app through Apples suite of tools that enable distribution and monetization of the app like Android Studio.
5. Submit the app to be reviewed by Apple. This usually takes under 24 hours, and can be published once accepted.

## 3.2. Web Apps:

Web apps will work on most, if not all mobile OS systems, and generally require less skill and experience to develop. Though they are less efficient than native apps, because of the technological overhead of components that convert JS or web components into native instructions.

Web apps are build using HTML, CSS, and JavaScript and then run via the device's web browser. Developing an app using these tools is much faster and cheaper to build as well as to maintain in comparison to native OS programming for mobile devices.

The downside of web apps is that they are slower to load and are less responsive than native mobile apps. Security is also a bigger factor, if the app has minimal functionality and connects to a remote web-server to do heavy lifting - security can be compromised.

HTML5 has also enhanced the functionality of web apps, but web app are always lagging behind the features of native apps. A web app can use GPS, but it isn't as seamless or straightforward - as the device will often ask for confirmation about accessing these privileges.
## 3.3. Hybrid Apps:

It is challenging to decide whether to choose to develop a web app or a native app, it depends on the experience of the programmer, resources, scope, time-frame, and so on.

A useful middle group is the hybrid approach. This enables developers to native code from a single code base across the multiple mobile platforms, there can be different approaches in building a hybrid app. But in each case, the framework is often an intermediate step written by the developer that interfaces between native APIs.

The goal of hybrid apps is to write JS code that will be converted into native level instructions and functionality. The hybrid approach lowers the barrier for entry giving web developers a chance to use existing skills to build a mobile app.

The software framework chosen to be the intermediate actor can change, but all of them enable developers to work with familiar technology than the device specific features or APIs.

You can research, look at modern data, stack overflow survey's, etc. to find modern frameworks.

### 3.3.1. Flutter:

[Flutter](https://flutter.dev/) which is a hybrid framework used and maintained by google, uses Dart. Dart is similar to JavaScript and Swift, Flutter either compiles to native code for apps or JavaScript for web apps to maximise performance. But there is also strong compatibility for Android, iOS platforms and web apps.

A large focus of Flutter is in building a strong UI that functions across mobile, web, desktop, native, and embedded apps. Flutter is not dependant on widgets provided by each device, since it uses it's own rendering engine to build UI elements.

### 3.3.2. React Native:

[React Native](https://reactnative.dev/) uses the React framework to build mobile apps. As with React, applications are coded within JS but the UI is rendered natively to the mobile app. So native application code is built from the JS to render to the screen and complete other tasks.

React Native supports Android and iOS as well as other third party apps. The difference from Flutter, is that apps developed with React Native use that devices native UI building blocks.

### 3.3.3. Ionic

[Ionic](https://ionicframework.com/) is built on [Cordova](https://cordova.apache.org/) and can use popular frameworks such as Angular, React, and Vue. Cordova works to provide the mobile integration and wraps HTML, CSS, and JS of a web app into a native view container.

Cordova's native view container comprises of a special browser window that is embedded within a native app. It doesn't contain the typical window structure of a browser, so it runs the HTML, CSS, and JS that make up a hybrid application inside a web view container.

The advantage of this is that hybrid apps can access the full features of a mobile app, as this would be more challenging if a web app running within a device's browser.
### 3.3.4. Summary:

Various mobile frameworks can be used to build hybrid apps, hybrid apps help developers as they can use their existing framework knowledge of JS and other JS frameworks to build a native experience and native device features can be integrated through JavaScript APIs.

***

## 4. Developing Mobile Apps:

React Native is the most popular language at the moment, and previously we've used react to build web apps, so it's the framework we are going with in this module.

You can use [Expo](https://expo.dev/) to build and demo mobile apps quickly, for the module we can't use this since the OCL doesn't support Metro via the proxy.

Developing within the OCL is the easiest way forward to completing quality coursework, so that's what I'll be doing.
### 4.1. OpenComputing Lab (OCL):

Using the OCL is similar to block 1.
### 4.1.1. Creating a React Native Project from a Provided Skeleton:

To build and run any activity we can use the following within the integrated terminal in the VCE:

```Bash
tm352 block2 build <part> <activity>
$ tm352 block2 build 1 3 # Build part 1 of activity 3
$ node ~/block_2/resources/scripts/build.js 1 3 # If block2 command is not found.
```

Or, we can use bash to copy skeleton files we use the following:
```Bash
cp -r ~/block_2/skeletons/reactnative my-app
cd my-app # Move to the directory
npm clean-install # We then install the necessary dependancies.
```

Do note we don't need to run `npm audit fix` since it's fine for our coursework, but not for production.

Finally, we run the environment similarly to block 1:
```Bash
npm run dev
```

### 4.1.2. Building an Empty Reactive Native Project from Scratch:

This isn't strictly required for the module, and I can use search engines and AI LLMs if I need to setup a production ready environment, or use policies given to me by a company.

### 4.1.3. Running the React App once Created:

You just use `run dev`

***

## 4.2. Installing Expo and React Native Locally:

This isn't strictly required for the module, and I can use search engines and AI LLMs if I need to setup a production ready environment, or use policies given to me by a company.

***

## 4.3. Expo Snack:

This isn't strictly required for the module, and I can use search engines and AI LLMs if I need to setup a production ready environment, or use policies given to me by a company.

***

## 5. Gaining Feedback with OpenStudio:

This section requires using the OUs OpenStudio to ask questions and share content with peers. So I'll follow the guide that is shown and place the content within the [[TMA 02/Question 1|TMA 02]].

***
## 6. Case Studies:

In block 2, three main case studies are explored.

### 6.1. Open University Running Club:

The [OURC](https://race-club.stem.open.ac.uk/) operates a website to promote the club and races that it operates. It also keeps track of race results. The website is simple but as runners access it on the go as well as at their desks it should be accessible from a range of devices.

### 6.2. Weather Station:

The weather station app is integrated into a web service to allow location-based weather observations to be reported and received. This simple app allows the key functionality of services to be explored.

### 6.3. Exercise Tracker:

The exercise tracker is a mobile application designed to allow users track a run. It keeps things simple, focusing on tracking the time and location of the run, allowing a runner to focus on running.

***

## 7. Summary:

Mobile applications can be made in many different ways, the native, hybrid, and PWA approach each have advantages and disadvantages. For our purposes, the Hybrid approach works best, since we can use our skills from React from Block 1 and Block 2 in the form of React Native.



***

## 8. Further Reading:

***

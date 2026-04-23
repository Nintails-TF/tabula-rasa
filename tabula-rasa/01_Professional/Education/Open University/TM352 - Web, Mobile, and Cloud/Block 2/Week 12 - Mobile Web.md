---
date created: Friday, December 19th 2025, 12:08:55 pm
date modified: Friday, January 30th 2026, 4:26:41 pm
Gen: "1"
---

# Week 12 - Mobile Web

## 1. Introduction

This week examines how websites and apps are adapted for use on mobile devices. A **web app** is an application that runs inside a web browser, allowing users to fulfil functions that traditionally required desktop software installation (e.g., email, calendar, contacts).

As web technologies became more sophisticated and users spent more time online, developers realised that developing and delivering apps from inside a web browser was convenient for both them and their users.

---

## 2. Aims

**Learning Outcomes:**

- Understand the differences between mobile and desktop web browsers
- Compare and contrast different mobile web design strategies
- Apply the principles of designing responsive websites
- Compare the advantages and disadvantages of web apps, especially single-page apps, to understand how they differ from mobile websites

---

## 3. Mobile Website Design Strategies

As a website designer, knowing your audience is crucial. A growing portion of your audience is likely using mobile devices - depending on your site's demographic, mobile may be the **primary interaction** users have with your website. Support for mobile devices can no longer be an afterthought.

**The Core Challenge:** Screen size differences between mobile and desktop devices pose significant challenges for designers wanting websites that work well on both.

**Three Broad Approaches:**

1. Do nothing
2. Maintain separate websites for desktop and mobile devices
3. Have one website that works for both (responsive design)

---

### 3.1. Do Nothing

You may choose to ignore mobile-specific considerations for several reasons:

**Potentially Valid Reasons:**

- Confidence that visitors will only use large-screen devices (desktops/tablets)
- In corporate environments, you may be able to narrow your user base

**Less Valid Reasons:**

- Assuming mobile technology will solve its own challenges (screen size limits remain)
- Believing the desktop-mobile gap will narrow enough (touchscreen input differences persist)
- Cost constraints (may or may not be valid depending on audience and budget)

**Reality Check:** Even larger, conservative organisations have had to embrace "Bring Your Own Device" (BYOD), where employees expect to access company data on personal devices.

#### 3.1.1. Fixed-Width Design

**Historical Context:**

- Late 1990s: Web designers from print backgrounds wanted control over designs
- Print paper sizes are fixed; web browsers are dynamic
- Early common resolution: 800 × 600 pixels
- Designers created fixed-width websites under 800 pixels to avoid horizontal scrolling

**Evolution:**

- Mid-2000s: Majority of desktops at 1024 × 768 pixels
- Designers assumed 960-990 pixels available for content
- Why not 1024? Browser furniture (scrollbars, window frame) takes up space
- **960 pixels** became most popular: easily divisible, good for column layouts

**Mobile Behaviour with Fixed-Width Sites:**

- Default: Mobile browser renders at fixed width, scales down to fit screen
- User sees whole desktop page "zoomed out"
- Must pinch-open to zoom in and make links touchable

**Example Comparison:**

- Hampshire Athletics: Shows scaled-down full page (default behaviour)
- OURC (original): Shows full-size content with horizontal scrolling required

#### 3.1.2. Gradations of 'Do Nothing'

The "do nothing" approach is more nuanced than it sounds. There are gradations involving one or two lines of code that attempt to improve mobile experience - but often make things worse.

**The Problem with Quick Fixes:** Adding viewport meta tags to fixed-width sites often breaks default mobile browser behaviour that would otherwise scale down the site appropriately.

#### 3.1.3. Viewport

**Definition:** The viewport is the part of the browser window where website contents are displayed. It excludes scrollbars, browser window frame, and browser chrome (interface components).

**Desktop vs Mobile:**

- Desktop: Viewport is narrower than screen width (due to scrollbars, frame)
- Mobile: Viewport fills entire screen width (no scroll bars or frame)

**The Viewport Meta Tag:**

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" />
```

**Properties Explained:**

|Property|Description|Effect|
|---|---|---|
|`width=device-width`|Sets viewport to full screen width|Viewport always fills screen|
|`initial-scale=1`|Multiplier for scaling (1 = no scaling)|Page displays at 100%|
|`maximum-scale=1`|Limits zoom level|Prevents user from zooming|

**Important Notes:**

- If `initial-scale` is not specified, browser automatically scales to fit page in viewport
- The viewport meta tag is part of **HTML5**, not XHTML
- Should NOT be used on fixed-width XHTML sites (breaks default behaviour)

**Best Practice for "Do Nothing":** If you're doing nothing to accommodate mobile browsers, truly do nothing. Let the mobile browser scale down the site so it fits within mobile display - this is what users expect.

---

### 3.2. Separate Mobile Site

For a time, prevailing wisdom was that mobile and desktop needed separate sites due to their different design considerations.

**How It Works:**

1. Detect that a mobile device is accessing the website
2. Redirect user to a separate mobile URL
3. Use client- or server-side techniques

**Browser Sniffing:** When a browser requests a web page, it identifies itself with a **user agent string** containing browser type and platform details.

**Example User Agent Strings:**

Desktop:

```
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36
```

Mobile:

```
Mozilla/5.0 (Linux; <Android Version>; <Build Tag etc.>) AppleWebKit/<WebKit Rev> (KHTML, like Gecko) Chrome/<Chrome Rev> Mobile Safari/<WebKit Rev>
```

**Typical Mobile Fixed Width:** 320 pixels (once a common mobile display width)

**Case Study: London 2012 Olympics**

- LOCOG served separate mobile and desktop sites
- Mobile version designed for 320-pixel width
- Challenge: Many mobile devices in one location
- Stripped-down mobile site reduced network load

#### Pros and Cons of a Separate Mobile Site

**Advantages:**

- Reduced network load for mobile users
- Content optimised for specific screen sizes
- Can provide different feature sets

**Disadvantages:**

|Issue|Problem|
|---|---|
|URL sharing|If you share a mobile URL, recipients get mobile version regardless of their device|
|Fixed widths|Both sites optimised for specific widths only|
|Development cost|Separate development and maintenance efforts required|
|Keeping in sync|Content must be updated in two places|

**Current Status:** Redirecting to separate stripped-down mobile sites has fallen out of fashion. Modern approach is responsive design (e.g., Tokyo 2020, current London 2012 legacy site).

---

### 3.3. Design One Website That Works Well for All Devices

Instead of fixed-width designs, many designers now re-embrace the **flexible nature of the web**. Using advanced CSS techniques, page contents display optimally according to available screen size.

**Responsive Design Benefits:**

- Fills whole screen on large desktop displays (no empty space)
- Makes best use of all available space on progressively smaller screens
- Single codebase to maintain
- Consistent URLs for sharing

**Example:** In 2015, BBC converted BBC News Online from separate mobile/desktop sites into one responsive design.

**Key Characteristic:** When you resize the browser window, contents change to make best use of available space.

---

## 4. Responsive Website Examples

Responsive websites present content differently across display sizes while being served from the same URL. This is NOT the same as separate mobile/desktop versions - a responsive site adapts to ALL screen sizes, not just two predefined extremes.

**Examples to Explore:**

- <https://www.bostonglobe.com/>
- <https://www.open.ac.uk/>
- <https://www.w3schools.com/>
- <https://www.theguardian.com/uk>
- <https://www.microsoft.com>
- <https://bbc.co.uk/news>

**Historical Note:** Early web pages (1993) were responsive by default because they were textual - content reflowed when browser size changed. However, elements didn't come/go or change from text to icons, so it wasn't sophisticated responsiveness.

**Tim Berners-Lee's First Web Page:** <http://info.cern.ch/hypertext/WWW/TheProject.html>

- Text reflows when browser narrowed
- Basic responsive behaviour by default

---

## 5. Three Principles of Responsive Web Design

Responsive web design relies on three key techniques:

1. Fluid design
2. Flexible images
3. CSS media queries

---

### 5.1. Fluid Design

**Fixed-Width vs Fluid Design:**

|Fixed-Width|Fluid|
|---|---|
|Page designed for specific width (e.g., 960px)|Page flows to fit available viewport width|
|Uses pixels for dimensions|Uses percentages for dimensions|
|Empty space on larger screens|Fills available space|

**Percentage-Based Widths:**

- 100% fills all viewport width
- 50% fills half
- Percentage is of available viewport width

**Example CSS for Fluid Design:**

```css
/* Fixed-width (problematic) */
#page_container {
    width: 940px;
    padding: 0 20px;
}

/* Fluid (responsive) */
#page_container {
    width: 100%;
    max-width: 1200px;
    padding: 0 2%;
}
```

**Key Principle:** Avoid specifying absolute dimensions in pixels for page elements if you want responsive behaviour.

---

### 5.2. Flexible Images

Images need to scale with viewport width rather than being cropped or overflowing.

**Basic Flexible Image CSS:**

```css
img {
    width: 100%;
}
```

This makes images fill their container width, scaling up and down.

**Problem:** Images can scale past 100% of their actual size (may look pixelated).

**Better Solution:**

```css
img {
    max-width: 100%;
}
```

This ensures images:

- Scale down when viewport is smaller than image
- Never scale up past their actual size

**Complete Basic Responsive Styling:**

```css
/* Flexible images */
img {
    max-width: 100%;
}

/* Basic typography */
body {
    font-family: arial, sans-serif;
    font-size: 100%;
    background: #ffffff;
}

/* Link styling */
a {
    text-decoration: none;
    color: #069;
}

a:hover {
    text-decoration: underline;
}
```

---

### 5.3. CSS Media Queries (and Device Breakpoints)

**Breakpoints:** The specific viewport widths at which display contents change. You, as the designer, decide where to define these.

**How to Determine Breakpoints:**

1. Start with desktop design
2. Narrow browser window using emulator
3. Note when design "breaks" (no longer works effectively)
4. Implement different design at that width

**Example:** OURC website starts breaking at 960 pixels (search button and navigation links get cut off).

**Media Query Syntax:**

```html
<!-- In HTML (linking stylesheets) -->
<link rel="stylesheet" media="(max-width:959px)" href="medium.css">
<link rel="stylesheet" media="(min-width:960px)" href="large.css">
```

**Explanation:**

- `medium.css` applied up to and including 959 pixels
- `large.css` applied to viewports 960 pixels and greater

**Three Common Breakpoints (Desktop, Tablet, Mobile):**

```html
<link rel="stylesheet" media="(max-width:480px)" href="small.css">
<link rel="stylesheet" media="(min-width:500px) and (max-width:959px)" href="medium.css">
<link rel="stylesheet" media="(min-width:960px)" href="large.css">
```

**Alternative: Media Queries Within CSS:**

```css
/* Base styles (mobile-first) */
.container {
    width: 100%;
    padding: 10px;
}

/* Tablet */
@media (min-width: 500px) {
    .container {
        width: 90%;
        padding: 20px;
    }
}

/* Desktop */
@media (min-width: 960px) {
    .container {
        width: 80%;
        max-width: 1200px;
        padding: 30px;
    }
}
```

**What Changes at Breakpoints:**

- Display, hide, or rearrange page elements
- Change navigation from full menu to hamburger icon
- Stack columns vertically instead of horizontally
- Adjust font sizes and spacing

---

## 6. Advantages and Disadvantages of Web Apps

**For Users:**

- No download/installation required
- No version checking for platform compatibility
- No dialogue boxes to navigate
- Always access to latest version
- Just type URL into browser address bar

**For Developers:**

- Add new functionality without user updates
- Single codebase for all platforms
- Easier maintenance and bug fixes

**Web App Pioneers:** Google (Gmail, Google Maps, Google Docs, Google Photos)

**Web Apps vs Web Pages:**

|Web Pages|Web Apps|
|---|---|
|Offer information|Focus on interaction|
|Static content|Enable users to "get things done"|
|Read-only|Create, edit, share|

**Additional Web App Benefits:**

- Leverage internet connectivity for extra functionality
- Access to online data (updated maps, driving conditions)
- Easy distribution and sharing

**Progressive Web Applications (PWAs):**

- Enabled by HTML5
- Can cache online content for offline usage
- Service workers sit between app and internet
- Control and cache web pages locally
- Enable offline media playback, catalogue browsing
- Operations (like orders) stored and synced when online again

**PWA Limitation:** Cached data may be out of date (not connected to live database)

---

### 6.1. Web App Weaknesses

|Weakness|Description|
|---|---|
|**Connectivity dependent**|Must typically be online for full functionality|
|**Browser constraints**|Limited to HTML, CSS, JavaScript capabilities|
|**Performance**|Can be slower than locally-installed software due to network reliance|
|**Wait times**|Page loads after each interaction (server-side data retrieval)|

**Counter-argument:** Browser interface is familiar to users, so learning curve between web apps is minimal. Web apps typically behave similarly, making them quite usable.

---

### 6.2. Single-Page Applications

**AJAX (Asynchronous JavaScript and XML):**

- Addressed early web app weaknesses
- Send/receive data without page reloads
- JavaScript makes requests in background
- Can redraw selected UI elements without full page reload
- Improved user interaction

**Single-Page Application (SPA):**

- Entire web application contained in single page
- Clicking links/buttons doesn't redirect to another URL
- JavaScript retrieves data and manipulates DOM
- Presents different views without page reload

**SPA Advantages:**

- No URL-to-URL redirection
- Can work completely offline
- Use HTML5 Application Cache (AppCache) for local storage
- Can launch even when offline
- User experience approaching native apps

---

### 6.3. Web Apps on Mobile Devices

**Why Web Apps Initially Struggled on Mobile:**

1. **Easy native app installation**
    
    - Pre-installed marketplaces (safe, secure)
    - Quick install/uninstall
    - Fast launch
    - Automatic updates
2. **Pricing**
    
    - Mobile apps very cheap (price of coffee)
    - Free versions with ads or in-app purchases
3. **Design issues**
    
    - Web apps designed for 960-pixel desktop displays
    - Didn't work well on mobile screen sizes
    - Native apps were optimised for mobile
    - Early mobile apps were often just containers for mobile-optimised web content

**Mobile Web App Advantages:**

- Can launch from device home screen (like native apps)
- With right configuration, run without browser interface (no menu bars, address bars, bookmarks)
- Viewport fills entire screen

---

### 6.4. Making a Web App Look and Feel More Native

To make a web app appear like a native app:

1. Allow users to create application shortcut on home screen
2. This is NOT the same as a browser bookmark
3. Code web app so shortcut signals OS to launch full-screen
4. Remove typical web browser controls

**Configuration Resources:**

- Chrome: Google's Web App Manifest documentation
- Safari on iOS: Apple's Safari Web Content Guide
- Opera: Opera's web app documentation

**Key Technologies:**

- Web App Manifest (JSON file defining app properties)
- Service Workers (for offline functionality)
- App Shell architecture (immediate loading of UI)

---

## 7. Summary

This week focused on developing mobile web apps and understanding responsive design:

**Key Concepts:**

|Topic|Key Points|
|---|---|
|**Design Strategies**|Do nothing, separate sites, responsive design|
|**Viewport**|Browser content area; meta tag controls scaling|
|**Fixed-Width**|960px common; problematic for mobile|
|**Responsive Design**|Fluid layouts, flexible images, media queries|
|**Breakpoints**|Width thresholds where design changes|
|**Web Apps**|Browser-based applications; SPAs improve UX|

**The Modern Approach:**

- Use responsive design (single site for all devices)
- Implement fluid layouts with percentages
- Make images flexible with `max-width: 100%`
- Use CSS media queries for breakpoints
- Consider PWA features for offline capability

**Where Next:** In the next part, you will investigate how asynchronous communications are used by applications to communicate with web services.

---

## 8. Key Code Reference

### Viewport Meta Tag

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Flexible Images

```css
img {
    max-width: 100%;
    height: auto;
}
```

### Basic Media Queries

```css
/* Mobile first approach */
.element {
    width: 100%;
}

/* Tablet */
@media (min-width: 768px) {
    .element {
        width: 50%;
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .element {
        width: 33.33%;
    }
}
```

### Link-Based Media Queries

```html
<link rel="stylesheet" media="(max-width:767px)" href="mobile.css">
<link rel="stylesheet" media="(min-width:768px) and (max-width:1023px)" href="tablet.css">
<link rel="stylesheet" media="(min-width:1024px)" href="desktop.css">
```

---

## 9. Glossary

|Term|Definition|
|---|---|
|**Viewport**|The area of browser window displaying website content|
|**Fixed-width design**|Website designed for specific pixel width|
|**Fluid design**|Website using percentages to fill available space|
|**Responsive design**|Single website adapting to all screen sizes|
|**Breakpoint**|Width at which website layout changes|
|**Media query**|CSS feature to apply styles based on device characteristics|
|**Browser sniffing**|Detecting browser type via user agent string|
|**User agent string**|Browser identification sent with HTTP requests|
|**Web app**|Application running inside web browser|
|**SPA**|Single-Page Application|
|**AJAX**|Asynchronous JavaScript and XML|
|**PWA**|Progressive Web Application|
|**AppCache**|HTML5 feature for local storage/offline access|
|**Service worker**|Script controlling web page caching and offline behaviour|

---

## Acknowledgements

- Hampshire Athletics website screenshots
- London 2012 Olympic Games website (Internet Archive)
- Open University Running Club website examples

---
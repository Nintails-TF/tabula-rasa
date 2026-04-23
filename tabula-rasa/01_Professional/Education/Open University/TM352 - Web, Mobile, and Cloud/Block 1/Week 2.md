---
date created: Tuesday, November 11th 2025, 11:46:19 am
date modified: Thursday, November 13th 2025, 12:14:08 pm
---

# 1. Introduction:

The web makes it easy for businesses and people to create and craft shopping, social media, entertainment, government services, etc. All for a low price and a low barrier to entry.

Since making websites is cheap compared to brick and mortar counterparts, and hardware and servers can be rented and spun up when needed. The web as we know it will be around for a long, long time.

***
# 2. Aims:

**Key Aims:**
- The respective roles of markup, styling, and scripting
- The role and development of web standards
- The practical and legal aspects of accessibility
- How to use HTML, CSS, and TypeScript.

***
# 3. Marking up Structural Information:

Markup languages are used to represent data in a clear way that not only computers can read, but people can as well. **Markdown** and **HTML** are examples of this. 

## 3.1. Web Hypertext Application Technology Working Group:

HTML is old, the first version was produced in 1993, and the first standard made by the **World Wide Web Consortium (W3C)**. After the realise of HTML 4.01 development slowed down as the W3C worked on XHTML.

During the early 2000s, with new browsers there became a great desire to continue development of the HTML standard. A new organisation called the **Web Hypertext Application Technology Working Group (WHATWG)** formed in 2004.

Disagreements formed between the W3C and WHATWG about the development of HTML 5. W3C wanted a slower more formal approach, whilst the WHATWG wanted a living standard. Since 2019, the W3C has given authority to WHATWG on the HTML Standard.

We can view today's HTML standards through different channels, but the most practical choices are:

1. [MDN Web Docs](https://developer.mozilla.org/en-US/)
	1. The Mozilla Developers Network covers the HTML, but also CSS, JS, and other web frameworks as well. It's a one stop shop of anything web related. A very powerful resource.
2. [HTML Standard](https://html.spec.whatwg.org/multipage/)
	1. This is the raw HTML standard as written by WHATWG.

***

# 4. Weekly Tasks:

## 4.1. Markup with HTML:

HTML is basically a text file that can be edited to change what is displayed, using Svelte as a JavaScript framework. This is because websites have become web apps, and you need dynamic components and features.

Each framework has advantages and disadvantages over other frameworks, the web development environment is constantly evolving.

***
## 4.2. Setup:

```Bash
npm ci # To download the necessary JS libraries.
npm run dev # To run the development server.
```

Ensure when you run the web server to use the global URL, not the local version.

***
## 4.3. Basic HTML:

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + Svelte + TS</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/src/main.ts"></script>
  </body>
</html>
```

Remember, that understanding and explaining code is key, I'm going to illustrate a few points of what the purpose of certain lines are:

- `<!DOCTYPE html>`
	- As HTML is now a living standard, we are just specifying that we are using the HTML standard. This is done, as to ensure that older browsers don't apply old standards.
	- Best practices to write tags and attributes in lower case. e.g. so `html` not `HTML`. As to be consistent with the HTML 5 modern standards.
	- Having a language attribute also helps browsers understand what languages to use for your website.
- `<html>`
	- The `<html>`tag must contain a `<head>`and`<body>`. A web browser first looks at metadata and resources within the head, before rendering the body.
	- You can place CSS links, scripts, SEO inside of the head tag.
		- Helps prevent a flash of unstyled content.
	- The body tag holds everything visible on the page.

#### 4.3.1. Writing Valid HTML:

Ensure that you close your tags and that your HTML is valid, to prevent any bugs or glitching, see:

```HTML
<main>
  <div>Some content  <!-- Need a closing </div> tag! -->
    <div>Some more content</div>
  </div>
</main>
```

Also ensure that the nesting level of the closing tags is correct as well.

***
## 4.4. HTML Elements:

Modern HTML has a huge amount of elements you can use to markup content. The MDN holds a [HTML elements reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements) for this.

Here is a quick crash course through the most critical elements.
### 4.4.1. Document Metadata:

All document metadata should be contained within the `<head>` element. 

**The most typical elements used here are:**

- **`<title>`**: The title of the page. This is generally shown in either the browser window’s title or in the browser tab’s title.
- **`<meta>`**: Defines a wide variety of metadata settings.
- **`<link>`**: Defines links to external content. Some of these links can define alternative versions of the page, while others instruct the browser to load in additional data, such as an external stylesheet.

### 4.4.2. Structure:

Structural elements are HTML elements that define spaces in which content in collated together. You should use descriptive structural elements rather than pure `<div>` as it aids in both code readability, but particularly accessibility.

**The most common structural elements are:**

- **`<header>`**: Contains introductory information either for the page or for a specific section that it is in.
- **`<main>`**: The dominant content of the body. If the page mainly contains information, then this will contain the primary content. If the page is an application, then this will contain the main functionality of the application.
- **`<footer>`**: The footer for either the page or the specific section it is in.
- **`<nav>`**: Defines an area that provides navigation functionality to the user.
- **`<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`**: Headings of different levels. Your page **must** always have one `<h1>` element and you **must not** skip heading levels, so, for example, your `<h1>` should not be followed by a `<h3>`.
- **`<article>`**: Represents a self-contained part of the page.
- **`<aside>`**: Contains information that is only indirectly related to the main content of the page.
- **`<section>`**: A section within the page, for whatever use desired. Should always be associated with a heading.

These descriptions are somewhat vague, because these guidelines are designed for an enormous amount of use-cases. But they are guidelines.
### 4.4.3. Text Blocks:

Text content is used to structure they actual content within the page, so structure defines where the text is placed, where as text is the **actual media** people are looking at.

**The most common textual elements are:**

- **`<div>`**: A generic block tag that has neither any pre-defined semantic role, nor any standard styling that is applied to it. You should only use this if there is no more appropriate semantic element available.
- **`<p>`**: A paragraph of text.
- **`<blockquote>`**: Indicates that the containing text is an extended quotation. A source can be provided via the `<cite>` element (see below).
- **`<figure>`**: An element to group together an image (via the `<img>` inline element) with a `<figcaption>` element.
- **`<figcaption>`**: The caption for a `<figure>`.
- **`<ul>`**: An unordered list of items. The individual items are then marked up using the `<li>` element. This is generally displayed as a bullet list.
- **`<ol>`**: An ordered list of items. The individual items are then marked up using the `<li>` element. This is generally displayed as a numbered list.
- **`<li>`**: A single item in either an ordered (`<ol>`) or an unordered (`<ul>`) list.
- **`<dl>`**: A list of definitions, similar to a dictionary. Each item in a definition list is always made up of a definition term (`<dt>`) and the definition data (`<dd>`).
- **`<dt>`**: The term that is being defined in a definition list (`<dl>`). In a dictionary this would be the word itself.
- **`<dd>`**: The definition for the definition term (`<dt>`). In a dictionary this would be the word’s definition.
### 4.4.4. Tables:

Table content is used for data typically stored within tables, you **shouldn't** use these for the layout of a page in the way you'd use structural elements.

**Common Table Elements Include:**

- **`<table>`**: Marks out a table, which can contain the `<caption>`, `<thead>`, `<tbody>`, or `<tfoot>` elements.
- **`<caption>`**: A caption for the whole table.
- **`<thead>`**: The header part of the table. Contains at least one row (`<tr>`) of table header (`<th>`) elements.
- **`<tbody>`**: The main content part of the table. Contains at least one row (`<tr>`) with either table data (`<td>`) or table header (`<th>`) elements.
- **`<tfoot>`**: The footer of the table. Contains at least one row (`<tr>`) with table data (`<td>`).
- **`<tr>`**: A row in the table, regardless of whether it is in the header, body, or footer of the table.
- **`<td>`**: A single cell in the table.
- **`<th>`**: A single cell in the table that contains header information.

When you build a table, you generally want to structure the content using `<table>`, `<thead>`, and `<tbody>`. The tag of `<tfoot>` isn't used as much, but useful in displaying totals (Net Assets, Price, etc.)
### 4.4.5. Inline Text:

Inline elements aren't positioned in vertical blocks like other elements in the DOM. But are displayed in a horizontal line and break into a new line when the maximum width of the parent container is reached.

**There are tons of inline elements, but the most commonly used are:**

- **`<span>`**: A generic inline tag that has neither any pre-defined semantic role, nor any standard styling that is applied to it. You should only use this if there is no more appropriate semantic inline element available.
- **`<a>`**: A link to a URL. This will be shown to the user as a clickable link.
- **`<em>`**: Indicates that the text content is emphasised.
- **`<strong>`**: Indicates that the text content is strongly emphasised.
- **`<ins>`**: Indicates that the text content has been added to the page at some point.
- **`<del>`**: Indicates that the text content has been deleted from the page.
- **`<s>`**: Indicates that the text content is no longer relevant or accurate.
- **`<cite>`**: A source for a `<blockquote>` quote element.
### 4.4.6 External Content:

External elements include a wide range of element types: like images, script links, videos, even other webpages.

**Common external elements include:**

- **`<picture>`**: Groups together an `<img>` element for displaying a single image, with one or more `<source>` elements for specifying alternative versions of the image for different screen sizes.
- **`<img>`**: A single image that is shown to the user.
- **`<video>`**: A video to be shown to the user. Use the `<source>` to specify different versions of the video to use.
- **`<source>`**: A media resource for use in `<picture>` or `<video>` tags. It is generally used to either provide different resolutions or different file types. The browser can look at these and depending on which formats the browser supports and aspects such as device type and network speed can pick the most appropriate version to display.
- **`<iframe>`**: Allows you to embed one web page inside another. Because this potentially a security issue, the embedding page can specify what functionality the embedded page has access to and the embedded page can specify whether the browser may embed it at all. We will touch on some of these details when we cover security-related aspects later in the block.
- **`<script>`**: An element that contains JavaScript code to implement dynamic features. Importantly the code is executed _immediately_ when the browser processes the `<script>` element, regardless of whether the rest of the page has completed loading. When building things by hand, we would have to take account of this, but using the frameworks we will look at in this block, we can mostly ignore this. The `<script>` element is also unusual, since it can be placed both in the body and in the header of the page.

### 4.4.7 Forms:

Form elements are used to create forms that gather feedback and data from users.

**Common form elements include:**

- **`<form>`**: Groups together one or more form input elements. The data entered into the form elements can then be sent to the server together, for further processing.
- **`<button>`**: A button that the user can click on. Use this if you want to let the user initiate an action that is **not** navigating to another page. For navigating to another page, always use the `<a>` element.
- **`<label>`**: A human-readable label for another input element. All input elements **must** have an associated `<label>`.
- **`<input>`**: An configurable input element, including various text, number, email, … elements and also checkboxes and radio buttons. Which input element is shown depends on the attributes set on the element.
- **`<textarea>`**: A multi-line text input area.
- **`<select>`**: A drop-down selection element. Each option that the user can select is provided via the `<option>` tag.
- **`<option>`**: A single option for use in the `<select>` element.
- **`<progress>`**: An element representing a progress bar.

***
## 4.5 HTML Attributes:

All HTML attributes must be placed into the opening tag of an element, the basic structure of HTML elements is as followed.

```HTML
<tag attribute-name="attribute-value">Content</tag>
```

Naming attributes should be done with hyphens to separate spaces. Attribute names can contain any text, except for speech marks which need to be substituted for: `&quot;`.
### 4.5.1 Generic Attributes:

The two most commonly used attributes which are universal across any HTML element are the `id` and `class` attributes.

```HTML
<tag id="box-warning-error"> <!-- We use kebab-case here for id and class names -->
<tag class="box warning"> 
```

- `id`: Must be unique, though most modern browsers will try to handle this even if there is an error, but it's poor and badly written HTML.
- `class`: You can have multiple elements that hold a single class. Different types of classes are added through a **space-separated list**. So in the above example, the tag has both **box** and **warning**class assigned to it. 

IDs will be override classes, so the styling done by an class will get overwritten.
### 4.5.2 Specific Attributes:

In addition to these generic attributes, many HTML elements can have further attributes. A few of the most common ones have been listed.

#### 4.5.2.1 Links:

- **`href`**: The `href` attribute on the `<a>` link element is used to specify which URL the browser will navigate to, if the user clicks on the link.
#### 4.5.2.2 Images:

- **`src`**: The `src` attribute on the `<img>` specifies the URL from which the browser will load the image that is then displayed to the user.
- **`alt`**: The `alt` attribute on the `<img>` provides a text alternative of the image. In most cases this should be relatively brief and if you need to provide a more extensive description, use the `<figure>` and `<figcaption>` elements to provide a fully detailed description.
	- This helps accessibility and 

#### 4.5.2.1 Forms:

- **`action`**: Specified on the `<form>` element, it specifies the URL that the form’s data is sent to, when the user submits the form.
- **`type`**: Specified on the `<input>` it is used to configure the display mode of the `<input>` element. Valid values include `text`, `number`, `email`, `search`, `checkbox`, and `radio`. The degree to which these different input types differ in how the user interacts with them depends [upon the browser](https://caniuse.com/?search=type).
- **`value`**: Specified on the `<input>` or `<select>` elements, it contains the initial value to show to the user.

### 4.5.3 Accessibility Attributes:

There are also a number of [accessibility-related attributes](https://docs.ocl.open.ac.uk/tm352/25j/block-1/week02/accessible-rich-internet-applications/index.html), which we will cover later in this block.

***
# 5. Styling with CSS:

Making sure that marked up content is visually appealing is important. Though you need to ensure that the content and styling remain separate from each other. As styling updates frequently and content doesn't.

We don't want to change markup once we've written it, sometimes it must be done though.

## 5.1. Word Wide Web Consortium (W3C):

The CSS specification is still maintained by the W3C, though the standard is split into various separate modules. CSS 2.1 was released in 2011, with snapshots of certain modules being evolved over time, there will be no CSS 3 release.

Snapshots are mainly targeted at browser implementers. The best resources for web developers would be: the [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS) and [Can I use](https://caniuse.com/).

**Key Concepts:**
- How to define a styling rule.
- How to specify which HTML elements a styling rule applies to.
- How the browser combines styling rules.

## 5.2. The CSS Rule:

CSS is used to style, design, and update the look of a webpage. 

**Core Concepts:**
- How to define a styling rule.
- How to specify which HTML elements a styling rule applies to.
- How the browser combines styling rules.

The structure of a CSS rule is as followed:
```CSS
selector1, selector2 {
    name1: value1;
    name2: value2;
}
```

In this case we have two selectors separated by a comma. Each property or CSS attribute must be closed by a semi-colon. 

It's trickier in CSS to specify complex values, you really need to check the documentation in this case.

## 5.3. CSS Selectors:

There are many [CSS selectors]([CSS selectors - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Selectors)), but the core 4 would be the following.

### 5.3.1. Element Selector:

```CSS
a {
  color: blue;
}
```

This selects all elements of a given type, so all anchor tags in this case.

### 5.3.2 ID Selector:

```CSS
#id-value {
  font-style: italic;
}
```

The ID value would style any elements that have the corresponding ID, generally you'd want to use classes when you can.
### 5.3.3. Class Selector:

```CSS
.large {
  font-size: 24pt;
}
```

The class selector matches any elements who have been assigned a similar class.
### 5.3.4. Attribute Selector:

```CSS
[id] {
  font-weight: bold;
}
```

An attribute selector enables you to select and attribute that is set on an HTML element to style it. So in this case, any element that has an `id` attribute would be emboldened.

```CSS
[data-role=warning] {
  color: red;
}
```

Another trick of the attribute selector is that it can style attributes that have been set to a specific value. So in this case, any element that has the attribute `data-role` with the value of `warning` is made red.

## 5.4. Combining CSS Selectors:

Now that we have the main building blocks, we can actually combine them together for more complex outputs, there are loads of these, but the most common ones are:
### 5.4.1. Same-element Combinator:

```CSS
h2.aside {
  font-size: 10pt;
}
```

This combinator occurs when we specify multiple selectors with no whitespace, what this does is only match HTML elements that meet all of the selectors.

In this case, any `<h2>` tag with the class `aside` would have its font size decreased.
### 5.4.2. Descendant Combinator:

```CSS
ul li {
  list-style-type: none;
}
```

This is a very typical combinator. It is used to select elements which are contained within another element.

In this case, within any unordered list, each list item (bullet point) will be removed.
### 5.4.3. Child Combinator:

```CSS
ul > li {
  list-style-type: none;
}
```

This is similar to the descendant combinator, it modifies any list item that is a direct child. This is different than the decedent combinator, as it wouldn't modify an element if another tag was in between.

***
# 6. Selector Specificity:

We can use various ways of CSS styling rules that match elements:

```CSS
h2 {
  font-family: "Poppins", Arial, sans-serif;
  font-size: 12pt;
}

aside h2 {
  font-size: 10pt;
}
```

CSS will resolve certain rules ahead of one another, the hierarchy of these rules is as followed:

1. ID selectors.
2. Class, attribute, pseudo selectors.
3. Element selectors.

```CSS
.big {
  font-size: 24pt;
}

#focus {
  font-size: 36pt;
}
```

In this example, text with the focus ID would override the big class, since ID > Classes in the CSS styling rules.

***
# 8. CSS Frameworks:
Writing CSS rules by hand is slow, and much of CSS frameworks are repeatable, so CSS frameworks were made. Popular frameworks include:
- Bootstrap
- Foundation
- Tailwind CSS

This module uses tailwind CSS. Which is a **utility-first CSS** approach. Which basically means, that Tailwind CSS has many CSS class components built into it, you can use multiple smaller chunks of classes to create complex design.

This leads to smaller CSS file sizes as only the CSS rules actually used are copied to the generated CSS file and help with JavaScript Frameworks.

### 8.1. Styling with Tailwind:
Consulting the [Tailwind CSS documentation](https://tailwindcss.com/docs/styling-with-utility-classes) is key here.

#### Example: Traditional CSS Vs Tailwind CSS

**Traditional CSS approach:**
```html
<!-- HTML -->
<button class="custom-button">Click Me</button>

<!-- Separate CSS file -->
<style>
.custom-button {
  background-color: #3b82f6;
  color: white;
  font-weight: bold;
  padding: 0.5rem 1rem;
  border-radius: 0.375rem;
  border: none;
}

.custom-button:hover {
  background-color: #2563eb;
}
</style>
```

**Tailwind CSS approach:**
```html
<!-- Everything in one line using utility classes -->
<button class="bg-blue-500 text-white font-bold py-2 px-4 rounded hover:bg-blue-700">
  Click Me
</button>
```

**Common Tailwind Utility Classes:**
- **Layout**: `flex`, `grid`, `block`, `inline`, `hidden`
- **Spacing**: `m-4` (margin), `p-4` (padding), `space-x-2` (gap between items)
- **Sizing**: `w-full` (width 100%), `h-screen` (height 100vh), `max-w-4xl`
- **Typography**: `text-xl`, `font-bold`, `italic`, `text-center`
- **Colours**: `bg-blue-500`, `text-gray-700`, `border-red-300`
- **Borders**: `border`, `border-2`, `rounded`, `rounded-lg`
- **Effects**: `shadow-lg`, `hover:bg-blue-700`, `transition`

***
# 9. TypeScript:

TypeScript extends JavaScript with type information. Though in this module, we aren't using most of TypeScript's capabilities. Just the basic processes of TypeScript.

For example:
```TypeScript
const MESSAGE: string = "Hello ";
let userName: string = "Alex";

console.log(MESSAGE + userName);
```

Would work, but must be compiled into JavaScript so it can be executed, we can do this like so:

```Bash
npm ci
npm run compile example.ts
node example.js
```

## 9.1. Catching Type Errors:

```TypeScript
function combine(a: number, b: number): number {
    return a + b;
}

console.log(combine(3, 4));

$ npm run compile functions.ts
$ node functions.js
```

Within TypeScript, unlike pure JS, we can specify that the inputs **must** be numbers and that the output must be a number as well.

If we were to perform the following: `console.log(combine("3", "4"));` Our code would crash, as we've tried to combine strings, when numbers are expected.

***
# 10. Legal Aspects:

- **Accessibility and Usability:** Accessibility is part of usability and user experience. A site with accessibility issues also has usability and UX issues. However, accessibility is distinct because it is a **legal requirement**.
    
- **Legal Framework (UK):**
    - Governed by the **Equality Act 2010** (and the **Disability Discrimination Act 1995** in Northern Ireland).
    - All **websites are considered services**, so anyone running a website is a “service provider” legally required to make “reasonable adjustments” for accessibility.
    - Only exceptions are cases where adjustments would be a **“disproportionate burden”**, though this is now rare due to modern technology.
        
- **Reasonable Adjustments (Equality Act 2010):**
    - Take steps to ensure **equal experience** and remove disadvantages for disabled users.
    - Fix **physical or digital barriers** that cause disadvantage.
    - Provide **auxiliary aids** where needed to achieve equality.
        
- **Case Study Application:**
    - Adjustments must be made for blind or partially sighted users.
    - Adjustments may be limited if a user’s disability makes independent use of a service impossible (e.g., complex shipping tasks for users with severe learning difficulties).
        
- **Technical Standards:**
    - **BS 8878 (2010)** – UK guideline recommending accessibility-focused design, clear responsibility, continuous review, and testing.
    - **WCAG (ISO/IEC 40500)** – International standard giving detailed technical guidance (currently version **2.2**).
    - **Public Sector Requirement (since 2018):** Public websites/apps must comply with **WCAG 2.1 Level AA**. This is a sensible **baseline** for all sites aiming for compliance.

In essence, meeting the WCAG guidelines as set by your employer, organisation, or clients is going to be key to succeeding as a developer.

## 10.1. Business Aspects:

Being accessible is a business driver, if you can appeal to those who are disabled and make your services better for them by improving their user experience, you can tap into that market and have an advantage.

Add to the fact that those who are disabled are more likely to access online resources, makes accessibility even more important.

It's easier to make changes digitally, than physically.

## 10.2. Web Content Accessibility Guidelines:

The W3C also does standardization for the WCAG (Web Content Accessibility Guidelines). This is defined by four key aspects:

- **Perceivable:** information and user interface components must be presentable to users in ways they can perceive. This covers aspects such as providing text-based alternatives for video/audio content, but also colour choices, colour contrast, font sizes, and related properties.
- **Operable:** user interface components and navigation must be operable. The primary aspect here is that a user interface must be operable and navigable via the keyboard only, but also that users are given enough time to interact with the system, that the interaction patterns do not trigger any kind of seizures or physical reactions.
- **Understandable:** information and the operation of user interface must be understandable. This means that the language used should be appropriate for the target audience, but also that the interaction patterns can be predicted by the user and that the user is provided with understandable support to avoid and correct any mistakes.
- **Robust:** content must be robust enough that it can be interpreted by a wide variety of user agents, including assistive technologies

There are three levels of conformance:

- **A:** the most basic level of conformance. Conformance with this level will alleviate the worst accessibility issues, but accessibility hurdles will remain for many users.
- **AA:** the ‘standard’ level of conformance. As mentioned earlier, this is the level that is generally seen as achieving legal compliance level and will ensure that the majority of users with accessibility needs can fully use the website.
- **AAA:** the highest level of conformance. Conformance with this level will ensure that only a very small sub-set of accessibility needs will not be satisfied.

You can use certain tools to check a accessibility:

- **WAVE** or **axe DevTools**
- Manual testing
	- Check all functions can be access with Tab/Enter
	- Check Colour contrast using WebAIM Contrast Checker.
	- Brief Screen reader test (NVDA or Voice over.)

This is enough, for non-audits.

***
# 11. ARIA (Accessible Rich Internet Applications):

The WCAG doesn't provide tools on how to improve the accessibility of website. But ARIA rules do, modern websites that use dynamic and interactive features, that without additional markup can't function for disabled users.

ARIA provides web developers with a few main elements:
- Roles to describe the type of widget an HTML element provides.
- Roles to describe the structure of a web page
- Properties to describe the state of widgets.
- Properties to define live regions of the page.
- A definition for how keyboard navigation for these aspects should be implemented.

Most available roles cover five main categories:
1. [**Widget roles:**](https://www.w3.org/TR/wai-aria-1.1/#widget_roles) are used to identify user interface widgets and includes specific roles such as buttons, menus, menu items or grids.
2. [**Document structure roles:**](https://www.w3.org/TR/wai-aria-1.1/#document_structure_roles) describe roles used to structure the content in the page and cover aspects such as articles, tables, lists or headings.
3. [**Landmark roles:**](https://www.w3.org/TR/wai-aria-1.1/#landmark_roles) are similar to document structure roles, but represent navigational landmarks within the page that are often used by assistive technologies to provide fast navigation through the page. These include roles such as the banner, form, main, navigation or search.
4. [**Live region roles:**](https://www.w3.org/TR/wai-aria-1.1/#live_region_roles) indicate to the assistive technology that the content is an area that is frequently updated, including roles such as alert, log, status and timer.
5. [**Window roles:**](https://www.w3.org/TR/wai-aria-1.1/#window_roles) represent elements that are acting as windows within the browser, such as dialogs.

Most roles within HTML are implicitly granted. So the button element has the button role automatically applied to it.

- **ARIA properties** (all starting with `aria-`) provide extra information about an element’s **content, state, or purpose** to assistive technologies like screen readers.
- **Static attributes** (e.g., `aria-label`) describe elements that have no visible text, helping screen readers convey meaning (e.g., labelling an image-only button).
    - Example: `aria-label="Close the dialog"` makes a button with an image accessible.
    - `aria-hidden="true"` hides elements (like decorative images) from assistive technologies.
- **Dynamic attributes** (e.g., `aria-checked`, `aria-selected`) reflect **changing states** of interactive elements as the user interacts with them.
- **ARIA Authoring Practices Guide** provides **implementation patterns and best practices**, ensuring developers use ARIA roles and properties correctly.
- **Use ARIA only when necessary** — incorrect or incomplete implementation (e.g., using a `menubar` role without proper keyboard navigation) can **worsen accessibility** rather than improve it.
- **Modern frameworks** (e.g., React, Angular) increasingly **include ARIA functionality by default**, reducing the burden on developers and helping maintain accessibility standards.

***

# 12. ARIA Examples:

## 12.1. Skip Link:

Modern web apps have lots of navigation content at the top of the page, for disabled users who need to use the keyboard to navigate, they need a better way as they lose a lot of time.

We can implement skip links that will skip to the generally recommended content. We can use the functionality of the `Tab` key to do this.

### Why This Works:

Buttons can always be focussed using the keyboard, but to move the focus to the main content, we need to tell the browser that the `<main>` element can be focussed on.

This is done through modifying the `tabindex` property and setting it to `-1`, what this does is ensure that the content can be focused by JavaScript, but not via `Tab`.

The script necessary for this is svelte would be:
```TypeScript
<script lang="ts">
  import { onMount } from "svelte";
  onMount(() => {
    (document.querySelector("body") as HTMLElement).focus();

    const SKIP_LINK_BUTTON = document.querySelector(
      "#skip-link",
    ) as HTMLButtonElement;
    SKIP_LINK_BUTTON.addEventListener("click", (ev: Event) => {
      (document.querySelector("#content") as HTMLElement).focus();
    });
  });
</script>
```

All our JS code is placed inside an anonymous function, which is passed into svelte through the `OnMount()` function. This means that when the HTML is loaded, that the script also runs.

### Styling the Button:

We don't want this button to be displayed for all users, only those using the keyboard to navigate, we can do this if the `Tab` button is pressed, using the following CSS implementation:

```HTML
  <button
    id="skip-link"
    class="sr-only focus:not-sr-only focus:absolute focus:top-0 focus:left-1/2 block transform -translate-x-1/2 focus:px-4 focus:py-2 bg-yellow-400 border border-blue-800 rounded-b"
    >Skip to content</button
  >
```

***

# 13. Accessible Toolbars:

Now that we've gotten the tab navigation to main content working, we now can use a toolbar. A toolbar is frequently used to provide quick access and functionality.

The two main issues of an regular toolbar would be:
1. Images are often used to represent functionality.
	1. This doesn't work for visually impaired users.
2. Toolbars are often expected to support arrow keys.
	1. Browsers don't support this by default.
## 13.1. Key Accessibility Features for Buttons

- **`tabindex="0"`**: Makes the button focusable when users tab through the page
- **`aria-pressed`**: Indicates button state (pressed/not pressed) for screen readers, toggling between "true" and "false"
- **`aria-label`**: Provides text descriptions for icon-only buttons so screen readers can announce their purpose

## 13.2. Keyboard Navigation

The toolbar implements arrow key navigation using JavaScript:

- Finds all buttons within elements marked with `role="toolbar"`
- Adds keyboard event listeners to each button
- **Left arrow**: Moves focus to the previous button (if not already on the first)
- **Right arrow**: Moves focus to the next button (if not already on the last)

## 13.3. Styling Benefits

The document demonstrates using ARIA attributes for CSS styling, which serves dual purposes:

- Style elements based on their accessibility state (e.g., `button[aria-pressed="true"]` changes background colour when pressed)
- Reduces the need for additional CSS classes by leveraging existing accessibility attributes

## 13.4. Recommendation

While this implementation covers the basics, the document recommends using established accessible UI libraries rather than building everything from scratch, as they provide fully compliant components with more comprehensive functionality.

These include:
- **Chakra UI** - Simple, composable components with accessibility as a priority (1.4 million downloads per month) [MakeUseOf](https://www.makeuseof.com/react-component-libraries-build-accessible-applications/)
- **Material UI (MUI)** - One of the most popular with 80k+ GitHub stars, follows Google's Material Design with accessibility as a core priority. [MakeUseOf](https://www.makeuseof.com/react-component-libraries-build-accessible-applications/)
- **Headless UI** - Fully accessible components with pre-styled examples via Tailwind UI. [MakeUseOf](https://www.makeuseof.com/react-component-libraries-build-accessible-applications/)
***
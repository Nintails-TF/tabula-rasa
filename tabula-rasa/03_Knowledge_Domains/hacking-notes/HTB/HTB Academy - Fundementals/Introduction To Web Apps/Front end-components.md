---
title: 'Front end-components:'
updated: 2023-04-06T10:21:27.0000000+01:00
created: 2023-04-03T16:20:25.0000000+01:00
---

URL encoding:

An important concept to understand regarding HTML is **percent-encoding/URL encoding.** For e browser to display the contents of a page, it needs to know what character set is in use. Browsers can only use **ASCII** encoding - which only allows alphanumeric characters and a few special characters.

This means that all characters outside of ASCII, must be encoded **within the URL** using a % symbol + two hex digits. For example a single quote (') is encoded to (%27).

URLs also cannot have spaces and each space will be replaced with a +. Common characters that are encoded within the URL are:
![image1](../../../../_resources/image1-105.png)
(A full reference guide: <https://www.w3schools.com/tags/ref_urlencode.ASP>**)**

BURP suite can be used to decode as well.

Usage of URL decoding:

The **\<head\>** tag often contains elements that are not directly printed on the page. Every tag like \<body\>, \<style\> and \<script\> contribute to the **DOM** or **Document Object Model** of a page.

*"The W3C Document Object Model (DOM) is a platform and language-neutral interface that allows programs and scripts to dynamically access and update the content, structure, and style of a document."*

There are 3 types of DOM:

**Core DOM:** *The standard model for all document types.*
**XML DOM:** *The standard model for XML documents.*
**HTML DOM:** *The standard model for HTML documents.*

The DOM can be used to filter and perceive the web page in a technical manner, that is still digestible and allows us to filter for specific features.

This makes DOM a useful tool when searching for front-end vulnerabilities (like XSS).

CSS Frameworks:

Popular CSS frameworks include:

- Bootstrap
- SASS
- Foundation
- Bulma
- Pure

It often makes sense to check for CSS frameworks, as older more outdated pages, could use old versions of frameworks that have vulnerable JavaScript Components.

JS usage:  

JavaScript is mainly used to automate complex processes and to perform HTTP requests to interact with the back end components to send and retrieve data via technologies like **Ajax.**

JavaScript is used alongside CSS, as previously mentioned to drive advanced animations. All modern web browsers are equipped with JS. JavaScript achieve a large number of processes quickly.

**Pure JavaScript** is slow in developing applications, so we have **JavaScript** frameworks that allow us to quickly develop applications, popular frameworks are:

- Angular
- React
- Vue
- jQuery


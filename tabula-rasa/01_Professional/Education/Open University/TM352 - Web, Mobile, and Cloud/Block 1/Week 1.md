---
date created: Monday, November 10th 2025, 11:04:09 am
date modified: Tuesday, November 11th 2025, 11:46:14 am
---

# 1. Introduction:

The purpose of this first block is to build some foundational skills required for the rest of the module as well as getting used to the technology used within the module.

This mainly refers to the **OpenComputing Lab** which is a cloud service that the OU runs.

***
# 2. Aims:

- accessed all the resources you will use in this block
- been introduced to the OpenComputing Lab, which you will use to undertake the block’s practical activities
- gained an awareness of what software is required, if you wish to undertake the practical activities on your own hardware.

***
# 3. OpenComputing Lab:

The **OpenComputing Lab** (OCL) is an online pre-configured suite of tools provided by the open university. It's the environment where assignments are tested, so it's best practice to do work within it and get used to it.

See [[OCL - OU Notes]] for more details on OCL configuration or quirks. It generally seems quite simple to setup, you get dropped into a vscode environment.

***

# 4. Weekly Tasks:

## 4.1. Exploring the Virtual Coding Environment:

The **Virtual Coding Environment** (VCE) opens in the `block_1` folder, that you'd usually want to stay in. The structure of the folder is:

- `skeletons` - Includes templates and example pieces of work
	- Note that this will be overwritten and replaced with defaults if you change anything during instance spawning. e.g. Don't save your work here.
- `work` - This is your working area for all Block 1 activities.
	- This space is persistent throughout sessions.

Generally, you'll be asked to copy a piece of work from the skeleton, analyse the code and copy it into your `work` and make changes on it. You can always scrap and replace your work with the skeleton templates if you get stuck.

### 4.1.1. The VCE Interface:

Make sure you do trust the authors of the module, it ensures that things work as they are suppose to. You can copy folders using:

```Bash
# Copying Folders:
cp -r ../skeletons/aria-example . # Copy the aria-example to current dir (work)
cp -r ~/block_1/skeletons/aria-example . # Copy the aria-example, absolute path, so works anywhere.

# Deleting folders
rm -r aria-example # Be careful when doing this.
rm -r ~/block_1/work/aria-example # Absolute example.
```

Another handy tip, is that you can either **upload** or **download** files by right-clicking a folder and picking the corresponding option.
## 4.2. Running Locally with Podman Desktop:

This isn't required, so I'm not actually going to do this. But the section on architecture is actually interesting. It's just if you have bad internet.

### Architecture:

A key problem in software is making repeatable software environments. This is since if we are distributing software, each system can act slightly differently leading to crashes or bugs. **Virtual Machines** are made into images to help solve this problem.

Multiple VMs can be produced on a machine, but there ends up being lots of redundancy. So **containerisation** started occurring.

- **Virtual Machines**
	- VMs run on hypervisors like VMware or VirtualBox which sit between the hardware and VM.
	- Each VM is isolated with its own kernel, system library, and resources.
	- Heavy - A single VM is several GBs since it holds an OS and is more system intensive.
- **Containers**
	- Containers share the host operating system kernel, this is almost always some Linux based kernel.
	- They run in container engines like Docker.
	- They are light - MBs rather than GBs

Containers have a greater security risk since they are less isolated from the system kernel. There is a work in progress to make containers more secure. Both are useful in different situations:

1. VMs for underlying infrastructure and strong isolation between workloads and systems.
2. Containers running inside of VMs for application development and scaling.

This is a simplistic way of how Kubernetes work typically work, since you get the advantages of both VMs and containers.

## 4.3. JavaScript Basics:

TM352 uses a fair amount of JavaScript, so a quick crash course is covered.
### Outputting Content:

```JavaScript
console.log("Hello!");
// node outputting-content.js - We use this to run the code.
```

Some key features of JS are that:
- JS is OOP. So in our example: `console` is and object and we call the method `log`.
	- Functions and methods both require brackets.
	- Function returns something, method's don't.
- Node is a JavaScript engine, so it's an interpreter that executes JS on a back-end server rather than a browser.
- **Ensure that speech marks are doubled** - This is what the course expects.
	- Enclose using `;`
### Variables and Constants:

#### Variables:
```JavaScript
let a;
let b = 4;

a = 3;

console.log(a);
console.log(b);

a = a + b;

console.log(a);
// node variables.js to run
```

The keyword of`let`is used to define a variable. You can define variables with or without a value - any variable defined without a value is initially assigned `undefined`. 

A value of `undefined` can be assigned in many other cases, such as *trying to call a non-existent object, not calling a missing function parameter, functions without explicit returns.*

This is somewhat of a drawback of JavaScript, as it can allow bugs to get through without people realising, as it can accept silent failures. This is why **TypeScript** is a bit stronger and why Linters are used.

`undefined` is different than `null`, since `null` is intentionally assigned as an absence of a value.

#### Constants:
```JavaScript
const A = 3;
const B = 4;

const C = A + B;

console.log(A);
console.log(B);
console.log(C);
// To run: node constants.js
```

Constants act similarly to variables, but they cannot be changed, thus they must be initially defined. e.g. `const A;` would result in an error.

Naming conventions are as followed:
	- Variables are lower case: `let year = 2025;`
		- Multi-word variables use camel-case: `let currentYear = 2025;`
	- Constant are upper case: const `const YEAR = 2025;`
		- Multi-word constants use underscores: `const CURRENT_YEAR = 2025`

### Functions:
```JavaScript
function sum(a, b) {
    return a + b;
}

const RESULT = sum(3, 4);
console.log(RESULT);
// To run: node basic-function.js
```

All functions in JavaScript return a value, even if you specific it or not. In this case, the function of `sum` returns the value of two inputted variables.

Functions in JavaScript are also known as **first-class elements.** Meaning, that functions can be passed as parameters into other functions. Which is a pattern frequently seen in development.

### Functions as Parameters:

```JavaScript
function sum(a, b) {
    return a + b;
}

function sub(a, b) {
    return a - b;
}

function math(a, operator, b) {
    return operator(a, b);
}

function mult(a, b){
    return a * b;
}

const TOTAL = math(3, sum, 4);
const DIFF = math(3, sub, 4);
const FACTOR = math(3, mult, 4)

console.log(TOTAL);
console.log(DIFF);
```

We can see in this example, that we have the function of `math` which takes in two sets of numbers and a function, that function then performs a mathematical operation on them, 

e.g. `math` will start a function call to the corresponding operator function (`sum, sub, or mult`) and then return the result, which is stored in one of the const.

### Anonymous Functions:

```JavaScript:
function math(a, operator, b) {
    return operator(a, b);
}

const TOTAL = math(3, (a, b) => { return a + b; }, 4);
const DIFF = math(3, (a, b) => { return a - b; }, 4);

console.log(TOTAL);
console.log(DIFF);
```

If you need to pass a function as a parameter, typically you only need to use it once, this is where **anonymous functions** come into play. If we wanted to call this function elsewhere in code, we'd be better of making it's own function.

***

# 5. Case Studies:

Case studies are given throughout the module in order to test certain skills or abilities. As certain jobs require different techniques and skills.

## Music Streaming Service

‘Sounds Good!’ is a young music streaming service, that aims to fulfil all its listeners’ music tastes, while ensuring that artists receive royalties that allow them to live. As such, while they deal with artists and music labels in the background, they are primarily a customer-focused business, delivering their services both via the web and via a custom mobile-app. Because they are a young business, they can pick and choose the most appropriate current technologies, without having to take account of any legacy systems. They are aiming to quickly grow this business, thus reactivity and quick development cycles are a central aspect of the business.

## Shipping Management

‘Mercury’ is a well-established shipping company, providing shipping and fulfilment services to a wide range of businesses. Businesses using Mercury’s services can use their website or APIs to generate fulfilment and shipping actions and then also provide tracking information via their APIs. They were an early adapter of digitisation in the business-to-business world. Due to this and the narrow margins in the shipping business, they have amassed a significant number of legacy systems that need to be supported. This business area is heavily dependent upon trust, thus Mercury are very focused on ensuring any developments do not negatively impact the stability of their systems.

***









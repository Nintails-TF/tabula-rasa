---
date created: Friday, December 19th 2025, 12:08:55 pm
date modified: Friday, January 30th 2026, 4:16:42 pm
Gen: "1"
---

# Week 11 - Mobile Devices:

## 1. Introduction:

This week examines more closely the technologies that make up a mobile device, including hardware components, network connectivity, and software. We will also examine mobile applications and compare the characteristics of mobile devices with desktop computers.

**Resources Required:**
- A computer with internet connectivity
- Google Chrome web browser (for developing a simple mobile web application)

---

## 2. Aims:

**Learning Outcomes:**

- Compare and contrast the characteristics of mobile devices and desktop computers
- Examine the hardware technologies that make up a mobile device
- Describe mobile operating systems and the architecture of application software
- Describe the differences between mobile and fixed devices in terms of their user behaviours and operating contexts

---

## 3. Invisible Computer:

In 1998, usability expert and former head of Apple Research Laboratories, **Donald Norman**, predicted a rise in 'information appliances'. He envisioned devices designed to perform one specific function that would be:

- Simpler and much easier to use
- Easier to maintain
- More popular than PC counterparts

**Key Characteristics of Norman's Information Appliances:**

- Human-centred, providing a close fit between user and task
- Not all-purpose computing machines
- Would contain a computer, but hidden away ("invisible")
- Users would be unaware of its presence
- Connectivity between devices (though Norman envisioned device-to-device, not cloud connectivity)

**Examples of "Invisible Computers":**

- Satnavs
- Digital cameras
- E-readers
- Amazon Dash buttons
- Embedded systems in packaging (RFID)

These devices don't contain "computer" in their name, have few user-serviceable parts, and users aren't encouraged to open them (even to replace batteries).

### 3.1. Trade-Offs:

**Disadvantage of Specialisation:** One device for one task means multiple devices for multiple tasks - this is inconvenient and costly. Who wants to carry fifteen devices when they could carry one?

**The Trade-Off Spectrum:**

|Aspect|Specialised Devices|Multi-Purpose Devices|
|---|---|---|
|Ease of use|✓ Higher|Lower|
|Simplicity|✓ Higher|Lower|
|Cost|Higher (multiple devices)|✓ Lower (one device)|
|Convenience|Lower|✓ Higher|

**Smartphones and Tablets:** Fall in the middle ground between Norman's invisible computer (information appliance) and the visible computer (multi-purpose PC). They represent a compromise that works for many users, though some will always prefer dedicated devices for specific tasks like photography, reading, or navigation.

### 3.2. Mobile Computing:

**What does "mobile" actually mean?**

Consider whether these qualify as "mobile computing":

- A PC that can be unplugged and moved between rooms?
- A laptop?
- A tablet?
- A smartphone?
- A feature phone?
- An old Nokia 3310 running Snake?

**Classifying Mobile Devices:**

|Device|Mobile Computing?|Invisible Computer?|
|---|---|---|
|Wired PC (movable)|Debatable - limited|No|
|Laptop (field use)|Yes|No|
|Smartphone|Yes|No|
|Pager|Limited|Yes|
|Digital camera|Limited|Yes|
|Pocket calculator|Limited|Yes|
|RFID chip|Yes (embedded)|Yes|
|Satnav|Yes|Yes|
|Handheld games console|Yes|Partial|
|Smart watch|Yes|Partial|

**Focus of TM352:** Smartphones and tablets, because:

- Most familiar and versatile mobile devices
- Creating applications is relatively straightforward (computers not embedded)
- Manufacturers compete to include established and emerging technologies (accelerometers, contactless payment, NFC)

**Three Areas of Mobile Technology:**

1. Hardware
2. Networks
3. Software

---

## 4. Hardware Characteristics:

Mobile devices differ substantially from desktop devices to optimise portability.

### 4.1. Screen:

The most obvious difference between smartphones/tablets and desktop devices is screen size. Example comparison:

- Work computer: 27-inch screen
- Samsung Galaxy Note 4: 5.7-inch screen

How a web page appears depends on: screen size, resolution, pixel density, and viewing distance.

#### 4.1.1. Screen Size:

**Definition:** Physical dimensions of the screen, typically measured in inches diagonally (corner to opposite corner).

**Implications of Small Screens:**

- Less room for display
- Overcome by scrolling (swipe gesture - horizontal or vertical)
- Scrolling down is more natural but still tiresome
- Ideally, users should perform important operations without scrolling through many screens

**Design Considerations:**

- Clearly identify the site's purpose - what are users coming to do?
- Organise pages to focus on one or two clearly identified outcomes
- Guide users screen by screen to task completion
- Avoid large pages dense with options, images, and content (suitable for desktop, frustrating on mobile)

#### 4.1.2. Resolution:

**Definition:** The number of pixels along horizontal and vertical axes, expressed as width × height (e.g., 1366 × 768).

**Key Concept:** A pixel is the smallest indivisible unit from which an image can be built. Higher resolutions mean more detail.

**Resolution Comparison:**

|Resolution Level|Pixels|Total Pixels|
|---|---|---|
|Lower|4 × 4|16|
|Middle|16 × 16|256|
|Higher|64 × 64|4,096|

**Trade-off:** Higher resolutions offer greater detail and are more pleasing to the eye, but require more processing power and memory, consuming more power.

#### 4.1.3. Pixel Density:

**Definition:** The number of pixels per inch (PPI) of screen display. Combines screen width (inches) with resolution (pixels).

**Why it matters:** Allows comparison of resolutions across devices with different screen widths.

**Example Comparison:**

|Device|Screen Size|Resolution|Pixel Density|
|---|---|---|---|
|iPhone 4|3.5"|960 × 640|~326 PPI|
|HTC Wildfire S|3.2"|480 × 320|~180 PPI|

**Retina Display:** Apple considers any pixel density above 300 PPI to be indistinguishable to the naked eye at normal mobile viewing distances (10-12 inches). Other manufacturers use 400 PPI as the threshold.

**Rule:** The higher the pixel density, the sharper the mobile display.

---

### 4.2. Central Processing Units:

**Mobile vs Desktop Processors:**

|Platform|Processor Type|Architecture|
|---|---|---|
|Mobile devices|ARM Holdings|RISC|
|Servers, desktops, laptops|Intel/AMD x86|CISC|

**RISC vs CISC:**

- **RISC** (Reduced Instruction Set Computer): Simpler instructions, fewer transistors per instruction
- **CISC** (Complex Instruction Set Computer): More complex instructions, more transistors per instruction

**Note:** RISC doesn't necessarily have fewer total instructions - it's the complexity of each instruction that's reduced.

**Transistor Comparison:**

|Processor|Transistors|Features|
|---|---|---|
|Intel Core i9-12900K|3 billion|16 cores|
|A16 Bionic (iPhone 14 Pro)|16 billion|6-core CPU, 5-core GPU, 16-core Neural Engine, onboard RAM|

Mobile processors pack more into a single chip (GPU, Neural Engine, RAM), while desktops use discrete components.

**Advantages of Fewer Transistors (RISC):**

- Lower power consumption
- Less heat generation
- Cheaper to manufacture
- Ideal for mobile devices and embedded computers

**Why ARM Dominates Mobile:**

- Intel and AMD focused on desktop competition
- Neither considered mobile market significant initially
- Intel's Atom (low-voltage x86) succeeded in netbooks but not smartphones
- ARM architecture used in over 95% of mobile phones
- Android and iOS dominate, so Windows compatibility isn't crucial

**Important:** ARM doesn't manufacture chips - it licenses designs to Samsung, Qualcomm, Taiwan Semiconductors, etc.

**Code Compatibility:** Applications compiled for ARM won't run on Intel x86 machines - they must be compiled for different instruction sets.

---

### 4.3. Memory and Storage:

**RISC Memory Requirements:** Although RISC processors need fewer transistors, they typically require more memory for programs (simpler instructions = more instructions needed for same result).

**Storage Differences:**

|Aspect|Mobile|Desktop|
|---|---|---|
|Primary storage|Flash memory (internal)|Hard disk or SSD|
|External storage|SD card (Android/Windows), None (iOS)|Multiple options|
|Capacity|Up to 512GB (expensive)|Multiple TB common|
|Cost per GB|Higher|Lower|

**Cloud Storage:** Because memory is limited, mobile devices frequently use cloud storage for large files (especially images).

**Advantage of Memory-Based Storage:** Programs and data stored in memory (not hard disk) means mobile apps launch quickly compared to desktop applications.

---

### 4.4. Energy Consumption:

Mobile devices need power supplies independent of mains electricity. Battery constraints affect:

- Size, weight, and bulk of device
- Device mobility
- Recharge frequency
- Battery lifespan and replacement cost

**Historical Context - Motorola DynaTAC 8000X (1984):**

- First commercially available mobile phone
- Weighed nearly 1 kilogram
- 30 minutes of use
- 10-hour recharge required
- The original "brick" phone

**Battery Technology Progress:**

- Batteries are now smaller, lighter, last longer, and charge faster
- However, battery technology hasn't kept pace with processor development
- **No Moore's Law for batteries** (Moore's Law: processor transistors/speed doubles every 18 months)

**Two Approaches to Energy Management:**

1. **Improving battery technology**
2. **Reducing device power consumption**

**Power-Saving Techniques:**

**Dynamic Frequency Scaling:**

- CPU clock frequency varies based on workload
- "Underclock" when phone not in use
- Increase frequency when applications launch
- Lower frequencies = lower voltages = less power

**Core Shutdown:**

- Multi-core processors can shut down unused cores
- Saves significant energy when full processing power isn't needed

---

### 4.5. Geolocation:

**GPS (Global Positioning System):** Refers to satellites that pinpoint geographical locations (operated by US government). Now used as a generic term.

**Alternative Geolocation Systems:**

- GLONASS (Russia)
- BeiDou (China)
- Galileo (EU)
- Quasi-Zenith (Japan)
- NavIC (India)

**Indoor Positioning:** When GPS signal unavailable (inside buildings), WiFi signals and SSID stations known to ISPs can provide geolocation.

**Applications:** Map applications can guide users from current location to destination.

**Privacy Considerations:**

- Location sharing can be perceived as a privacy risk
- Important to inform users of potential risks
- Obtain consent before collecting geolocation data
- Additional consent required for storing locations to remote services

---

### 4.6. Accelerometer:

Accelerometer sensors enable mobile devices to detect:

- Device orientation
- Speed of movement
- Direction of movement

**Common Uses:**

- **Screen rotation:** Adjust from portrait to landscape when device rotated (standard feature)
- **Step counting:** Count steps user walks
- **Physics-oriented applications:** Games, fitness apps

**Additional Sensors:**

- Pedometers
- Proximity sensors
- Ambient lighting sensors
- Depth sensors
- Facial recognition
- Fingerprint sensors

These sensors enrich user input and interaction capabilities.

---

## 5. Network Connectivity:

**Common Issues:**

- Unattainable mobile signal
- Dropped connections
- WiFi hotspots not readily available (often paid)
- Strict regulations on signal strengths and frequency spectrum
- Bandwidth issues during high usage (e.g., New Year's Eve)
- Network-intensive activities affected (video calling, streaming)

**Connectivity Options:** Modern mobile devices connect via WiFi, mobile networks, and various other protocols.

**Physical Wireless Architecture:**

- Base station (cellular communication)
- Router (passing packets)
- Sender/receiver (user end)

**Cellular Generations:**

|Generation|Trend|
|---|---|
|1G|Original analogue|
|2G|Digital, SMS|
|3G|Mobile data|
|4G|High-speed data|
|5G|Ultra-high bandwidth|

General trend: Increasing bandwidth with each generation.

**Network Types:**

|Technology|Range|Network Type|Characteristics|
|---|---|---|---|
|**Cellular**|Wide (cell stations)|WAN (Wide Area Network)|Relies on telecom infrastructure|
|**WiFi**|~300 metres|WLAN (Wireless Local Area Network)|IEEE 802.11 standard, higher bandwidth than cellular, requires base station|
|**Bluetooth**|<10 metres|PAN (Personal Area Network)|End-to-end between paired devices, no interference from other devices|
|**NFC**|Touch/near-touch|-|Near-field communication, used for wireless payment|

---

## 6. Software:

Mobile computers employ specialised software: mobile operating systems and dedicated application development frameworks.

### 6.1. Operating Systems:

**Major Mobile Operating Systems:**

- **Android** (Google) - Dominant market share
- **iOS** (Apple) - Significant market share
- **Windows 10 Mobile** (Microsoft) - Discontinued

**Windows Mobile History:**

- Microsoft attempted to unify desktop/mobile development with Windows 10 Mobile (2015)
- Remained behind Android and iOS in app availability
- Microsoft announced end of support (December 2019)
- Recommended users migrate to iOS or Android

---

### 6.2. Apps:

Mobile apps are the means by which users interact with their device. Without apps, the mobile device is useless.

**Pre-installed (Bundled) Apps:**

- Phone calls
- Text messages
- Web browsing
- Weather
- Email
- App marketplace (to download more apps)

When users think of "apps," they often think of downloaded apps rather than pre-installed ones.

#### 6.2.1. The Appeal of Apps:

**User Time:** Over 80% of time spent on mobile devices is using mobile apps.

**Why Apps Are Popular with End Users (Ingram, 2010):**

1. **Easy-to-use/secure payment systems**
    
    - Embedded systems (carrier billing, iTunes) allow real-time payment
    - Biometrics (fingerprints, iris scans) are personal
    - Avoids lengthy passwords or PIN codes
2. **Small price tags**
    
    - Most content and subscriptions under $5
    - Compared to expensive, bloated desktop software
3. **Walled gardens reduce piracy**
    
    - Content exists in proprietary environments
    - Difficult to get pirated content onto mobile devices
    - User protection against piracy and copyright infringement
4. **Established storefronts**
    
    - Carrier decks and iTunes store allow easy discovery and purchase
    - Single-touch purchasing
    - Smart recommendations based on past behaviour or similar users
5. **Personalisation**
    
    - More important on mobiles than desktops
    - Desktop limited by lack of information when not in use
    - Mobile devices carry personal information, enabling better personalisation

**Stakeholder Perspectives:**

|Stakeholder|Benefits of Apps|
|---|---|
|**Consumers**|Number and quality of apps is purchasing consideration|
|**Developers**|Monetisation, notifications, more functionality than web pages, full device capabilities|
|**IT Managers**|Personalised data/workflow management for employees, sophisticated IT policy enforcement|

---

## 7. 'On the Go' Meets 'Need It Now':

**Traditional View:** Mobile devices associated with accessing information on the move.

**Modern Reality:** Mobiles are used not just "on the go" but as a way of accessing information quickly, whether moving or not.

**Characteristics of Modern Mobile Use:**

- Always on, ever-connected
- Ready for use whenever needed
- Reach out for information regularly
- Well-suited for spur-of-the-moment activities

**"Need It Now" Behaviour:**

- Ad hoc micro-tasking
- Happens while sitting (e.g., in front of TV) as much as while out
- Used for distraction and boredom busting
- Second screen to look up information (quick and easy)

**Case Study: Urban Bus Navigator (UBN)**

The UBN app was developed as part of the GAMBAS (Generic Adaptive Middleware for Behavior-driven Autonomous Services) European research project.

**Internet of Things (IoT) Connection:**

- IoT describes the vision of billions of everyday objects with network connectivity
- Mobile devices (smartphones) could be central to IoT
- The UBN demonstrates how an app can include an urban bus in the IoT
- Uses WiFi to identify each bus
- Tracks bus position on journey (next bus stop)

**Academic Reading Strategy (from Activities):**

1. **Read title and abstract first** - get initial understanding
2. **Read introduction** - gather additional detail
3. **Read conclusion** - judge whether full paper is worth reading
4. **Skim-read main body** - locate information for specific questions
5. **Read thoroughly** - deep understanding of methodology and findings

---

## 8. Summary:

This week covered the specifics of mobile devices:

**Hardware Components:**

- Limited screens (for better mobility)
- GPS and geolocation systems
- Cameras
- Accelerometers and other sensors

**Key Comparisons (Mobile vs Desktop):**

|Aspect|Mobile|Desktop|
|---|---|---|
|Screen|Small, high PPI|Large, lower PPI|
|Processor|ARM (RISC)|Intel/AMD x86 (CISC)|
|Memory|Limited, flash-based|Large, HDD/SSD|
|Power|Battery, energy-efficient|Mains electricity|
|Connectivity|Cellular, WiFi, Bluetooth, NFC|Primarily Ethernet/WiFi|

**Software Considerations:**

- Browsers render content differently on mobile
- Many device configurations = more testing required
- Chrome DevTools enables mobile browsing emulation
- Mobile device emulators available as virtual machine images

**Where Next:** In the next part, you will study the creation of websites that work with mobile devices.

---

## 9. Key Terms Glossary:

|Term|Definition|
|---|---|
|**PPI**|Pixels Per Inch - measure of pixel density|
|**RISC**|Reduced Instruction Set Computer|
|**CISC**|Complex Instruction Set Computer|
|**ARM**|Advanced RISC Machine - dominant mobile processor architecture|
|**GPS**|Global Positioning System|
|**WAN**|Wide Area Network|
|**WLAN**|Wireless Local Area Network|
|**PAN**|Personal Area Network|
|**NFC**|Near-Field Communication|
|**IoT**|Internet of Things|
|**Dynamic Frequency Scaling**|Adjusting CPU clock speed based on workload|
|**Retina Display**|Apple term for displays with PPI above 300|

---

## 10. Further Reading:

- Norman, D.A. (1998) _The invisible computer_. Cambridge, MA: MIT Press.
- Ingram, M. (2010) 'Mary Meeker: mobile internet will soon overtake fixed internet', GigaOM.
- Tondare, S.M., Panchal, S.D. and Kushnure, D.T. (2014) 'Evolutionary steps from 1G to 4.5G', _International Journal of Advanced Research in Computer and Communication Engineering_, 3(4), pp. 6163–6166.
- IEEE 802.11 Wireless Protocol Standard: <http://www.ieee802.org/11/>

---
---
title: enr
date modified: Friday, May 17th 2024, 7:41:31 pm
---

I just moved into a new apartment that came prefurnished with a Vilo router. To set up the router, I downloaded Vilo's app from the App Store and connected to my router. However, I'm a naturally curious person so I wanted to see what data my app was sending the router, and figured out how to capture traffic going to the router. Unfortunately, it seems some messages are encrypted, so I'm hoping the APK file will shed some light on this.

What's the non-null `enr` value being sent to the router?

Flag format - `byuctf{enrvalue}`
***
## Introduction

We are looking at a real-world domestic router, by the company Vilio. They are routers that use a meshing system to prevent Wi-Fi cold spots in your house.

We are given two files:
1. enr.apk
	1. This is an android app package, which is the APK for the Vilo app.
	2. A popular method of inspecting this kind of file involves making it a [zip file then unzipping it.](https://stackoverflow.com/questions/3599210/how-to-view-the-contents-of-an-android-apk-file)
2. enr.pcapng
	1. This is a snapshot of the network traffic sent between the users router and phone.
	2. I know that I can open this and inspect this in **wireshark.**

***
## What are we looking for?

We are looking for *an non-null enr value, that is being sent to the router.* But what actually is an enr value?

**Environmental Noise Ratio** (ENR) is used to measure the level of interference or noise that is in the wireless environment. Since routers use radio signals to communicate over the air, enr is used to measure signal strength.

A high ENR indicates a better signal, whilst a low ENR indicates a worse signal. 

ENR is influenced by various factors such as:
 - Other wireless devices on the same frequency band.
 - Electrical interference.
 - Physical obstructions (walls, furniture).

ENR is used by routers to make better wireless adjustments to improve network performance.

**So we are looking the value of the signal strength being sent to the Vilio router.**
***
## Analyzing the pcapng:

We need to find out information about the ENR from the pcapng that we have found. This can usually be found within the **management or control frames** that carry information about the WiFi.

We can find this information in the **Beacon frames and the Probe Response frames**










---
layout: single
title:  "COVID Crisis Tech Remedies (May 2020)"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
With the "work-from-home" restriction imposed to counter COVID crisis, the chromebook became even more useless. It could neither run the desktop version of Zoom nor work with a drawing tablet. I believe these problems can be solved by enabling the Developer Mode and installing Ubuntu alongside ChromeOS, but I highly doubt that audio and other drivers will work in Ubuntu. However, since mobility is not desired anymore, I cdecided to build desktop PC with minimum possible budget (which turned out to be $650, same as the cost of the basic Pixelbook Go or an entry level ThinkPad with core i5 10th gen mobile).

# Performance
Following is the comparison of my PC with the best laptop available in the market in May 2020 for USD 650 (before tax):

| Specification | Custom build PC   | Acer Swift 3 (SF314-42-R9YN) |
| ------------- |:-----------------:|:----------------------------:|
|CPU            | AMD Ryzen 3 3200G (3.60 GHz x 4 cores, Zen+)    | AMD Ryzen 7 4700U (2.00 GHz x 8 cores, Zen 2)|
|iGPU            | AMD Radeon Vega 8  (1.25 GHz x 8 cores, Gen 8)  | AMD Radeon 7 (1.60 GHz x 7 cores, Gen 9)|
|RAM | 2 x 4 GB DDR4 2933 MHz                | 2 x 4 GB LPDDR4 4266 MHz|
|Storage| Crucial P1 500GB NVMe SSD  | Samsung PM991 512GB NVMe SSD|
|Ports| PS/2, 5 x USB 3.2, 4 x USB 2.0, DVI-D, HDMI, Audio In/Out, 2 x Mic| 1 x USB Type-C, 1 x USB 3.2, 1 x USB 2.0, HDMI, Headset/speaker jack|
|Network| Realtek 8111H Gigabit LAN | Intel Integrated WiFi 6 (802.11ax) and Bluetooth 5.0 |
|Audio| Realtek ALC892 Codec| Realtek Audio |
|Display | 21.5" 1920x1080 60Hz IPS with Eye Care and 2 stereo speakers| 14" 1920x1080 IPS with Bluelight Shiel and 2 stereo speakers|
|Webcam | 720p with mic| 720p with mic|
|Keyboard | Tenkeyless mechanical with Outemu Blue switches  | 60% chiclet with scissor switch and backlight|
|Pointing device | Wireless mouse | Touchpad |
|Warranty |  1.5 to 5 years depending on the part | 1 year|
|Bottomline | Sturdy and easy to repair | Mobility (0.71" thin and 2.65 lbs) |

Theoretically, Ryzen 7 4700U should be about 20% better than Ryzen 3 3200G for compiling LaTeX files ([single core performance](https://www.cpu-monkey.com/en/compare_cpu-amd_ryzen_3_3200g-952-vs-amd_ryzen_7_4700u-1093)). However, I have no complaints in terms of performance. The only headache is the lack of HDMI compatibility between the motherboard and monitor. Luckily, this time the Realtek ethernet drivers [didn't cause headache](https://tuxbyte.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/).


## Cloud Backup Setup in Ubuntu PC

# Build Details

| PC Part | Model   | MSRP before tax/shipping (round figure) |
| ------------- |:-----------------:|:----------------------------:|
||System Unit|
|CPU+GPU+cooler| AMD Ryzen 3 3200g | USD 100|
|Input/Output Devices|
|Keyboard | Redragon| USD 30|

Intel monopoly https://videocardz.com/newz/intel-faces-criticism-for-comparing-gaming-laptops-with-different-gpu-models

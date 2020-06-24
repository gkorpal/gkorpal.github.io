---
layout: single
title:  "Draft Post"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
## Pre COVID ##
The laptop that I got when I joined college 5 years ago was now old enough to be replaced. Mostly because I picked all the wrong specs when there was a choice (like Realtek vs Intel wireless, 2x4 GB RAM vs 1x8GB RAM, 48Wh vs 62Wh battery) and my lack of maintenance (never cleaned dust from inside or the rust from the ports). So I wanted something portable that can allow me to browse internet and write homework assignments in LaTeX. Following is the comparison of my new laptop (USD 375 before taxes) with the older laptop (USD 916 before taxes) :


| Specification | Asus Chromebook C425 (C425T) | Lenovo ThinkPad E440 (Custom build) |
| ------------- |:--------------------------------------:|:----------------------------:|
|CPU            | Intel Core m3-8100Y (1.10GHz x 2 cores, Amber Lake Y)    | Intel Core i7-4702MQ (2.20GHz x 4 cores, Haswell)|
|iGPU            | Intel UHD Graphics 615  (300MHz, Gen. 9 Amber Lake)  | Intel HD Graphics 4600 (400MHz, Gen. 7.5 Haswell)|
|RAM | Micron Technology 2 x 4GB LPDDR3 1866 MHz SO-DIMM            | SK Hynix 8GB PC3-12800 DDR3L SDRAM 1600 MHz SO-DIMM|
|Storage| 64GB eMMC 5.0 HS400 + 100GB Google One for 1 year (later $20/year) | Seagate 2.5" 500GB HDD, 7200rpm |
|Battery | 48 Wh | 48 Wh |
|Ports |  Audio jack (mic/headphone), 2 x Type-C USB 3.0 (display and power delivery support), Type-A USB 3.0, micro SD card reader | Audio jack (mic/headphone), 2 x Type-A USB 3.0, 1 x USB 2.0 VGA, HDMI, SD card reader (Realtek), Optical drive (PLDS DVD-RW), Lenovo OneLink connector (for docking) |
|Network| Intel Integrated WiFi 5 (802.11 ac (2x2)) and Bluetooth 5.0 | Realtek 8168E Gigabit Ethernet and Realtek 8723BE Integrated WiFi 4 (802.11 n) and Bluetooth 4.0 |
|Audio|  Dialog Semiconductor DA7219  Codec (for wired headset) and Maxim MAX98927 Codec (for speakers) | Conexant CX20751 SmartAudio HD |
|Display | 14" 1920x1080 60Hz AntiGlare IPS (45% NTSC) | 14" 1600x900 AntiGlare TN|
|Webcam | 720p with mic | 720p with mic |
|Keyboard | 60% chiclet with scissor switch and backlight | Thinkpad keyboard with TrackPoint pointing stick |
|Pointing device | Elan Microelectronics Touchpad | Synaptics Touchpad |
|Warranty | 1 year  | 1 year |
|Bottomline | Mobility (Fanless, 0.66" thin and 2.8 lbs) | Sturdy and easy to upgrade (user manual has full details) |

Core i7-4702MQ is about 10% better than Core m3-8100Y for LaTeX ([single core performance](https://www.cpu-monkey.com/en/compare_cpu-intel_core_m3_8100y-1216-vs-intel_core_i7_4702mq-448)). Howeover, the process is extremely slow since Debian runs in a virtual machine.

Had to replace the dying HDD with 250 GB SSD (2.5" SATA 6Gb/s). For budget PC expect low build quality and dim display.

https://tuxbyte.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/

## Post COVID ##
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
|Warranty |  2-5 years on expensive parts | 1 year|
|Bottomline | Customizability (optimized for Ubuntu and LaTeX) | Mobility (0.71" thin and 2.65 lbs) |

Ryzen 7 4700U is about 20% better than Ryzen 3 3200G for LaTeX ([single core performance](https://www.cpu-monkey.com/en/compare_cpu-amd_ryzen_3_3200g-952-vs-amd_ryzen_7_4700u-1093)).

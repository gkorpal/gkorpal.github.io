---
layout: single
title:  "Pre-Covid Crisis Tech Remedies (Jan 2020)"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
The laptop that I got when I joined college 5 years ago was now old enough to be replaced. Mostly because I picked the wrong specs when there was a choice (like chose Realtek over Intel NIC, 1x8GB over 2x4GB RAM, and 48Wh over 62Wh battery) and my lack of maintenance (never cleaned dust from inside or the rust from the ports). So I wanted something portable that can allow me to browse internet, write homework assignments in LaTeX (not Overleaf) and backup my data to the cloud. Moreover, I find Windows very irritating to use and prefer Ubuntu. However, due to budget constraints, I couldn't just buy the $1000+ Dell XPS 13 or Lenovo ThinkPad X. So I was only left with the option of Chromebook, which Linus Torvalds believes to have potential of becoming the future of desktop Linux. The best option available in terms of build quality was the $650 Google Pixel Go (m3-8100Y processor) but spending so much money on a chromebook was out of question since ChromeOS is a handicapped version of Linux with limited hardware and software support (just like Android, due to which I had to abandon my lovely Google/Asus Nexus 7 tablet). So I searched for something with specs similar to Pixelbook Go but at lower price (i.e. lower build quality) and stumbled upon Asus Chromebook C425 and bought it without putting much though since it fit my budget of around $350.

# Performance 

Following is the comparison of tech specs of my new laptop (USD 375 before taxes in Jan 2020) with the older laptop (USD 916 before taxes in Oct 2014) :


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
|Warranty | 1 year  (ChromeOS updates until June 2026)| 1 year |
|Bottomline | Mobility (Fanless, 0.66" thin and 2.8 lbs) | Sturdy and easy to upgrade (user manual has full details) |

I considered this an upgrade since it offered better mobility and screen.

## LaTeX Setup in Chromebook 

1. Turn on Linux (Beta) by following [these steps](https://support.google.com/chromebook/answer/9145439?hl=en). 
2. Check that the sandbox (Penguin container/Crostini) is up-to-date. In your browser, go to `chrome://components`. Under `cros-termina`, select "Check for update". If you download an update, you might need to restart your Chromebook.
3. Open terminal and update the packages `sudo apt-get update && sudo apt-get dist-upgrade` (there won't be any password prompts)
4. Install TeX Live from Debian repo: `sudo apt-get install texlive`
5. Install TexMaker from Debian repo: `sudo apt-get install texmaker`
6. Install Evince (pdf viewer) from Debian repo: `sudo apt-get install evince`
7. Install DjVu4 (DjVu viewer) from Debian repo: `sudo apt-get install djview4

I used `apt-get` instead of `apt` since I am more used to that. 

Theoretically, Core i7-4702MQ should be about 10% better than Core m3-8100Y for compiling LaTeX files ([single core performance](https://www.cpu-monkey.com/en/compare_cpu-intel_core_m3_8100y-1216-vs-intel_core_i7_4702mq-448)). Howeover, the pdfLatex process is extremely slow in Chromebook since Debian runs in a sandbox and have limited access to resources (still in beta state). Moreover, there are random crashes when multiple pdf/DjVu docs are opened using Evince/DjVu-viewer. The thing which I hate the most is the introduction of new bugs even in stable channel and the browser using 90% of the available RAM (irrespective of how many tabs are open or the total RAM the computer has).

<figure>
  <img src="/images/chromeos.jpeg" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption>The current state of Chrome OS: <a href="https://twitter.com/RonAmadeo/status/1218230779148427271?s=20">Ron Amadeo</a></figcaption>
</figure>

# Build Quality

| Quality Parameter | Asus Chromebook C425 (C425T) | Lenovo ThinkPad E440 (Custom build) |
| ------------- |:--------------------------------------:|:----------------------------:|
| Chassis |  Metal flap with plastic body. The laptop looks stylish but the hinge design is really bad. Can't be open with just one hand and it flexes the whole machine a little bit putting strain on the plastic casing. Therefore, the frame started cracking within 2 months of usage and it is not covered under warranty. | Metal flap with plastic body. The laptop looks simple and the laptop can be easily openend with one hand. No cracks after 5 years of rough usage.|
|Display |  |  |
|Speakers|   |   |
| Keyboard | | |
| Trackpad |   |  |
| Thermals |  |  |
For budget PC expect low build quality and dim display.



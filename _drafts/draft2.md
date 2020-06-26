---
layout: single
title:  "COVID Crisis Tech Remedies (May 2020)"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
With the "work-from-home" restriction imposed to counter COVID crisis, the chromebook became even more useless. It could neither run the desktop version of Zoom nor work with a drawing tablet. I believe these problems can be solved by enabling the Developer Mode and installing Ubuntu alongside ChromeOS, but I highly doubt that audio and other drivers will work in Ubuntu. However, since mobility is not desired anymore, I decided to build desktop PC with minimum possible budget (which turned out to be $650, same as the cost of the basic Pixelbook Go or an entry level ThinkPad with core i5 10th gen). Moreover, desktop CPUs are much more powerful than laptop CPUs, for instance the [Intel Core i3-9100 gives slightly better performance as Intel Core i5-10210U](https://www.cpu-monkey.com/en/compare_cpu-intel_core_i3_9100-924-vs-intel_core_i5_10210u-941).

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

This will certainly an upgrade from the desktop computer I used a decade ago with Intel Pentium 4 CPU and 512MB RAM (no idea how did the graphics work in that machine).

The current AMD budget processors provide a much superior iGPU performance than their Intel counterparts. For example: 
* We can compare the entry level quad-core desktop processors from last year: Intel Core i3-9100 (MSRP $120) has better CPU but worse iGPU than AMD Ryzen 3 3200g (MSRP $100) ([benchmark](https://www.cpu-monkey.com/en/compare_cpu-amd_ryzen_3_3200g-952-vs-intel_core_i3_9100-924)).
* We can compare the pro level mobile processors from this year: Intel Core i7-10710U with 6-physical cores with hyperthreading, is not better than AMD Ryzen 7 4700U with 8-physical cores but no hyperthreading ([comparison](https://www.pcworld.com/article/3541009/ryzen-7-4700u-review-amds-budget-8-core-crushes-intels-10th-gen-chips-again.html)).

I finally decided not to spend extra $20 for i3-9100 since the ability of 3200g to allow light gaming would be more than enough for my daily usage. Moreover, since neither of them have hyperthereading/multithreading, I won't expect much improvement in multitasking. However, Intel being more popular has better support for various hardware (for example, I couldn't run my monitor via HDMI due to compatibility issue between the motherboard and monitor). Howoever, luckily, this time the Realtek ethernet drivers [didn't cause headache with Ubuntu](https://tuxbyte.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/).


## Cloud Backup Setup in Ubuntu PC

<figure>
  <img src="/images/comparison.png" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption> This a a comparison of Passmark results (screenshot taken on 26 June 2020, when the prices had dropped due to announcement of next gen processors). I have no idea what these benchmarks prove, since each CPU has different architecture and a given program need not be optimised for a particular processor. In general, all seem to agree that Intel gives better single threaded performance than AMD, i.e. Intel should be better for pdfLateX.  <a href="https://twitter.com/RonAmadeo/status/1218230779148427271?s=20">Ron Amadeo</a></figcaption>
</figure>
# Build Details

| PC Part | Model   | MSRP before tax/shipping (round figure) |
| ------------- |-----------------|------------------------|
|***System Unit*** | ***Total cost*** | ***USD 380***  |
|CPU+GPU+cooler| AMD Ryzen 3 3200g | USD 100|
|***Input/Output Devices***| ***Total cost*** | ***USD 380***  |
|Keyboard | Redragon| USD 30|

Intel monopoly https://videocardz.com/newz/intel-faces-criticism-for-comparing-gaming-laptops-with-different-gpu-models

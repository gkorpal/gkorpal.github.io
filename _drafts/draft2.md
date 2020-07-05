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

I finally decided not to spend extra $20 for i3-9100 since the ability of 3200g to allow light gaming would be more than enough for my daily usage. Moreover, since neither of them have hyperthereading/multithreading, I won't expect much improvement in multitasking. However, Intel being more popular has better support for various hardware (for example, I couldn't run my monitor via HDMI due to compatibility issue between the motherboard and monitor). However, luckily, this time the Realtek ethernet drivers [didn't cause headache with Ubuntu](https://tuxbyte.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/).

<figure>
  <img src="/images/comparison.png" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption> This is a comparison of PassMark results (screenshot taken on 26 June 2020, when the prices had dropped due to announcement of next gen processors). PassMark a good measure of server orientated performance, where multiple cores are often simultaneously loaded. However, as seen above, for everyday use Core i3 is better than Ryzen 3.</figcaption>
</figure>

## Cloud Backup Setup in Ubuntu PC

I am suing [rclone](https://rclone.org/downloads/) to sync files between my PC and Google Drive. Following are the steps one can follow to set it up:

0. Create your own Google Drive OAuth2 client ID for rclone:

   a)  Log into the [Google API Console](https://console.developers.google.com/) with your Google account. It doesn't matter what Google account you use. (It need not be the same account as the Google Drive you want to access.
   
   b)  Select a project or create a new project.
   
   c)  Under "ENABLE APIS AND SERVICES" search for "Drive", and enable the "Google Drive API".
   
   d)  Click "Oauth Consent Screen" in the left panel and select user type "External". Then add Application name (anything you want) and save.
   
   e)  Click "Credentials" in the left panel. Then click on "+ CREATE CREDENTIALS" button at the top of the screen, then select "OAuth client ID". Select Application type as "Desktop app", enter whaever client anme you want and click create.
   
   f)  It will show you a client ID and client secret. Use these values in rclone config.

1. Install the latest version of rclone via Terminal: `curl https://rclone.org/install.sh | sudo bash`
2.  Now [configure rclone](https://rclone.org/drive/) for Google Drive via Terminal: `rclone config` and follow the steps. Remeber to use the Client ID and client secret we created above. Since we created this API for personal use, we won't be submitting it for verfication. Hence don't be alarmed by the very scary confirmation screen shown when we connect via your browser for rclone to be able to get its token-id.  Also, if you want to fetch Google Docs as links (instead of converting them to .odt etc) from Google Drive, in "advance-config" set "export-formats" to "links.html".
3.  Sync files using "[copy](https://rclone.org/commands/rclone_copy/)" and NOT "[sync](https://rclone.org/commands/rclone_sync/)": `rclone copy source:path dest:path [flags]`. For example, to sync all files from "New Folder" Google Drive (named: Drive) to PC (folder: home) and view the progress, type: `rclone copy Drive:"New Folder" /home -P`.  Google Drive tend to have duplicate files since it allows same names files in same folder, in that case use [dedupe](https://rclone.org/commands/rclone_dedupe/) to delete all duplicate files.
4.  Set-up [auto update](https://forum.rclone.org/t/update-rclone-to-latest-version-with-rclone-u/10954) for rclone program (can see the latest version [here](https://github.com/rclone/rclone/releases)):

    a)  Open the bash file using a text editor like gedit: `sudo gedit ~/.bashrc`
    
    b)  Add the following code to the file and save it: `rclone() { if [[ $@ == "-U" ]]; then command curl https://rclone.org/install.sh | sudo bash; else command rclone "$@"; fi; }`
    
    c) To update to the latest version run this in the Terminal: `rclone -U`

# Build Details

As I said above, Intel Core i3 9100 would have been a better choice in terms of processing power. However, even after the launch of 10th gen CPUs that build would have costed about $20 more since though the RAM will be really cheap as only 2400 MHz is supported by i3 (-$10), the CPU and motherboard (H310) will remain a little more expensive than the AMD counterparts (+$30). So, instead of following the recommendation for gaming PC, right now one can get a better Linux support for about the same price by going for Intel instead of AMD. AMD build is better than Intel if one plans to play games and do overclocking by buying a better motherboard and monitor.

| PC Part | Model   | MSRP (round figure) | Comments |
| ------------- |-----------------|------------------------| ----------|
|***System Unit*** | ***Total cost*** | ***USD 380***  | ***Should not require any upgrade for 4 years***|
|CPU+GPU+Cooler| AMD Ryzen 3 3200g | USD 100| Cheapest quad-core processor in the market with a proper GPU|
|Motherboard | MSI A320M-A Pro Max | USD 55 | Cheaptest motherboard with Ryzen 3000 APU support and M.2 PCIe. Shortcomings include the lack of ability to overclock CPU, no VGA port, only 2 RAM slots, only one case fan port and Realtek LAN|
|Memory | Patroit Viper 4 Blackout (2x4GB, 3000MHz)|USD 40 | Was able to use it at CPU's supported frequency of 2933 MHz|
|Storage | Crucial P1 500GB | USD 60 | This QCL NVMe M.2 SSD is chaper than many SATA SSDs in the market|
|PSU | Corsair CX450 | USD 65| Cheapest 80+ Bronze rated power supply with good reviews.|
|Case| Cooler master N200 | USD 50 | Decent quality mini-tower with two pre-installed quiet-fans (not PMW). However, it being small in size, made cable management really hard|
|***Input/Output Devices***| ***Total cost*** | ***USD 380***  |  ***minimalistic, nothing fancy*** |
|Keyboard | Redragon K552-N| USD 30| Cheapest tenkeyless mechanical keyboard without any lighting. The next decent option was for around USD 100. |
|Mouse | Logitech M310 | USD 20 | Wireless ambidextrous mouse which is not very small. Though would prefer a bigger mouse.|
| Monitor+speakers | Asus VA229HR | USD 100 | This 1080p 21" IPS screen with 1.5W sterio speakers didn't meet my expectations. Its HDMI port doesn't work well with my motherboard/CPU. Also, stand was so bad that I has to buy a new stand. |
|Webcam+mic | Logitech C270 | USD 30 | Better than the HD camera laptop have |
|***Accesories*** | ***Total Cost*** | ***USD 380*** | ***Required to make PC setup comfortable*** | System Case Stand | Iocrest Sy-ACC65029 |USD 10 | Cheapest case stand for keeping system on carpet| 

Intel monopoly https://videocardz.com/newz/intel-faces-criticism-for-comparing-gaming-laptops-with-different-gpu-models

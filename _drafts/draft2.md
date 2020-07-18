---
layout: single
title:  "COVID Crisis Tech Remedies (May 2020)"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
With the "work-from-home" restriction imposed to counter COVID crisis, the chromebook became even more useless. It could neither run the desktop version of Zoom nor work with a drawing tablet. I believe these problems can be solved by enabling the Developer Mode and installing Ubuntu alongside ChromeOS, but I highly doubt that audio and other drivers will work in Ubuntu. However, since mobility is not desired anymore, I decided to build desktop PC with minimum possible budget (which turned out to be $650, same as the cost of the basic Pixelbook Go or an entry level ThinkPad with core i5 10th gen). Moreover, desktop CPUs are much more powerful than laptop CPUs, for instance the [Intel Core i3-9100 gives slightly better performance than Intel Core i5-10210U](https://www.cpu-monkey.com/en/compare_cpu-intel_core_i3_9100-924-vs-intel_core_i5_10210u-941).

# Performance
Following is the comparison of my PC with the best laptop available in the market in May 2020 for USD 650 (before tax):

| Specification | Custom build PC   | Acer Swift 3 (SF314-42-R9YN) |
| ------------- |:-----------------:|:----------------------------:|
|CPU            | AMD Ryzen 3 3200G (3.60 GHz x 4 cores, Zen+)    | AMD Ryzen 7 4700U (2.00 GHz x 8 cores, Zen 2)|
|iGPU            | AMD Radeon Vega 8  (1.25 GHz x 8 cores, Gen 8)  | AMD Radeon 7 (1.60 GHz x 7 cores, Gen 9)|
|RAM | 2 x 4 GB DDR4 2933 MHz ([with 64MB reserved for iGPU](https://www.techspot.com/article/1578-amd-raven-ridge-reserved-memory-explainer/))            | 2 x 4 GB LPDDR4 4266 MHz|
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

This will certainly an upgrade from the desktop computer I used a decade ago with Intel Pentium 4 CPU and 512MB RAM (no idea what graphics card was there in that machine). Moreover, though on paper Intel Core i7 4702MQ (my old Thinkpad) is not much worse than AMD Ryzen 3 3200G in terms of CPU performance, the AMD iGPU much better. For instance,  with the best graphic settings of [SuperTuxKart](https://supertuxkart.net/Main_Page) (for 60FPS/1080p required to have min AMD Radeon RX 460 with 1 GB VRAM), AMD gives about 30 fps on an average whereas Intel only gives 10 fps 

The current AMD budget processors provide a much superior iGPU performance than their Intel counterparts. For example: 
* We can compare the entry level quad-core desktop processors from last year: Intel Core i3-9100 (MSRP $120) has better CPU but worse iGPU than AMD Ryzen 3 3200g (MSRP $100) ([benchmark](https://www.cpu-monkey.com/en/compare_cpu-amd_ryzen_3_3200g-952-vs-intel_core_i3_9100-924)).
* We can compare the pro level mobile processors from this year: Intel Core i7-10710U with 6-physical cores and hyperthreading, is not better than AMD Ryzen 7 4700U with 8-physical cores but no hyperthreading ([comparison](https://www.pcworld.com/article/3541009/ryzen-7-4700u-review-amds-budget-8-core-crushes-intels-10th-gen-chips-again.html)).

I finally decided not to spend extra $20 for i3-9100 since the ability of 3200g to allow light gaming would be more than enough for my daily usage. Moreover, since neither of them have hyperthereading/multithreading, I won't expect much improvement in multitasking. However, Intel being more popular has better support for various hardware (for example, I couldn't run my monitor via HDMI due to compatibility issue between the motherboard and monitor). Luckily, this time the Realtek ethernet drivers [didn't cause headache with Ubuntu](https://tuxbyte.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/).

<figure>
  <img src="/images/comparison.png" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption> This is a comparison of PassMark results (screenshot taken on 26 June 2020, when the prices had dropped due to announcement of next gen processors). PassMark a good measure of server orientated performance, where multiple cores are often simultaneously loaded. However, as seen above, for everyday use Core i3 is better than Ryzen 3.</figcaption>
</figure>

## Cloud Backup Setup for Linux PC (tested in Linux Mint and Ubuntu)

I am suing [rclone](https://rclone.org/downloads/) to sync files between my PC and Google Drive. Following are the steps one can follow to set it up:

0. Create your own Google Drive OAuth2 client ID for rclone:

   a)  Log into the [Google API Console](https://console.developers.google.com/) with your Google account. It doesn't matter what Google account you use. (It need not be the same account as the Google Drive you want to access.
   
   b)  Select a project or create a new project.
   
   c)  Under "ENABLE APIS AND SERVICES" search for "Drive", and enable the "Google Drive API".
   
   d)  Click "Oauth Consent Screen" in the left panel and select user type "External". Then add Application name (anything you want) and save.
   
   e)  Click "Credentials" in the left panel. Then click on "+ CREATE CREDENTIALS" button at the top of the screen, then select "OAuth client ID". Select Application type as "Desktop app", enter whaever client anme you want and click create.
   
   f)  It will show you a client ID and client secret. Use these values in rclone config.

1. Install the latest version of rclone via Terminal: `curl https://rclone.org/install.sh | sudo bash`
2.  Now [configure rclone](https://rclone.org/drive/) for Google Drive via Terminal: `rclone config` and follow the steps. Remeber to use the Client ID and client secret we created above. Since we created this API for personal use, we won't be submitting it for verfication. Hence don't be alarmed by the very scary confirmation screen shown when we connect via your browser for rclone to be able to get its token-id.  Also, if you want to fetch Google Docs as links (instead of converting them to .odt etc) from Google Drive, in "advance-config" set "export-formats" to "link.html".
3.  Sync files using "[copy](https://rclone.org/commands/rclone_copy/)" and NOT "[sync](https://rclone.org/commands/rclone_sync/)": `rclone copy source:path dest:path [flags]`. For example, to sync all files from "New Folder" Google Drive (named: Drive) to PC (folder: home) and view the progress, type: `rclone copy Drive:"New Folder" /home -P`.  Google Drive tend to have duplicate files since it allows same names files in same folder, in that case use [dedupe](https://rclone.org/commands/rclone_dedupe/) to delete all duplicate files.
4.  Set-up [auto update](https://forum.rclone.org/t/update-rclone-to-latest-version-with-rclone-u/10954) for rclone program (can see the latest version [here](https://github.com/rclone/rclone/releases)):

    a)  Open the bash file using a text editor like gedit/xed/vim: `~/.bashrc`
    
    b)  Add the following code to the file and save it: `rclone() { if [[ $@ == "-U" ]]; then command curl https://rclone.org/install.sh | sudo bash; else command rclone "$@"; fi; }`
    
    c) To update to the latest version run this in the Terminal: `rclone -U` and enter the PC password.

# Build Details
 
All the system part recommendations were from [PC-Part-Picker](https://pcpartpicker.com/) forums and [Build-a-PC](https://www.reddit.com/r/buildapc/) subreddit hence were biased towards gaming performance.

| PC Part | Model   | MSRP (round figure) | Comments |
| ------------- |-----------------|------------------------| ----------|
|***System Unit*** | ***Total cost*** | ***USD 370***  | ***Should not require any upgrade for 4 years. 57% of the total budget.***|
|CPU+GPU+Cooler| AMD Ryzen 3 3200g | USD 100| Latest and cheapest quad-core processor in the market with a proper GPU|
|Motherboard | MSI A320M-A Pro Max  | USD 55 | Cheaptest motherboard with Ryzen 3000 APU support and M.2 PCIe. Shortcomings include the lack of ability to overclock CPU, no VGA port, only 2 RAM slots, only one case fan port and Realtek LAN. Luckily it came with most stable UEFI/BIOS (UEFI version 7C52v24/E7C52AMA.240, Released Nov-07-2019)|
|Memory | Patroit Viper 4 Blackout (2x4GB, 3000MHz)|USD 40 | Was able to use it at CPU's supported frequency of 2933 MHz|
|Storage | Crucial P1 500GB | USD 60 | This QCL NVMe M.2 SSD is chaper than many SATA SSDs in the market|
|PSU | Corsair CX450 | USD 65| Cheapest 80+ Bronze rated power supply with good reviews.|
|PC Case| Cooler Master N200 | USD 50 | Decent quality mini-tower with two pre-installed quiet-fans (not PMW). However, it being small in size, made cable management really hard though it comes with zip-ties. I hade to move the front intake fan to the outside to get rid of humming noise ([video](https://youtu.be/7S5SpE62HDE))|
|***Input/Output Devices***| ***Total cost*** | ***USD 180***  |  ***minimalistic, nothing fancy. 28% of the total budget.*** |
|Keyboard | Redragon K552-N| USD 30| Cheapest tenkeyless mechanical keyboard without any lighting. The next decent option was for around USD 100. |
|Mouse | Logitech M310 | USD 20 | Wireless ambidextrous mouse which is not very small. Though would prefer a bigger mouse.|
| Monitor+speakers | Asus VA229HR | USD 100 | This 1080p 21.5" IPS screen with 1.5W sterio speakers didn't meet my expectations. Its HDMI port doesn't work well with my motherboard/CPU. Also, stand was so bad that I has to buy a new stand. Would have bought HP VH240a if it had longer warranty period and a smaller screen size option.|
|Webcam+mic | Logitech C270 | USD 30 | Better than the HD camera laptop have |
|***Accesories*** | ***Total Cost*** | ***USD 100*** | ***Required to make PC setup comfortable. 15% of the total budget.*** 
|Surge protector | Belkin BE108200-06 | USD 20 | |
| System Case Stand | Iocrest SY-ACC65029 |USD 15 | Cheapest case stand for keeping system above carpet| 
|Mouse pad| Insignia  NS-PNP5008 | USD 5 | |
|Monitor stand| Huanuo HNCM5-S | USD 25 | |
|DVI-D to VGA cable| Benfei B07JYXYSSL | USD 10 | |
|Audio cable| StarTech Slim 3.5mm jack | USD 5 | |
|Ethernet cable| Quantum CAT5e | USD 10 | |
|USB 3.0 extension cable| Sabrent CB-3060 | USD 10 | |

## Introspection

The original plan was to use [Ubuntu 20.04 GNOME](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes) as the OS since I wanted a stable system (hence not the rolling release distros like Manjaro and Solus) with Linux kernel [greater than 4.20](https://www.phoronix.com/scan.php?page=news_item&px=Raven2-Picasso-Firmware-Files) (hence not Debian 10) and large software repository (hence not enterprise focused distros like OpenSUSE and Fedora). But Ubuntu turned out to be RAM hungry, since it required extra softwares like [GNOME extensions](https://extensions.gnome.org/) and [Variety](https://peterlevi.com/variety/) for customization, and depended on the unstable [Snap store](https://bugs.launchpad.net/snap-store-desktop/+bug/1879137). While trying to fix these issues I was able to brick my system thrice and hence decided to shift to [Linux Mint 20 Cinnamon](https://blog.linuxmint.com/?p=3928) which provides out-of-the-box support for [Flatpak](https://blog.linuxmint.com/?p=3418)(needed for [Xournal++](https://github.com/xournalpp/xournalpp)) and [blocks Snap](https://www.linuxmint.com/rel_ulyana_cinnamon.php) while providing better customizability and the same 5 year support (unlike official Ubuntu flavours which give only 3 years support). Though the appearance and RAM usage became much better with Linux Mint, it still inherited many boot errors like:

1.  [IOMMU](https://dev.getsol.us/T8884): Most likely this is a [false alarm](https://bbs.archlinux.org/viewtopic.php?id=218140) from the Linux kernel. However, turning off IOMMU in BIOS is not an option since it is [needed for HSA](https://bugzilla.redhat.com/show_bug.cgi?id=1404139) used by [AMD for making GPU and CPU work together in its APUs](https://en.wikipedia.org/wiki/Heterogeneous_System_Architecture). 

2. [Time Stamp Counter](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1804591): Another Ryzen APU compatibility issue with Linux kernel.

3. [Kwallet](https://forums.linuxmint.com/viewtopic.php?f=42&t=286950): KWallet is supposed to be with KDE and not Cinnamon/GNOME.

4. [GNOME key-ring](https://gitlab.gnome.org/GNOME/gnome-keyring/-/issues/28): Issue with GNOME.

5. [Pulseaudio+BlueZ](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Disable_Bluetooth_support): due to unavailability of Bluetooth in my computer and presence of Pulseaudio and BlueZ 5.53 in Ubuntu 20.04.

6. [initramfs](https://askubuntu.com/questions/1245458/getting-the-message-0-283078-initramfs-unpacking-failed-decoding-failed-wh): Boot speed improvements through changing the default kernel compression algorithm to lz4 (in Ubuntu 19.10) on most architectures, and changing the default initramfs compression algorithm to lz4 on all architectures. Somehow doesn't work well for my PC. Has to apply the fix everytime this package is updated.

7. [UVC driver/Alsa](https://askubuntu.com/questions/1189925/uvcvideo-failed-to-query-get-info): I think that the audio driver of Webcam leading to error during boot.

Out of these 1 and 4 are logged consistently during each boot, 2 and 7 are logged some times, and the remaining could be fixed if they ever occur again. Since I am running LTS distro, I won't have to worry much about losing compaibility of my hardware or learning about latest softwares. Though there are only non-fatal boot errors, since everything is working as intended, it might be best to just [shrug sholders](https://forums.linuxmint.com/viewtopic.php?f=46&t=323195). 

Also, if you are using NVMe SSD then consider installing the NVMe tool as [discussed here](https://www.cyberciti.biz/faq/linux-find-nvme-ssd-temperature-using-command-line/) (might lead to logging of boot errors). Once you install any linux OS I would recommend running following commands and checking is everything is running as expected:
`````
inxi -Fxz #system information google to learn more about inxi

lscpu #can also see lspci, lshw

sudo nvme smart-log /dev/nvme0n1" #NVMe info

journalctl -b -p 3 #error log messages

dmesg -l emerg,alert,crit,err
`````

Also, in case things get out of hand, to access GRUB Menu press right <kbd>Shift</kbd> if system boots using BIOS or press <kbd>Esc</kbd> if system boots using UEFI. Remeber that if you press <kbd>Esc</kbd> multiple times then you will enter [GRUB command prompt instead](https://www.gnu.org/software/grub/manual/grub/html_node/Command_002dline-and-menu-entry-commands.html). 

As I said above, Intel Core i3 9100 would have been a better choice in terms of processing power. Even after the launch of 10th gen CPUs that build would have costed about $20 more since though the RAM will be really cheap as only 2400 MHz is supported by i3 (-$10), the CPU and motherboard (H310) will remain a little more expensive than the AMD counterparts (+$30). however, by buying HP VH240a instead of Asus VA229HR, I could have saved USD 30, hence keeping the total cost of build USD 650 even with i3 9100. That said, I am happy with my AMD PC since it allows me to do some light gaming as a bonus (which was not the purpose of this PC). AMD build is clearly better than Intel if one plans to play even a single racing/shooting game with an option for overclocking by buying a better motherboard.

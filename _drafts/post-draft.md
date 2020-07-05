---
layout: single
title:  "Pre-Covid Crisis Tech Remedies (Jan 2020)"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
The laptop that I got when I joined college 5 years ago was now old enough to be replaced. Mostly because I picked the wrong specs when there was a choice (like chose Realtek over Intel NIC, 1x8GB over 2x4GB RAM, and 48Wh over 62Wh battery) and my lack of maintenance (never cleaned dust from inside or the rust from the ports). So I wanted something portable that can allow me to browse internet, write homework assignments in LaTeX (not Overleaf) and backup my data to the cloud. Moreover, I find Windows very irritating to use and prefer Ubuntu. However, due to budget constraints, I couldn't just buy the $1000 Linux friendly laptops like Dell XPS or Lenovo ThinkPad . Fortunately, the university gives free unlimited high-speed WiFi which makes Chromebook a viable option. The best Chromebook available in terms of build quality was the $650 Google Pixel Go (m3-8100Y processor) but spending so much money on a chromebook was out of question since ChromeOS is a handicapped version of Linux with limited hardware and software support (just like I had to abandon my lovely Google/Asus Nexus 7 2nd gen tablet because Android stopped getting updates). So I searched for something with specs similar to Pixelbook Go but at lower price (i.e. lower build quality). While searching I stumbled upon Asus Chromebook C425 and bought it without putting much though since it fit my budget of $350-400.

# Performance 

Following is the comparison of tech specs of my new laptop (USD 375 + taxes in Jan 2020) with the older laptop (USD 916 + taxes in Oct 2014) :


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

I considered this as an upgrade since it offered better mobility and screen. Moreover, before getting the Thinkpad as a gift, I was using the netbook [HP Mini 1103](https://www.laptopmag.com/reviews/laptops/hp-mini-1103) (10.1-inch screen with a single-core 1.66-GHz Intel Atom N455 CPU and 1GB of RAM) with Windows 7 replaced by Lubunu. I learned LaTeX on that small computer. Note that hyperthreading might be disabled by default, so you will have to enable it by going to `chrome://flags/#scheduler-configuration` and changing the option to "Enables Hyper-Threading on relevant CPUs". You might need to repeat this process after each bi-weekly system update.

The thing which I don't like about the Chromebook is that the browser uses majority of the available RAM irrespective of how many tabs are open or the total RAM the computer has. Also, one wrong browser extension can lead to random crashes. And the stupidest thing is the lack of local trash/recycle-bin folder just like Android, so deleted files can't be recovered (i.e. make a Downloads folder on Google Drive instead of using the local drive folder).


<figure>
  <img src="/images/ideal.png" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption>When you are lucky, you might get ideal performance, with hyper-threading active in both ChromeOS and Crostini, along with no CPU hogging by Crostini. Here, the Cog app is showing ChromeOS info, neofetch is showing Linux system info (the CPU identity is not shared with the virtual machine) and System Task Manager shows CPU/RAM usage.</figcaption>
</figure>

## LaTeX Setup in Chromebook 

For LaTeX I use [Vim](https://packages.debian.org/bullseye/vim) with [Terminal](https://packages.debian.org/bullseye/gnome-terminal) as the text-editor and [MuPDF](https://packages.debian.org/bullseye/mupdf) as the pdf-viewer since both can be accessed solely via keyboard. Earlier I used [TexMaker](https://packages.debian.org/bullseye/texmaker) as text-editor and [Evince](https://packages.debian.org/bullseye/evince) as pdf-viewer, but the [display scaling](https://www.reddit.com/r/Crostini/wiki/howto/adjust-display-scaling) was bad with TexMaker and Evince was not unable to open DjVu files (hence no advantage of it using poppler), save annotated files by replacing the existing one, or open multiple PDF files without leading to system crash.

1. Turn on Linux (Beta) by following [these steps](https://support.google.com/chromebook/answer/9145439?hl=en). 
2. Check that the sandbox (Penguin container/Crostini) is up-to-date. In your browser, go to `chrome://components`. Under `cros-termina`, select "Check for update". If you download an update, you might need to restart your Chromebook.
3. Open Crostini and use the preinstalled version of Vim to edit, if needed, the "cros.list" and "sources.list" so that they have the following content (make sure it is "http" and not "https", otherwise you can get HTTP proxy issues):  
   ````
   $ cat /etc/apt/sources.list.d/cros.list
   deb http://storage.googleapis.com/cros-packages/83 buster main
   
   $ cat /etc/apt/sources.list
   # Generated by distrobuilder
   deb http://deb.debian.org/debian buster main
   deb http://deb.debian.org/debian-security buster/updates main
   deb http://deb.debian.org/debian testing main
   ````
   Here "buster" should correspond to the [version of Debian](https://wiki.debian.org/DebianReleases) installed in Crostini. We have basically added [Debian Testing](https://wiki.debian.org/DebianTesting) to the source list so that we can [install the latest version of packages known to be stable](https://nosarthur.github.io/coding/2019/09/05/crostini.html).
4. Mark stable release as default: `echo 'APT::Default-Release "stable";' | sudo tee -a /etc/apt/apt.conf.d/00local`
5. Update the packages: `sudo apt update && sudo apt dist-upgrade` (there won't be any password prompts).
6. Remove the installed version of Vim (we will do a fresh install of the latest version): `sudo apt remove vim vim-common vim-tiny vim-runtime` and then `sudo apt autoremove`
7. Install the latest version of [Vim](https://www.vim.org/) (36.3 MB downloaded) : `sudo apt -t testing install vim`. You can also try the GUI version like GTK3, but screen resolution might be messed up ([fixing screen resolution](https://www.reddit.com/r/Crostini/comments/9g1ovl/scale_and_dpi_in_sommelierrc/)). Moreover, "vim-gtk3" will also  add support for scripting with Lua, Perl, Python 3, Ruby, and Tcl which I neither need nor have space for in my chromebook. 
8. Install the latest version of Ubuntu's [Terminal](https://help.gnome.org/users/gnome-terminal/stable/) (304 MB downloaded) which allows new tabs via `Ctrl`+`Shift`+`T`: `sudo apt -t testing install gnome-terminal` (It also uses GTK interface, so you can consider installing vim-gtk or vim-gtk3 instead). 
9. Install the latest version of [MuPDF](https://mupdf.com/) (35.3 MB downloaded): `sudo apt -t testing install mupdf` 
10. Install the latest version of [TeX Live](https://www.tug.org/texlive/) (336 MB downloaded): `sudo apt -t testing install texlive`
11. Install plugin manager [vim-plug](https://github.com/junegunn/vim-plug) for Vim:
12. Install the plugin [vim-tex](https://github.com/lervag/vimtex) which will allow Vim to specialize as LaTeX editor: 
13. Right click on the folder where you want to create the tex files and choose "Share with Linux" and "Available offline". The folder can be accessed via  `cd /mnt/chromeos/GoogleDrive/MyDrive/"NameOfSharedFolder"`

You might get gibberish text when using Linux, in that case you will have to disable GPU-acceleration for the sandbox, this can be done by going to `chrome://flags/#crostini-gpu-support` and changing the option to "disabled". 

Though ChromeOS gives you an option of making a backup of Chrostini, I would recommend removing Linux before system restart for the biweekly updates and then rinstall everything. Many times Linux breaks after system updates.

The pdfLatex process in this Chromebook can be as slow as in the old netbook (HP Mini 1103) since the [Debian runs in a virtual machine](https://linuxiumcomau.blogspot.com/2018/07/introduction-to-crostini-part-1-hp.html) and might get limited access to resources due to [sandbox restrictions](https://chromium.googlesource.com/chromium/src/+/master/docs/design/sandbox.md). In particular, hyperthreading for Crostini sometimes get disabled after ChromeOS update, i.e. only 2 cores instead of 4 are available ([discussion thread](https://bugs.chromium.org/p/chromium/issues/detail?id=1088305)). Therefore, in Crostini the Intel Core m3-8100Y might sometimes perform like Intel Atom N455. However, the most frustrating thing is when the virtual machine starts utilising 200% or more of the CPU (i.e. approximately 100% of more than one of the available cores) even after you have closed it, in which case you will have to go to Task Manager (`Search` + `Esc`) and end it there ([discussion thread](https://www.reddit.com/r/Crostini/comments/apxf77/crostini_linux_running_at_300_cpu_usage/)). 


<figure>
  <img src="/images/buggy.jpg" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption>Even with hyperthreading enabled, sometimes the Linux will show only 2 cores. Note that virtual machine is reading the CPU as single core with 2 or 4 threads. Hence, the cache organization is half of the <a href="https://en.wikichip.org/wiki/intel/core_m/m3-8100y">actual value</a>.</figcaption>
</figure> 

# Build Quality

From what I had read about Chromebook's lack of basic capabilities (can't run most softwares, can't format flash drive to desired format, don't have SSD, and no compatible with many hardwares like drawing tablet), for $400 I expected the build quality of a $800 windows laptop. However, just like the Linux capabilities, the build quality was also disappointing.
 
| Quality Parameter | Asus Chromebook C425 (C425T) | Lenovo ThinkPad E440 (Custom build) |
| ------------- |:--------------------------------------:|:----------------------------:|
| Chassis |  Metal flap with plastic body. The laptop looks stylish but the hinge design is really bad. Can't be open with just one hand and it flexes the whole machine a little bit putting strain on the plastic casing. Therefore, the frame started cracking within 2 months of usage and it is not covered under warranty. | Metal flap with plastic body. The laptop looks simple and can be easily openend with one hand. Only the fan grill plastic broke after 5 years of rough usage.|
|Display |  |  |
|Speakers|   |   |
| Keyboard | Makes web browsing more comfortable.  When the Chromebook lid swings out for use, the hinge forces the back of the keyboard up, [increasing strain on hinge](https://www.androidcentral.com/asus-c425-best-chromebook-buy-black-friday). | |
| Trackpad |   |  |
| Thermals | Due to the lack of fan, multitasking and video calls can make the right side of keyboard really hot (about 55°C). |  |
|Internals| Coil whining | easy to upgrade |

I will end by quoting the reviews I read before buying this chromebook and ignored the warnings:

> I’m not a plastic hater, but there are price brackets I equate to plastics being used, and at MSRP $499, I don’t expect a mostly-plastic build. While there isn’t a ton of flex and wobbliness with this chassis, there’s no getting around the way plastic feels under your palms as you actually use a Chromebook. ---- [Chrome Unboxed](https://chromeunboxed.com/asus-chromebook-c425-review/)

> Personally, I don’t mind a plastic bottom. In fact, there are advantages to having a plastic bottom, as plastic is lighter and less heat-conductive than metal. However, a plastic main-deck might be enough of a reason to pay extra for the C434. I mean, the plastic on the C425 is not the poor-quality we’ve used to see on entry-level laptops in the past, but it’s still plastic nonetheless, and doesn’t feel as nice or as sturdy as metal..... That being said, I think there’s better value in the $550 Chromebook C434 than in this $399 ChromeBook C425, even with less RAM. And if you’re on a tight budget, perhaps consider that ChromeBook C302 first, see if you can live with a smaller screen, but without compromising on the build and the screen. The C425 comes as a third option, if those other two failed to meet your mark due to their higher price or smaller display. ---- [UltrabookReview.com](https://www.ultrabookreview.com/31669-asus-chromebook-c425-reviewed/)

> The C425’s plastic body has more flex and suffers from a duller-looking, non-touch screen, but the keyboard and trackpad are responsive, the screen is fine for documents and spreadsheets, and it has enough battery life to last a full day of work or classes. ---- [NY Times- Wirecutter](https://www.nytimes.com/wirecutter/reviews/best-chromebook/) 

## Introspection

Somethings that I overlooked because of branding of Intel is that m3 uses DDR3 RAM, whereas modern Intel Pentium, Intel Celeron and AMD A4 use DDR4. Moreover, getting rid of fan though makes the system lighter and quiter, bottlenecks the capabilities of the processor. Also, since the prices fluctuate a lot, if it wasn't an emergency I would have waited for better price on alternatives. If mobility was not a concern, then 15" laptops like Acer Aspire 5 and Asus VivoBook 15 were good options. If I knew that we will be teaching for home then Apple iPad Mini would have been a better option.

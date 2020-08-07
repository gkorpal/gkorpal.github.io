---
layout: single
title:  "Upgrading to the next level of Linux experience"
header:
categories: 
  - Jekyll
tags:
  - edge case
---

# FOSS is better

Free and open-source software are great because they allow transparency and technical superiority. In fact, this is good enough incentive for many big corporations/companies like Intel (Open Source Technology Center), IBM (Red Hat Enterprise Linux), Microsoft (Azure), Google (Chrome), Novell (SUSE Linux), Canonical (Ubuntu) etc. to sponsor [Linux Foundation](https://www.linuxfoundation.org/membership/members/) and other commmunity-driven Linux projects like [GNOME](https://www.gnome.org/foundation/), [KDE](https://kde.org/donations), [Cinnamon DE](https://www.linuxmint.com/sponsors.php), [Debian](https://www.debian.org/partners/) and [Gentoo](https://www.gentoo.org/inside-gentoo/sponsors/). However, there are still some popular Linux related projects like [Arch Linux](https://www.archlinux.org/donate/) and [Xfce](https://simon.shimmerproject.org/2020/06/18/why-bountysource-why/) that are being developed by the community at a steady pace without any corporate funding. Though these community-only projects are really powerful and allow the user to create a custom workflow, they tend to attract only the ones with considerable knowledge of Linux and desire to contribute. 

For normal consumer products like desktops and laptops, Microsoft Windows has the monopoly because it comes pre-installed for free and is supported by all softwares (games) and latest hardware. However, in the enterprise world where mainframe computers and servers need to be really secure, Linux distributions like Ubuntu, RHEL, CentOS, SUSE and Debian tend to be more popular. Among these, Debian is the only one which is not owned by any specific company, but [companies can directly fund the long-term-support](https://wiki.debian.org/LTS/Funding). Ubuntu, which derives its source from Debian Sid, is [quite popular among tech start-ups](https://ubuntu.com/blog/ubuntu-startups-a-match-made-in-code) because of its freemium kind of business model where anyone can download it for free and one only needs to pay for extended service (similar to the extreme popularity of the free-to-play games like Fortnite and PUBG) . In fact, it was marketed so well that it is the most popular Linux distribution among people who just wants a better OS than Windows but can't afford to be a part of Mac ecosystem.

<figure>
  <img src="/images/ubuntu.jpg" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption> My understanding of current Ubuntu development.</figcaption>
</figure>

Ubuntu's major contribution has been the [LightDM](https://wiki.ubuntu.com/LightDM) display manager. However, neither Ubuntu nor Debian is the market leader because they lack fast paced innovation. [RHEL has been the market leader](https://www.redhat.com/en/blog/red-hat-leading-enterprise-linux-server-market) for enterprise linux for a long time, mainly because it has [invested a lot in innovation](https://www.linuxfoundation.org/blog/2016/08/the-top-10-developers-and-companies-contributing-to-the-linux-kernel-in-2015-2016/). Following is a rough representation of how it works in present:
<figure>
  <img src="/images/redhat2.jpg" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption> My understanding of current RHEL development.</figcaption>
</figure>

The second most popular enterprise Linux distro is SUSE, it is the oldest commercial Linux distro. In recent years, it has also [reorganized itself](https://www.admin-magazine.com/Archive/2017/38/An-exclusive-interview-with-openSUSE-Chairman-Richard-Brown) by starting community driven openSUSE project similar to the successful Fedora project to speed up innovation:
<figure>
  <img src="/images/suse2.jpg" alt="my alt text" style="width:534px;height:269px;"/>
  <figcaption> My understanding of current SUSE development.</figcaption>
</figure>

This new Tumbleweed was a result of the [‘merger’ of Old Tumbleweed and Factory in November 2014](https://rootco.de/2016-03-28-why-use-tumbleweed/). Recently, AMD to complement its great technological advancements have [started making significant contributions to the Linux kernel](https://wiki.archlinux.org/index.php/AMDGPU). In fact, it is also [one of the primary sponsors of openSUSE project](https://en.opensuse.org/Sponsors). In my opinion, openSUSE Tumbleweed is a good comeptitor for Fedora since it strives to provide access to latest packages using rolling release instead of short lived point release. On the other hand, openSUSE Leap is a good competitor for Ubuntu LTS since it gives an option for upgrading to much superior SUSE enterprise. 

# Mix and Match

Now a days there are many emerging comeptitors like Manjaro and Solus competing with Ubuntu and its forks for the non-technical users. I was introduced to linux as a non-techincal user in 2006 when I ran Ubuntu in a virtual box on my Windows XP desktop PC, thanks to the free CD I got with the PC World magazine I had bought during summer vacations. I have been using Ubuntu-based distros (I replaced Windows 7 with Lubuntu on my Netbook) since Windows XP died in 2014, and it has been a nice journey. Whenever I ran into some trouble, I just copy-pasted codes from some blog/forum and ignored issues as long as work got done. For example, I chose not to use WiFi over using Windows 8 when Realtek drivers were breaking on Ubuntu (had no idea it has to do something with Linux Kernel). But now since I have built my own PC for the first time, I have a much better knowledge of the hardware and find it difficult to just shrug shoulders as long as system boots. Theorefore, Ubuntu can no more fulfill my needs and I will have to move to a little less stable distro.   

The main use of my new PC is to write documents in LaTeX, hence I would really like to have easy access to the latest version of texlive and text-editor (like Vim, though you will always get some version of vim-minimal pre-installed). However, stable distros like Ubuntu LTS and openSUSE Leap tend to have outdated repositories of both of these and Ubuntu tries to mitigate this with untrusted PPAs, [unstable Snaps](https://jatan.blog/2020/05/02/ubuntu-snap-obsession-has-snapped-me-off-of-it/) and [useless Flatpaks](https://medium.com/@alex285/using-flatpak-vim-from-flathub-d876faa00d5b). Moreover, compiling them from sources can be a bit tricky (eg:  installing [TexLive](https://tex.stackexchange.com/q/1092/73743) and [Vim](https://vi.stackexchange.com/q/10817/30343)). Hence I felt the need to migrate to a distro which can give **easy access to latest version of these programs**. But I don't have enough time and knowledge to be able to maintain the stability and security of rolling-release distros like Arch, openSUSE TW and Gentoo. Therefore, since I don't need any proprietary drivers for my PC, I decided to take a middle ground and move to the [pseudo-rolling/stable-release distro](https://www.reddit.com/r/linux/comments/96dlhy/why_fedora_does_not_market_it_self_as_rolling/e40fhtu/) Fedora (13 month life cycle, new release every 6 months) which is the upstream source of the commercial Red Hat Enterprise Linux distribution. Another reason for choosing Fedora was that its community is more knowledgebable (RedHat is [one of the biggest contributer](https://www.redhat.com/en/blog/red-hat-leads-open-source-contributions-to-kernel) to Linux kernel) and the [bugs](https://docs.fedoraproject.org/en-US/quick-docs/howto-file-a-bug/) acutally get resolved (for Ubuntu there can exist an year old bugs like the [initramfs bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660) with temporary solution in forums). One bug that has followed me in Ubuntu and Linux Mint is the momentary blackout of screen when some pop-up menu opens in applications like Google Chrome and TexMaker Settings, however I have no hope of it getting solved since there is this [similar three years old bug report](https://askubuntu.com/questions/911666/) in the forums.

For the desktop environment I decided to go with Xfce because most of my programs use GTK (hence not KDE or LXQt), didn't want to waste RAM for customizability (hence not GNOME 3 or MATE which are resource heavy but still lack simple in-built customization options like desktop wallpaper slideshow) and needed stability (hence not Cinnamon which lacks proper documentation and bug resolving mechanism, eg: this an year old [zombie-windows bug](https://github.com/linuxmint/cinnamon/issues/8856) which requires restarting cinnamon to troubleshoot, moreover most appearance tweaks depend on themes and applets created by volunteers which are not guaranteed to be actively maintained). Cinnamon is an attempt to mimic Xfce while staying close to GNOME, however its lack of documentation puts me off.

I installed Fedora Xfce using [Server Netinstall](https://alt.fedoraproject.org/) instead of the official [Spins](https://spins.fedoraproject.org/en/cinnamon/) since they tend to be bloated and will have to install lots of updates afterwards. Fedora comes with Ubuntu's [LightDM display manager](https://github.com/canonical/lightdm) which manages the login screen, in the case of Xfce Fedora uses the Xubuntu's [LightDM GTK+ Greeter](https://github.com/Xubuntu/lightdm-gtk-greeter).

# Differences between Ubuntu and Fedora

Most of my Linux experience is based on Ubuntu. Following are some differences:

## Administrator vs. User

Users have the option of setting a root password in when installing a non-GNOME Fedora, but it is not required if the user creates an initial user account and selects the option to add it to the wheel group. If root password is set, then the <code>root</code> account is the account for the system admin. This account is disabled in Ubuntu. In Ubuntu, one performs actions that require <code>root</code> privileges using **sudo**, while in a Fedora spin, **sudo** is not the default method of gaining administrative permissions. Therefore, in Fedora Xfce spin with root password, <code>root</code> access can only be gained with `su`.  **su** will ask for the <code>root</code> password, not the regular user password. After logging in successfully as `root`, one has administrative rights until terminal is closed or logged out with `exit`. However, for [GNOME Fedora](https://getfedora.org/en/workstation/), it's just like Ubuntu i,e. [no root password set by default](https://fedoraproject.org/wiki/Changes/ReduceInitialSetupRedundancy#Root_Account) and user account is handled by gnome-initial-setup. Having a root password is [not useful for nontechnical users](https://www.howtogeek.com/111479/htg-explains-whats-the-difference-between-sudo-su/).
   
## Package management

Fedora uses different tools for package management to Debian. Here is a quick overview of how to accomplish common tasks in Fedora: ([source](https://fedoraproject.org/wiki/Differences_to_Ubuntu))

| Debian command | Fedora command |
|--------------- | --------------- |
| apt update | dnf check-update | 
| apt upgrade | dnf upgrade | 
| apt dist-upgrade | dnf system-upgrade | 
| apt install | dnf install |
| apt remove | dnf remove |
| apt purge | N/A |
| apt-cache search | dnf search |

In older versions, `apt-get` in Ubuntu corresponded to `yum` in Fedora.  To know if a reboot is needed after doing a `dnf update` use either [tracer](https://dnf-plugins-extras.readthedocs.io/en/latest/tracer.html) or [needs-restarting](https://dnf-plugins-core.readthedocs.io/en/latest/needs_restarting.html) plugin.

Moreover, like in Ubuntu we use `dpkg` for installing .deb files, we can use `rpm` in Fedora for installing .rpm files. Following is a comparison of commands:

| Command Details | 	Fedora Command	| Ubuntu Command |
| ---------------- | -----------------| --------------- |
|Install a package |	rpm -i package.rpm |	dpkg -i package.deb |
|Update package |	rpm -U  package_name  |	dpkg -i {file.deb}|
|Remove an installed package |	rpm -e package_name	 | dpkg -r package_name|
|List all installed packages |	rpm -qa	| dpkg -l|
|List files in an installed package |	rpm -ql package_name |	dpkg --listfiles package_name|
|Show information about installed package	 | rpm -qi package_name| dpkg --status package_name |
|Show information about package file	| rpm -qpi package.rpm |	dpkg --info package.deb|
|List files in a package file	 | rpm -qpl package.rpm |	dpkg --contents package.deb|
|Verify all installed packages |	rpm -Va |	N/A|
|Verify installed package	| rpm -V package_name |	N/A|

You can also use `dnf` instead of `rpm`, just like we can use `apt` instead of `dpkg`. You can find an outdate but more extensive list in [Ubuntu Wiki](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora).

## Finding packages using GUI

Fedora's equivalent to Debian's Synaptic package manager is [dnfdragora](https://github.com/manatools/dnfdragora), unfortuately it's nowhere as good as Synaptic. However, in GNOME edition of Fedora there is GNOME Software Centre which makes things smoother, but requires [PC reboot for installing updates](https://ask.fedoraproject.org/t/gnome-software-center-wants-me-to-restart-to-install-updates/1283/5).  In the RPM world opeSUSE has YaST as a worthy competitor of Synaptic (but that feels too nosey, it is much more than just a package manager).

## Installing packages not in repository

The equivalent of the Ubuntu <code>restricted</code> and <code>multiverse</code> repositories, that include patented and closed-source technologies and programs, is the [RPMFusion repository](https://docs.fedoraproject.org/en-US/quick-docs/setup_rpmfusion/). **free** is the equivalent of <code>universe</code> and contains potentially patent-encumbered software like <code>gstreamer-plugins-bad</code> or the <code>VLC media player</code>, while **nonfree** includes non-free software like proprietary 3D graphics drivers.

These repositories can easily be enabled by typing (as <code>root</code>):

<pre>
dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
</pre>

Moreover, the equivalent of the PPAs in Ubuntu is [Copr](https://copr.fedorainfracloud.org/). This repository can be [added with](https://dnf-plugins-core.readthedocs.io/en/latest/copr.html)

<pre>
dnf copr enable user/project.
</pre>

Note that just like Ubuntu PPA and Arch AUR, there is no way to verify that a package in Copr does not contain anything malicious unless you review the source code.

## Linux Security Modules

Ubuntu uses AppArmor (which was earlier developed by SUSE), whereas Fedora uses SELinux. AppAromor is said to be easier to maintain than SELinux.

# Installing Fedora

Firstly download and verify the iso file. Then make a bootable pendrive using the Qt app [Fedora Media Writer](https://flathub.org/apps/details/org.fedoraproject.MediaWriter), unfortunately it requires KDE so will install that also. I decided to use ext4 file system, which is the current default file system for Workstation and Spins, instead of  the dfault file system [xfs for Server/Netinstall](https://www.phoronix.com/scan.php?page=news_item&px=Fedora-Server-22-XFS) (there are benchmarks claiming either [xfs is better](https://www.phoronix.com/scan.php?page=article&item=linux-58-filesystems&num=4) or [ext4 is better](https://unix.stackexchange.com/questions/525613/xfs-vs-ext4-performance)). I followed [Fedora's recommended partitioning scheme](https://docs.fedoraproject.org/en-US/fedora/f32/install-guide/install/Installing_Using_Anaconda/#sect-installation-gui-manual-partitioning-recommended) and created the following [GUID partition table](https://docs.fedoraproject.org/en-US/fedora/f32/install-guide/install/Installing_Using_Anaconda/#sect-installation-gui-manual-partitioning-standard):

| Mount Point | Parition Type |File System | Size | % of total space|
|-------------|----------------|-----------|------| ----------------|
|/boot | Standard | ext4 | 500 MB | 0.1% |
| /boot/efi | Standard |  EFI System Partition | 200 MB | 0.04 % |
| swap | Standard | swap |  4 GB |  0.8 % |
| / |  Standard  | ext4 | 60 GB |  12 % |
|/home | Standard |ext4 | 435 GB | 87 % |

Note that modern Linux OS [don't require separate partitions](https://superuser.com/a/520088) for both `/boot` and `/boot/efi` (EFI System Partition) directories. The only requirement for suing GRUB2 boot loader is that `/boot` directory [must be on a plain ext4 or xfs partition](https://fedoraproject.org/wiki/Unified_Extensible_Firmware_Interface#Partitioning_for_UEFI) and `/boot/efi` directory [must be on a plain vfat partition](https://fedoramagazine.org/learning-about-partitions-and-how-to-create-them-for-fedora/).  If one wants to install Fedora with only two paritions `/` and `/boot` then it is recommended to [use systemd-boot boot loader](https://fedoramagazine.org/learning-about-partitions-and-how-to-create-them-for-fedora/) instead. However, since we were following Fedora's [recommended partitoning scheme](https://docs.fedoraproject.org/en-US/fedora/f32/install-guide/install/Installing_Using_Anaconda/#sect-installation-gui-manual-partitioning-recommended) we created separate `/boot` and `/home` paritions with standard ext4 format instead of leaving them with `/`. Also, I alloted thrice the recommended size for 20 GB for `/` because I plan to use Timeshift which saves snapshots in root directory itself and works only with GRUB2 ([very important tool](https://www.zdnet.com/article/boothole-fixes-causing-boot-problems-across-multiple-linux-distros/), was [fixed later](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1889556)).

Select Xfce Fedora without any extra software programs, we will manually install the ones we want. Also reclaim the whole disk to remove the previously installed OS. To bypass creating root password in netinstall mode, just create a user account and mark it as administrator.

## DNF plugins

[tracer](https://dnf-plugins-extras.readthedocs.io/en/latest/tracer.html).

[system-upgrade](https://dnf-plugins-extras.readthedocs.io/en/latest/system-upgrade.html) and 

## Xfce appearance

Few [panel plugins](https://docs.xfce.org/panel-plugins/start) like Datetime, Places, PulseAudio and ScreenShooter are already installed.

| Purpose | Software | dnf Package |
|----------|----------|---------|
|Clipboard manager | Clipman | xfce4-clipman-plugin|
|Weather indicator on taskbar | Weather | xfce4-weather-plugin|

Note that the weather plugin has known bugs, like using inaccurate data from [Meteorologisk institutt](https://www.met.no/) instead of actual data from [OpenWeatherMap](https://openweathermap.org/) and co-ordinating day/night icon with [UTC instead of local time](https://bugzilla.xfce.org/show_bug.cgi?id=16091). None of these bugs are there in [Cinnamon's weather plugin](https://cinnamon-spices.linuxmint.com/applets/view/17).

Themes: https://fedoramagazine.org/tweaking-the-look-of-fedora-workstation-with-themes/

## Free and open source software

Vim, PulseAudio Volume Control and dnfdragora are already available.

| Purpose | Software | dnf Package |
|----------|----------|---------|
|Login screen modification tool | [LightDM GTK+ Greeter settings](https://wiki.archlinux.org/index.php/LightDM#GTK_greeter) | lightdm-gtk-greeter-settings |
|System Restore | [Timeshift](https://github.com/teejee2008/timeshift) | timeshift|
|GUI for Systemd Journal |[GNOME Logs](https://wiki.gnome.org/Apps/Logs)| gnome-logs |
|Web browser| Firefox | firefox |
|Calculator | [Galculator](https://github.com/galculator/galculator) | galculator |
|File searching tool | [Catfish](https://bluesabre.org/catfish/) | catfish |
|GUI Text Editor | [Mousepad](https://github.com/codebrainz/mousepad) | mousepad |
|Viewing and editing images | [gThumb](https://wiki.gnome.org/Apps/Gthumb) | gthumb|
|Disk Usage Analyzer | [Baobab](https://wiki.gnome.org/Apps/DiskUsageAnalyzer) | baobab |

Xournal++, AbeWord, Gnumeric, Evince, SuperTuxKart, Cheese, texlive, Xarchiver


## Restricted software

| Purpose | Software | Installation guide |
|---------|----------|--------------------|
|Playing videos with patented multimedia codecs | Celluloid | [RPM Fusion Free Repository](https://admin.rpmfusion.org/pkgdb/package/free/celluloid/)|
|Using streaming services like Netflix which require  h264/mp3/aac and widevine | Google Chrome | [fedora-workstation-repositories](https://fedoraproject.org/wiki/Workstation/Third_Party_Software_Repositories)|
|Video conferencing | Zoom | [manual download](https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_b6ce9fba-dd38-4448-80c0-ac2e58db3acc)|



# Introspection

The plan is to [upgrade to next version of Fedora](https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/) three months after its release so that maximum bugs can be avoided (eg: initial release of Fedora 32 had [a bug](https://bugzilla.redhat.com/show_bug.cgi?id=1816787) which has been corrected later using system updates). Hence I will get a system wide update twice a year. Fedora is going to change to [btrfs as default filesystem](https://fedoraproject.org/wiki/Changes/BtrfsByDefault) in the next release of Fedora 33 (something [default in SUSE but abandoned by Red Hat](https://www.phoronix.com/scan.php?page=news_item&px=Red-Hat-Deprecates-Btrfs-Again)).  One annoying thing is that I have to install lots of updates everyday since Fedora pushes bug fixes as soon as they are found, irrespective of how important they are. Moreover, the supported releases are updated to the latest stable version of the Linux kernel, increasing the chances of unstability. 

Though Xfce is highly customizable and has a great [documentation](https://docs.xfce.org/start), it lacks GUI for basic things like system info viewer, individual CPU core usage, user login picture manager (though Fedora has [Whisker menu plugin](https://src.fedoraproject.org/rpms/xfce4-whiskermenu-plugin), it lacks the required [Mugshot](https://src.fedoraproject.org/rpms/mugshot) package) and [tablet pen-pressure settings](https://docs.xfce.org/xfce/xfce4-settings/mouse) (which is very nicely done for GNOME 3, Cinnamon and KDE). However, these can easily be done using manually via Terminal. For example, for system info we have CLI tools like `inxi` ([doc](https://smxi.org/docs/inxi-man.htm)), `neofetch` and `lshw`. Also, to view system usage information we can use tool like `top` in terminal, and [get individual core usage](https://askubuntu.com/a/257258) by `top 1` ([doc](http://manpages.ubuntu.com/manpages/xenial/en/man1/top.1.html)). We can manually edit the [profile picture configuration](https://forums.fedoraforum.org/showthread.php?295285-Change-user-picture-in-login-manager-Fedora-19-XFCE)

````
$ sudo mkdir /var/lib/AccountsService/icons/<your_user_name>
$ sudo cp ~/home/<my_picture_of_size_96x96>.png /var/lib/AccountsService/icons/<your_user_name>

$ sudo mousepad /var/lib/AccountsService/users/<your_user_name>
````

Add the line: `Icon=/var/lib/AccountsService/icons/<your_user_name>/<my_picture_of_size_96x96>.png`. And for Wacom tablet pen-pressure on X Window System we can use `xsetwacom` ([doc](https://github.com/linuxwacom/xf86-input-wacom/wiki/xsetwacom))

`````
xsetwacom set "Wacom One by Wacom S Pen stylus" PressureCurve 0 75 25 100
````` 

However, any setting changed by `xsetwacom` will be reset to default (or a statically configured setting) whenever the device is unplugged, disabled or the X Server is restarted. One can make Linux [run the command automatically at startup](https://smallbusiness.chron.com/run-command-startup-linux-27796.html) or  change [xorg.conf](https://github.com/linuxwacom/xf86-input-wacom/wiki/Tablet-Configuration-1:-xsetwacom-and-xorg.conf), but they have limitations (like when hot-plugging the device). For more details refer to this [Arch wiki page](https://wiki.archlinux.org/index.php/wacom_tablet). Note that, these CLI methods [won't work when using Wayland](https://github.com/linuxwacom/xf86-input-wacom/wiki/Wayland-and-Wacom-devices) instead of Xorg. I could't make CLI work in Cinnamon, only GUI settings worked and provided the following options:

````
  0  75   25  100  # very soft
  0  50   50  100  # soft
  0  25   75  100  # little soft
  0   0  100  100  # default
 25   0  100   75  # little firm
 50 100  100   50  # firm
 75   0  100   25  # very firm
````
The default appearance editor can only edit GTK2 themes/icons. That is, to edit GTK3 themes/icons either edit the `~/.config/gtk-3.0/settings.ini` or use the LXDE appearance editor `lxappearance`.

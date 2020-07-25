---
layout: single
title:  "Upgrading to the next level of Linux experience"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
I believe that, in the present scenerio, there are 3 levels of Linux distors in terms of sophestication for everyday users (non-server):

1. Ubuntu: Long Term Support distro which works out-of-the-box and has various customized versions available. Requires no prior knowledge of linux and is popular among people looking for Windows alternative. Most of the troubleshooting is done using community forums.

2. Fedora: Front-runner of Linux development which can be adjusted to personal needs as long as working with free and open source stuff. Requires little prior knowledge of Linux and is popular among people having CentOS and RHEL at work. Most of the troubleshooting is done using bug reports (documentation tend to be outdated).

3. Arch Linux: Enables you to build a highly customized OS with you yourself being responcible for its security. Requires good knowledge of Linux and is popular among people who want full control over their OS. Most of the troubleshooting is done using the extensive documentation.

All these three levels have emerging comeptitors like Manjaro and Solus competing with Ubuntu and its forks, and openSUSE competing with Fedora and Arch by offering option of rolling and point release. I was introduced to linux in 2006 when I ran Ubuntu in a virtual box on my Windows XP desktop PC, thanks to the free CD I got with the PC World magazine I had bought during summer vacations. I have been using Ubuntu-based distros (I replaced Windows 7 with Lubuntu on my Netbook) since Windows XP died in 2014, and it has been a nice journey. Whenever I ran into some trouble, I just copy-pasted codes from some blog/forum and ignored issues as long as work got done. For example, I chose not to use WiFi over using Windows 8 when Realtek drivers were breaking on Ubuntu (had no idea it has to do something with Linux Kernel). But now since I have built my own PC for the first time, I have a much better knowledge of the hardware and find it difficult to just shrug shoulders as long as system boots. Theorefore, Ubuntu can no more fulfill my needs and I will have to move to a little less stable distro.   

The main use of my new PC is to write documents in LaTeX, hence I would really like to have easy access to the latest version of texlive and text-editor (like Vim, though you will always get some version of vim-minimal pre-installed). However, stable distros like Ubuntu LTS tend to have outdated repositories of both of these and try to mitigate this with untrusted PPAs, [unstable Snaps](https://jatan.blog/2020/05/02/ubuntu-snap-obsession-has-snapped-me-off-of-it/) and [useless Flatpaks](https://medium.com/@alex285/using-flatpak-vim-from-flathub-d876faa00d5b). Moreover, compiling them from sources can be a bit tricky (eg:  installing [TexLive](https://tex.stackexchange.com/q/1092/73743) and [Vim](https://vi.stackexchange.com/q/10817/30343)). Hence I felt the need to migrate to a distro which can give **easy access to latest version of these programs**. But I don't have enough time and knowledge to be able to maintain the stability and security of rolling-release distros like Arch, openSUSE TW and Gentoo. Therefore, since I don't need any proprietary drivers for my PC, I decided to take a middle ground and move to the pseudo-rolling/stable-release distro Fedora (13 month life cycle, new release every 6 months) which is the upstream source of the commercial Red Hat Enterprise Linux distribution. Another reason for choosing Fedora was that its community is more knowledgebable (RedHat is [one of the biggest contributer](https://www.redhat.com/en/blog/red-hat-leads-open-source-contributions-to-kernel) to Linux kernel) and the [bugs](https://docs.fedoraproject.org/en-US/quick-docs/howto-file-a-bug/) acutally get resolved (unlike Ubuntu, Red Hat has lot of financial interests in solving bugs detected in Fedora, eg: this an year old [initramfs bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660) with temporary solution in forums). One bug that has followed me in Ubuntu and Linux Mint is the momentary blackout of screen when some pop-up menu opens in applications like Google Chrome and TexMaker Settings, however I have no hope of it getting solved since there is this [similar three years old bug report](https://askubuntu.com/questions/911666/) in the forums.

For the desktop environment I decided to go with Xfce because most of my programs use GTK (hence not KDE or LXQt), didn't want to waste RAM for customizability (hence not GNOME 3 or MATE which are resource heavy but still lack simple in-built customization options like desktop wallpaper slideshow) and needed stability (hence not Cinnamon which lacks proper documentation and bug resolving mechanism, eg: this an year old [zombie-windows bug](https://github.com/linuxmint/cinnamon/issues/8856) which occors everytime I use [Zoom app](https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux)). Though Xfce is highly customizable and has a great [documentation](https://docs.xfce.org/start), it lacks GUI for basic things like system info viewer, user login picture manager (though Fedora has [Whisker menu plugin](https://src.fedoraproject.org/rpms/xfce4-whiskermenu-plugin), it lacks the required [Mugshot](https://src.fedoraproject.org/rpms/mugshot) package) and [tablet pen-pressure settings](https://docs.xfce.org/xfce/xfce4-settings/mouse) (which is very nicely done for GNOME 3, Cinnamon and KDE). However, these can easily be done using manually via Terminal. For example, for system info we have CLI tools like `inxi` ([doc](https://smxi.org/docs/inxi-man.htm)), `neofetch` and `lshw`. We can manually edit the [profile picture configuration](https://forums.fedoraforum.org/showthread.php?295285-Change-user-picture-in-login-manager-Fedora-19-XFCE)

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

I installed Xfce Fedora via netinstall mode using [Network Installer](https://alt.fedoraproject.org/) since Fedora 32 and its [spins](https://spins.fedoraproject.org/en/xfce/) had [a bug](https://bugzilla.redhat.com/show_bug.cgi?id=1816787) during initial release which has been corrected with the latest updates. Fedora comes with Ubuntu's [LightDM display manager](https://github.com/canonical/lightdm) which manages the login screen, in the case of Xfce Fedora uses the Xubuntu's [LightDM GTK+ Greeter](https://github.com/Xubuntu/lightdm-gtk-greeter).

# Differences between Ubuntu and Fedora

Most of my Linux experience is based on Ubuntu. Following are some differences:

1.  Users have the option of setting a root password in when installing a non-GNOME Fedora, but it is not required if the user creates an initial user account and selects the option to add it to the wheel group. If root password is set, then the <code>root</code> account is the account for the system admin. This account is disabled in Ubuntu. In Ubuntu, one performs actions that require <code>root</code> privileges using **sudo**, while in a Fedora spin, **sudo** is not the default method of gaining administrative permissions. Therefore, in Fedora Xfce spin with root password, <code>root</code> access can only be gained with `su`.  **su** will ask for the <code>root</code> password, not the regular user password. After logging in successfully as `root`, one has administrative rights until terminal is closed or logged out with `exit`. However, for [GNOME Fedora](https://getfedora.org/en/workstation/), it's just like Ubuntu i,e. [no root password set by default](https://fedoraproject.org/wiki/Changes/ReduceInitialSetupRedundancy#Root_Account) and user account is handled by gnome-initial-setup. Having a root password is [not useful for nontechnical users](https://www.howtogeek.com/111479/htg-explains-whats-the-difference-between-sudo-su/).
   
 2.  Fedora uses different tools for package management to Debian. Here is a quick overview of how to accomplish common tasks in Fedora: ([source](https://fedoraproject.org/wiki/Differences_to_Ubuntu))

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

3.  Like in Ubuntu we use `dpkg` for installing .deb files, we can use `rpm` in Fedora for installing .rpm files. Following is a comparison of commands:

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

4.  Fedora's equivalent to Debian's Synaptic package manager is [dnfdragora](https://github.com/manatools/dnfdragora), unfortuately it's nowhere as good as Synaptic. However, in GNOME edition of Fedora there is GNOME Software Centre which makes things smoother, but requires [PC reboot for installing updates](https://ask.fedoraproject.org/t/gnome-software-center-wants-me-to-restart-to-install-updates/1283/5).  In the RPM world opeSUSE has YaST as a worthy competitor of Synaptic (but that feels too nosey, it is much more than just a package manager).

5.  The equivalent of the Ubuntu <code>restricted</code> and <code>multiverse</code> repositories, that include patented and closed-source technologies and programs, is the [RPMFusion repository](https://rpmfusion.org/). **free** is the equivalent of <code>universe</code> and contains potentially patent-encumbered software like <code>gstreamer-plugins-bad</code> or the <code>VLC media player</code>, while **nonfree** includes non-free software like proprietary 3D graphics drivers.

These repositories can easily be enabled by typing (as <code>root</code>):

<pre>
dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
</pre>

6.  The equivalent of the PPAs in Ubuntu is [Copr](https://copr.fedorainfracloud.org/). This repository can be [added with](https://dnf-plugins-core.readthedocs.io/en/latest/copr.html)

<pre>
dnf copr enable user/project.
</pre>

Note that just like Ubuntu PPA and Arch AUR, there is no way to verify that a package in Copr does not contain anything malicious unless you review the source code.


# Installing Fedora

Select Xfce Fedora without any extra software programs, we will manually install the ones we want. Also reclaim the whole disk to remove the previously installed OS. To bypass creating root password in netinstall mode, just create a user account and mark it as administrator. Vim, PulseAudio Volume Control and dnfdragora are already there.

Uninstall: pidgin, hexchat, thunderbird, transmission, eom, shotwell, simple-scan, xawtv, xfburn, xreader, redshift

Install the following [Fedora's repository](https://src.fedoraproject.org/): 

| Function | Software | dnf Package |
|----------|----------|---------|
|Tool for [modifying the login screen](https://wiki.archlinux.org/index.php/LightDM#GTK_greeter) | LightDM GTK+ Greeter settings | lightdm-gtk-greeter-settings |
|System Restore | [Timeshift](https://github.com/teejee2008/timeshift) | timeshift|
|GUI for Systemd Journal |[GNOME Logs](https://wiki.gnome.org/Apps/Logs)| |

Xournal++, AbeWord, Gnumeric, gThumb (edit photos), Celluloid (mpv frontend), Evince, SuperTuxKart, Cheese,  calculator

Proprietary: [Google Chrome](https://fedoraproject.org/wiki/Workstation/Third_Party_Software_Repositories) and [Zoom](https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_b6ce9fba-dd38-4448-80c0-ac2e58db3acc).

DNF plugins: [system-upgrade](https://dnf-plugins-extras.readthedocs.io/en/latest/system-upgrade.html) and [tracer](https://dnf-plugins-extras.readthedocs.io/en/latest/tracer.html).

# Introspection

The plan is to [upgrade to next version of Fedora](https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/) three months after its release so that maximum bugs can be avoided. Hence I will get a system wide update twice a year.

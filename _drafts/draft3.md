---
layout: single
title:  "Shifting from Debian-based to RPM-based distro"
header:
categories: 
  - Jekyll
tags:
  - edge case
---

The main use of my new PC is to write documents in LaTeX, hence it would be essential to have easy access to the latest version of texlive and text-editor (like Vim, though you will always get some version of vim-minimal pre-installed). However, stable Debian-based distros (like Debian Stable, Ubuntu LTS and Linux Mint) tend to have outdated repositories of both of these and try to mitigate this with untrusted PPAs, [unstable Snaps](https://jatan.blog/2020/05/02/ubuntu-snap-obsession-has-snapped-me-off-of-it/) and [useless Flatpaks](https://medium.com/@alex285/using-flatpak-vim-from-flathub-d876faa00d5b). Moreover, compiling them from sources can be a bit tricky (eg:  installing [TexLive](https://tex.stackexchange.com/q/1092/73743) and [Vim](https://vi.stackexchange.com/q/10817/30343)). Hence I felt the need to migrate to a distro which can give easy access to latest version of these programs. But I don't have enough knowledge to be able to maintain the stability of rolling-release distros like Arch, openSUSE and Gentoo. Therefore, since I don't need any proprietary drivers, I decided to take a middle ground and shift to the pseudo-rolling/stable-release distro Fedora (13 month life cycle) which is the upstream source of the commercial Red Hat Enterprise Linux distribution. Another reason for choosing Fedora was that its community is more knowledgebable (RedHat is [one of the biggest contributer](https://www.redhat.com/en/blog/red-hat-leads-open-source-contributions-to-kernel) to Linux kernel). 

For the desktop environment I decided to go with Cinnamon because most of my programs use GTK (hence not KDE or LXQt), didn't want to waste RAM for customizability (hence not GNOME 3 or MATE which are resource heavy but still lack simple in-built customization options like desktop wallpaper slideshow) and needed a GUI for drawing tablet settings (unfortunately, Xfce lacks GUI for tablet [pen-pressure settings](https://docs.xfce.org/xfce/xfce4-settings/mouse)). The only problem that I have faced with Cinnamon is that sometimes I experience [zombie-windows bug](https://github.com/linuxmint/cinnamon/issues/8856).

I installed Cinnamon Fedora via netinstall mode using [Network Installer](https://alt.fedoraproject.org/) since Fedora 32 and its [spins](https://spins.fedoraproject.org/en/xfce/) had [a bug](https://bugzilla.redhat.com/show_bug.cgi?id=1816787) during initial release which has been corrected with the latest updates.

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

In older versions, `apt-get` in Ubuntu corresponded to `yum` in Fedora.

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

4.  Fedora's equivalent to Synaptic package manager is [dnfdragora](https://github.com/manatools/dnfdragora). However, the outdated [Yum Extender](https://github.com/timlau/yumex-dnf) (yumex-dnf) is much faster and easier to use.


5.  The equivalent of the Ubuntu <code>restricted</code> and <code>multiverse</code> repositories, that include patented and closed-source technologies and programs, is the [RPMFusion repository](https://rpmfusion.org/). **free** is the equivalent of <code>universe</code> and contains potentially patent-encumbered software like <code>gstreamer-plugins-bad</code> or the <code>VLC media player</code>, while **nonfree** includes non-free software like proprietary 3D graphics drivers.

These repositories can easily be enabled by typing (as <code>root</code>):

<pre>
dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
</pre>

6.  The equivalent of the PPAs in Ubuntu is [Copr](https://copr.fedorainfracloud.org/). This repository can be [added with](https://unix.stackexchange.com/a/152976/420307)

<pre>
dnf copr enable user/project.
</pre>

Note that just like Ubuntu PPA and Arch AUR, there is no way to verify that a package in Copr does not contain anything malicious unless you review the source code.


# Installing Fedora

Select Cinnamon Fedora without any extra software programs, we will remove the unncessary ones and install the ones we want later. Also reclaim the whole disk to remove the previously installed OS. To bypass creating root password in netinstall mode, just create a user account and mark it as administrator. Vim is already there.

Uninstall: pidgin, hexchat, thunderbird, transmission, eom, shotwell, simple-scan, xawtv, xfburn, xreader, redshift

Install: 

| Function | Software | dnf Package |
|----------|----------|---------|
|System Restore | [Timeshift](https://github.com/teejee2008/timeshift) | timeshift|
|GUI Text Editor |  |    |



Xournal++, AbeWord, Gnumeric, gThumb (edit photos), Celluloid (mpv frontend), xfce4-terminal (drop-down support), Evince, , [GNOME Logs](https://wiki.gnome.org/Apps/Logs), SuperTuxKart, Cheese, pulse-audio-volume-control

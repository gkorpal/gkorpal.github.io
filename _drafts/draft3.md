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

For the desktop environment I decided to go with Xfce because most of my programs use GTK (hence not KDE or LXQt), didn't want to waste RAM (hence not GNOME3/MATE which is resource heavy but still lacks simple in-built customization options like deaktop wallaper slideshow) and was facing [zombie-windows bug](https://github.com/linuxmint/cinnamon/issues/8856) in Cinnamon (though I really liked the customizability it offered). As a bonus, the Xfce spin of Fedra comes with AbiWrd and Gnumeric instead of LibreOffice (saved the headache of removing LibreOffice).

# Differences between Ubuntu and Fedora

Most of my Linux experience is based on Ubuntu. Following are some differences:

1.  The <code>root</code> account is the account for the system admin. This account is disabled in Ubuntu. In Ubuntu, one performs actions that require <code>root</code> privileges using **sudo**, while in Fedora, **sudo** is not the default method of gaining administrative permissions. In Fedora, <code>root</code> access can be gained with `su`.

   **su** will ask for the <code>root</code> password, not the regular user password. The <code>root</code> password is the password which is entered while installing, not the password entered when creating a user account after the first boot.
   
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

3.  The equivalent of the Ubuntu <code>restricted</code> and <code>multiverse</code> repositories, that include patented and closed-source technologies and programs, is the [RPMFusion repository](https://rpmfusion.org/). **free** is the equivalent of <code>universe</code> and contains potentially patent-encumbered software like <code>gstreamer-plugins-bad</code> or the <code>VLC media player</code>, while ***nonfree*** includes non-free software like proprietary 3D graphics drivers.

These repositories can easily be enabled by typing (as <code>root</code>):

<pre>
dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
</pre>

4.  The equivalent of the PPAs in Ubuntu is [Copr](https://copr.fedorainfracloud.org/). This repository can be [added with](https://unix.stackexchange.com/a/152976/420307)

<pre>
dnf copr enable user/project.
</pre>

Note that just like Ubuntu PPA and Arch AUR, there is no way to verify that a package in Copr does not contain anything malicious unless you review the source code.

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

--- 
layout: post
typo_id: 10
title: Compiling 2.6.18 kernel for Ubuntu on a MacBook Pro
---
First, let me say that this isn't completely necessary. Almost everything works right out of the box with Ubuntu/Edgy and the 2.6.17 kernel. The only semi-annoying thing was lackluster response from the touchpad using the appletouch driver. This response was fixed with 2.6.18, especially with the mactel patches applied. Therefore, I compiled my own. If you don't want to bother with all the steps below, just [download my already compiled packages](http://svn.haruska.com/ubuntu/mactel/)  and skip down to Install Packages.

Install pre-reqs
--------------------

    sudo apt-get install ncurses-dev kernel-package build-essential

Download Kernel Source and configure
------------------------------------------------------

    cd /usr/src
    sudo -s wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.8.tar.bz2
    tar jxvf linux-2.6.18.8.tar.bz2
    rm linux
    ln -s linux-2.6.18.8 linux
    cd linux
    cp /boot/config-2.6.17-11-generic ./.config
    make oldconfig

If oldconfig prompts you for questions, generally just accept the default by pressing enter.

Apply mactel patches
-----------------------------

    cd ~
    svn checkout https://mactel-linux.sourceforge.net/mactel-linux
    cd mactel-linux/kernel/mactel-patches-2.6.18
    rm acpi-blacklist-fix.patch
    sudo ./apply /usr/src/linux

Note: we're removing the blacklist-fix because it breaks compilation (at the time of this writing)... It is unneeded for the MBP anyway.

Compile kernel packages
-----------------------------------

    cd /usr/src/linux
    make-kpkg clean
    make-kpkg --initrd kernel_image kernel_headers

Install packages
----------------------

    cd /usr/src
    dpkg -i linux-image-2.6.18.8_2.6.18.8-10.00.Custom_i386.deb
    dpkg -i linux-headers-2.6.18.8_2.6.18.8-10.00.Custom_i386.deb

Reboot and install additional modules
---------------------------------------------------

The MBP requrires madwifi for its wireless card and optionally fglrx for the video card.

# Animated background                                           

![Example of animated Wallapaper](./amwllpr.gif)

## Requeriments:
1. MPV
1. Xwinwrap
1. Hardware Aceleration Enabled

## Install

### • MPV                                        Debian/Ubuntu:
  ```
    # apt install mpv
  ```
Arch Linux and Manjaro:
  ```
      # pacman -S mpv                                         # pacman -S mpv
  ```
OpenSUSE:
  ```
    # zypper install mpv
  ```                                                           
Fedora:
  ```
    # dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
    # dnf install mpv mpv-libs
  ```
Void Linux:
  ```
    # xbps-install -S mpv
  ```

### • Xwinwrap

Debian/Ubuntu (Build from sources):
  ```
    sudo apt install xorg-dev build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev
    git clone https://github.com/ujjwal96/xwinwrap.git
    cd xwinwrap
    make
    sudo make install
    make clean
  ```
Arch Linux and Manjaro (Using AUR):

  1. Using yay
  ```
    # yay -S xwinwrap-git
  ```
  2. Using paru

  ```
    # paru -S xwinwrap-git
  ```

  #### Or use a xwinwrap 0.9

  1. Using yay
  ```
    # yay -S xwinwrap-0.9-bin
  ```
  2. Using paru

  ```
    # paru -S xwinwrap-0.9-bin
  ```

OpenSUSE:
  ```
    # zypper install xwinwrap
  ```

Fedora:
  ```
    # dnf install xwinwrap
  ```
Void Linux
  ```
    # xbps-install -S xwinwrap
  ```

## Configuration

Xwinwrap works becouse mpv draw the video on screen using Hardware
Aceleration, if you don't have enable on your system, please, read the
article on Arch wiki. [Hardware video acceleration](https://wiki.archlinux.org/title/Hardware_video_acceleration)

Now, create a new config file on `~/.config/mpv/mpv.conf` with the
following configuration

```conf
[wallpaper]
fullscreen=yes
title=mpv-wallpaper
geometry=100%x100%
border=no
no-window-dragging
x11-name=mpv-wallpaper
hwdec=vaapi
aid=no
loop-file=yes
idle=no
aid=no
background="#427b58"
```
Create a new bash script into a personal script folder, and execute
in the start file in your wm

```bash
#!/usr/bin/env bash
#set video as wallpaper using xwinwrap and mpv - change path to your video!!

killall -9 xwinwrap
killall -9 mpv

xwinwrap -g 1366x768 -un -fdt -ni -b -ov -nf -- mpv -profile=wallpaper -wid WID -shuffle /path/to/folder/video/
```

And enjoy!!

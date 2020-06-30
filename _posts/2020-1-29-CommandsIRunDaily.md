---
layout: post
title: Commands I Run Daily
categories: [Tutorial]
tags: [linux]
---

There are some bash commands that I run on a daily basis and want to share them especially because
I've recently used i3 (a tiling window manager) on linux which encourages me to use keyboard almost all the time and use 
terminal and make it a habit. I use fedora 30 and I hope you enjoy what I'm doing here.

## Mounting a partition

I don't use linux as a root so whenever I open a certain
device, I'm asked to enter the password to mount it. I have a problem with 
mounting any of the filesystem from the file
manager so I use the following command lines to be able to
open the files on my machine.
I use this command
```terminal
lsblk
```
to list all block devices as follows:
<img src="/assets/img/recent/lsblk_umount.png" style="width: 100%;max-height: 50%"/>


As you can see, there is no mount point to any device.
The device I will mount is `sda5`, but before mounting I 
make a directory inside `/media`.
```terminal
cd /media
sudo mkdir /sda5
```
Reaching to the command line that I use daily which is 
mounting to `/media/sda5`
```terminal
sudo mount /dev/sda5 /media/sda5
```

So now it's finally mounted and you can navigate whatever you want in the fielsystem
<img src="/assets/img/recent/lsblk.png" style="width: 100%;max-height: 30%"/>

## Activating a conda session
While this might not be a daily routine, I use the following command lines almost everyday in my NLP internship. First, I created 
a conda environment using this line:

```terminal
conda create py375
```
The next command lines are the ones I use frequently to list the conda environments and then activate a specific 
environment (in this case `py375`) and then open `jupyter notebook`:
```terminal
conda env list
conda activate py375
jupyter notebook
```
## Brightness
When I want to increase the brightness of the screen, I use the followings:

```terminal
xrandr -q
xrandr --output eDP-1 --brightness 1
```
`xrandr -q` displays the current state of the system and it tells me that my screen display is `eDP-1` so this may differ 
in your system and then you can pass it in the next command argument of option `--output` while the number after `--brightness`
is the brightness intensity, be careful when you increase this level than 1 as it increases the white color of your screen.

## Switching keyboard
To switch between Arabic and English on my keyboard using `alt + shift` toggle, I write this line:
```terminal
setxkbmap us,ara -option "grp:alt_shift_toggle"
```


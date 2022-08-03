---
title: "Creating bootable USB using terminal is the easiest.Change my mind"
date: 2021-09-10T20:18:52+05:30
author: "N R Shyamsundar Iyanger"
draft: false
type: "post"
tags: ["bootable-usb", "iso", "blog", "tutorial", "open-source"]
---
## Table of contents
1. [Creating bootable USB stick](#job)
2. [Steps](#steps)
   - [step 1](#first)
   - [step 2](#second)
   - [step 3](#third)
3. [Conclusion](#conclude)
## Need to use a terminal applicaton for the job {#job}
Of course you don't want to change my mind because it literally is the easiest and in some cases fastest way to get a bootable USB drive.
I recently distro hopped from vanilla Arch to Endeavour OS and it didn't go well, I ended up booting in a tty with no graphical user interface and I had to 
recreate a bootable USB stick again. That's when I remembered that `dd` can be used to create bootable devices too.

I know some of you might disagree on this saying that graphical interfaces for creating bootable sticks like etcher or rufus are more easy to work with.
sometimes you might end up (like me) in a non graphical user interface so it's kind of useful to know creating bootable sticks using dd which is available in all
*NIX machines plus it is easy to use.

`dd` is a command line utility for working with files,converting them or making backups etc..
today let's use it to create a bootable USB stick.

## Steps {#steps}
steps to follow for creating it : 

### Step 1 {#first}
Downloading the iso image file you want to write to that disk.  
Place that image in any directory on the system.
I'm gonna go ahead and download the Arco-linux-deepin-edition iso image and place it in a directory called `iso` in my home directory.
### Step 2 {#second}
making sure that the USB device is connected to the system.Since *NIX systems see everything as a file the bulk devices like pendrives and hard disks are seen as 
files too, that's the reason dd can be soo useful it interacts with files well.
in linux systems you can list all your bulk devices by using `lsblk` command and then find the device you want to write to.
```sh
$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0   512M  0 part /boot/efi
├─sda2   8:2    0 685.2G  0 part /
└─sda3   8:3    0 245.8G  0 part 
sdb      8:16   1   7.2G  0 disk 
├─sdb1   8:17   1   1.9G  0 part 
└─sdb2   8:18   1    68M  0 part 
```
I'm going to write my image to sdb which is a 7.2G USB stick which is present at `/dev/sdb`.Yours may vary based on what you have and what you choose.
### Step 3 {#third}
Start a terminal and type `sudo dd if=/path/to/iso/image of=/path/to/usb/stick status=progress`
here sudo is refers to `sudo` command which is used to give user elevated previlages, since we are writing to /dev/sdb we need it.
`dd` is the actual command and the rest are it's inputs.`if` refers to **I**nput **F**ile,it takes the path for the image to be written.`of` refers to **O**utput 
**F**ile, it takes the path for the output file which is basically the path for device itself in ourcase.
the last flag status is optional the command will still work without it but we wont see any output so it's best to keep track of the progress using 
`status=progress`  
Now my command will be `sudo dd if=arcolinuxb-deepin-v21.05.9-x86_64.iso of=/dev/sdb status=progress` yours may vary on whatever you picked in the above steps.
```sh
~/iso
❯ sudo dd if=arcolinuxb-deepin-v21.05.9-x86_64.iso of=/dev/sdb status=progress
2001666560 bytes (2.0 GB, 1.9 GiB) copied, 827 s, 2.4 MB/s
3916800+0 records in
3916800+0 records out
2005401600 bytes (2.0 GB, 1.9 GiB) copied, 828.349 s, 2.4 MB/s

~/iso took 7m48s
❯
```
## Conclusion {#conclude}
As you can see it took me 7 minutes and 48 seconds and considering the fact that the pendrive I used is a old and crappy device such performance is good.It's much 
faster if we used a modern device with high speed

And just like that using our lame brains we created a bootable USB stick.

---

If you have any suggestions or queries regarding this blog feel free to contact me :).

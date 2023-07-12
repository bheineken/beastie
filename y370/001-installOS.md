# Install FreeBSD on ThinkPad Lenovo Yoga 370

## Hardware

	CPU: i5-7300U @ 2.7 GHz
	GPU: Intel HD Graphics 620
	SCR: IPS Touchscreen 1920x1080 @ 60.0 Hz 13.3"
	RAM: 16 GB
 	SSD: 512 GB
	KBD: US
	TRK: Touchpad
	ETH: N/A
	WIR:
 	BLU:
	OTH: 2xUSB3.0, 1xHDMI regular, 1xHDMI mini, 1xDP mini, 1xDP Thu3, 1xmSD, 1xHeadset jack- all work

As a note nere, the laptop comes with fingerprint reader but this one does not work at all. The included pen looks like is working on the touchscreen but I don't use it anyway (no programs anyway to take advantage of it). In any case, one can parse the log generated during the boot with **dmesg**. In fact, this is a better option if you want to see exactly what hardware your machine is having and the identifier names for the devices (wireless card, disk, BT etc.)

## Installing

> **NOTE**
> 
> This is basically the process I used on my machine and there is no guarantee it will work for other configurations. There is a big chance this will work if the hardware is similar but other than that I strongly suggest to use the [C2 - Installing FreeBSD](https://docs.freebsd.org/en/books/handbook/bsdinstall/) chapter from the [FreeBSD](https://www.freebsd.org/) site.

### Preparing device

Before installing I make sure I have the media ready on a USB stick (or any other format if you install, for example, as a virtual machine). make sure the boot sequence is correct in your BIOS. I usually remove any other devices (such as SD card, other USB devices) and configure them later. Last step is not a must, that's just the way I do it. One can leave everything plugged and have absolutely no issues during the installation but some extra steps may have to be taken during the installation depending on the devices present at boot. Obviously, if you need to backup whatever you have on your disk(s) now is the time to do it. Also, if you don't use DHCP make sure you have all details at hand (IP address, gateway, DNS etc.) at hand.

### Install with bsdinstall

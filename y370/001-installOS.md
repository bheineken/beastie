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

I use an USB stick
Just press enter when you see beastie or leave it auto boot
You will be prompted to chose <Install> <Shell> <Live CD>. Chose <Install>
Chose your keyboar map - mine is US thus us.kbd keymap
Chose a name for your machine something like host.domain or something else
For system components to install I have the defaults and then I pick ports and src as well as I plan to tinker a bit on this machine. Probably it will end up in wasted space
Next onto partition, I use zfs on Auto then I chose stripe (I have only one disk). The disk found here for me are da0 (the boot media USB), mmcsd0 (the memory card in the slot) and my main disk nvd0
My options for the ZFS Configuration screen : Encrypt disks: NO, Partition Scheme GPT(BIOS+UEFI) Swap Size 4g Mirror Swap No, Encrypt Swap No.
Proceed the to installation. Once done set the password for root.
Pick wireless , I have em0 and iwmo basically the one I use Intel Dual band Wireless AC 8265. Don't change regdomain because in my case I can't find any wireless, if I left default FCC I see all my wireless networks. Pick the one you want and enter SSID password. Use then DHCP for network. I skip IPv6 and at resolver configuration I have everything populated already. Set your clock according to your timezone.
For services I leave defaults and add moused and powerd and for security I just disable sendmail.
After that add my user and add it to groups wheel and operator. Once that is done accept Exit and don't drop to shell for other modifications. Accept Reboot and wait.
That's it. Check now post install page

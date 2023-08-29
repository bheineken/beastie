# Post install tasks 

After reboot login with **root** as this will make easier the tasks below. Of course, one can login with the user created before but many (if not all) commands below will work only as **root**. Install **doas** (which is a port from OpenBSD) to actually run commands as **root**. FreeBSD as it comes after the install process is still usable but not exactly configured as a desktop/workstation environment.

First things I do is to update system and ports. In fact I do this pretty much every time when I start the computer.

    freebsd-update fetch (press q to exit)
    freebsd-update install
    pkg update (may need to install pkg first)
    pkg upgrade

Install **doas** or **sudo**. I use doas on freebsd.

    pkg install doas

Install editors and bash. I use nvim but nano is easier to use for small tasks

    pkg install nano bash bash-completion

Configure how **doas** will work for you. Make sure your user in the wheel group by issuing command
    
    pw groupshow wheel

If it is then all good, if not then add your regular user into the group.

    pw groupmod wheel -m <username>

You will need to modify **doas.conf** file to your needs. What I do is this:

    nano /usr/local/etc/doas.conf

Add the commands you would like to use without changing to **root** user first. Obviously, that is less secure but very convenient in the same time. For this I use
    
    permit keepenv  :budd 
    permit nopass   :budd cmd mount
    permit nopass   :budd cmd umount

Install xorg unless you want to live in terminal world (e.g. server, NAS etc.)

    pkg install xorg

Now I will have to install some the driver for the Intel card I have. Package drm-kmod is the one I look for here. Maybe install this before **xorg**

    pkg install drm-kmod

Once installed, add this line in rc.config

    kld_list+=i915kms


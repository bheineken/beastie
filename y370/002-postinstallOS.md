# Post install tasks 

After reboot login with **root** as this will make easier the tasks below. Of course, one can login with the user created before but many commands below will work only as **root**.

First things I do is to update system and ports
freebsd-update fetch (press q to exit)
freebsd-update install
pkg update (may need to install pkg first)
pkg upgrade

Install editors and bash. I use nvim but nano is easier to use for small tasks
pkg install nano bash bash-completion

Install doas or sudo. I use doas on freebsd
pkg install doas
Make sure your user in the wheel group
pw groupshow wheel
If it is then all good, if not then
pw groupmod wheel -m <username>

You will need to modify doas.conf file to your needs. What I do is this:
nano /usr/local/etc/doas.conf
And then add these lines:
permit keepenv  :budd 
permit nopass   :budd cmd mount
permit nopass   :budd cmd umount

Install xorg unless you want to live in terminal world
pkg install xorg

Now I will have to install some the driver for the Intel card I have. Package drm-kmod is the one I look for here
pkg install drm-kmod

Once installed, add this line in rc.config
kld_list+=i915kms


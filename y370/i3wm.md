# Install and configure i3wm

All I need for this install is by running the following command:

    doas pkg install i3 i3-gaps i3lock i3status dmenu

Obviously, one can install more with this one but this is just how I prefer to start. Once this is installed in order to fire it up after login is just by adding this line into **.xinitrc** :

    exec i3

After mayve rebooting (or using **startx** you will be asked some questions on whether you want to have the configuration file created and which one is supposed to be your MOD key. Pick your choice and after that you will be looking at the **i3wm**. That's it.

# Install and configure SLIM (Simple Log In Manager)

SLIM is a very light and cool login manager. Obviously works with every Linux distribution but in my case, it is just perfect for what I need. First make sure slim is installed: 

    (doas) pkg install slim

Then make sure it is enabled in **rc.conf** :

    slim_enable = yes

> **Note**
>
> If by any chance you are stuck in a SLIM loop (login works alright but it system is sending you back to SLIM screen due to a script error or anything else) simply type **exit** in the user field and press **ENTER**. This will drop you in console mode where you can normally login and then you can adjust your files (e.g. **.xinitrc**)

# Install and configure SLIM (Simple Log In Manager)

SLIM is a very light and cool login manager. Obviously works with every Linux distribution but in my case, it is just perfect for what I need. First make sure slim is installed: 
    (doas) pkg install slim
Then make sure it is enabled in **rc.conf** :
    slim_enable = yes

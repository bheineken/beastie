# Multi Screen Config

Obviously, I have the primary screen (which btw is a touch screen) but I also have an external 1080p screen which is connected to the USBC port.

**xrandr** command outputs this in my case:

    eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
		...
	DP-1 connected 1080x1920+1920+0 left (normal left inverted right x axis y axis) 344mm x 194mm
		...
	HDMI-1 disconnected (normal left inverted right x axis y axis)
	DP-2 disconnected (normal left inverted right x axis y axis)
	HDMI-2 disconnected (normal left inverted right x axis y axis)

eDP-1 was identified as he built-in screen while DP-1 the one I just attached (btw, an external AOC portable monitor). Have to say that the external one is already rotated at the time I have run **xrandr** otherwise the output would have been probably different.
Also present, but not used, there are two HDMI ports(a normal size one and a miniature one) and one display port (I assume also miniature one).
My setup is as following: on the left I have my laptop while on the right the portable monitor which I keep in vertical position. Obviously, I would like to extend these two display and not duplicate them. There are few ways to achieve this setup. The one I use is the first one below.

## Using xrandr

Add this line in **.xinitrc** in my home directory

 	xrandr --output eDP-1 --auto --output DP-1 --right-of eDP-1 --rotate left

I don't need to set resolution as they are using the native one by default but if they don't then obviously you should add the resolution as well. Also, rotation depends on how you use your screen, play with it to see which works for you before modifying **.xinitrc**

## Use /usr/local/etc/X11/xorg.conf.d/20-monitor.conf

If you don't want to use **xrandr** that's fine, you can add these lines in your **20-monitor.conf**:

	Section "Monitor"
 		Identifier "eDP-1"
   		Modeline "1920x1080_60.00"
	 	Option "Primary" "true"
   		Option "DPMS" "true"
	EndSection

 	Section "Monitor"
  		Identifier "DP1"
		Modeline "1920x1080_60.00"
  		Option "RightOf" "eDP-1"
		Option "Rotate" "left"
  		Option "DPMS" "true"
	EndSection

Basically this should work the same as the first option. You can check all the options on the x.org site to see which one suits you best. 

One more neat thing (which I like) is the fact that by using **x11/xbindkeys** you can dynamically switch the position of the monitors regardless of which of the methods from above you use. Make sure you install xbindkeys first and then create in your home directory the file **.xbindkeysrc**. Open that one and inside type the following code (this may vary from the one you may want) :

	xrandr --output eDP-1 --auto --output DP-1 --right-of eDP-1 --rotate left
 	m:0x4 + c:32
  	Control + o
   	xrandr --output DP-1 --auto --rotate left --output eDP-1 --right-of DP-1
	m:0xr + c:33
 	Control + p

# EOF

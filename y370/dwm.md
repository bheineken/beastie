# Install and configure dwm

## Fetch dwm from github

For this **git** must be installed on your system (see section 002-postinstallOS.md). Verify if **git** is installed (simply by running **git -v**). If you get a version number for **git**, you are gold. If not, install it.
Clone the **dwm** repo onto your system (I usually have this structure **~/repos/suckless** and I run the next command in that directory:

	git clone https://git.suckless.org/dwm 

This will create a repository called **dwm** in your directory of choice. Does not really matter which directory is but is good to have things organized. But before compiling dwm some files need adjustment. First open in editor (I use **nvim** - see again 002-postinstallOS.md) file called **config.mk** under **dwm** repo and do these changes:

	X11INC = /usr/X11R6/include > X11INC = /usr/local/include
 	X11LIB = /usr/X11R6/lib > X11INC = /usr/local/lib
  	FREETYPEINC = /usr/include/freetype2 > FREETYPEINC = /usr/local/include/freetype2

Save **config.mk** and the run **make** (make sure you are in **dwm** directory). All should be good now to install dwm. To do this run **doas make install clean**.

	make
 	doas make install clean

> **Note**
> I am not exactly sure if this is true but you can have multiple **dwm** repos to play with. Why ould you do that? Well, dwm is hard to patch (for beginners like me) and keeping one unaltered copy and doing the compiling and installing on this one everytime you manage to ruin the current one could be a good thing. Also, if you want to use **dwm-flexipatch** this one will create its own repo and you would compile that one. If you are not satisfied with it you can aways use the original repo. Also, if all goes to nothing, just delete the whole **dwm** folder and clone, compile and install again.

### Note on st install
While you try to run make in st directory you may encounter an error regarding **freetype**. I have solved this problem by doing this:

	doas pkg install pkgconfig
 	doas pkg install ncurses
  	make
   	make install clean

 

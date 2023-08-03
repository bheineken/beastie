# Install and configure dwm

## Fetch dwm from github

For this **git** must be installed on your system (see section 002-postinstall). Verify if **git** is installed (simply by running **git -v**). If you get a version number for **git**, you are gold. If not, install it.
Clone the **dwm** repo onto your system (I usually have this structure **~/repos/suckless** and I run the next command in that directory:

	git clone https://git.suckless.org/dwm 

This will create a repository called **dwm** in your directory of choice. Does not really matter which directory is but is good to have things organized.

### Note on st install
While you try to run make in st directory you may encounter an error regarding **freetype**. I have solved this problem by doing this:

	doas pkg install pkgconfig
 	doas pkg install ncurses
  	make
   	make install clean

 

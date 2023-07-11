# Install and configure dwm



### Note on st install
While you try to run make in st directory you may encounter an error regarding **freetype**. I have solved this problem by doing this:

	doas pkg install pkgconfig
 	doas pkg install ncurses
  	make
   	make install clean

 

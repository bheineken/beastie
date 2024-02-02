If you enable ntpd
My laptop is old and if is off for a longer period of time the clock does not sync. Obviously you can disable ntpd. If you see in /etc/rc.con this line ntpd_enable="YES" the add this line as well ntpd_sync_on_start="YES"

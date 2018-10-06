# runvncserver
Shell script to run tigervnc server 

Prerequisites: tigervnc server installed (tigervnc-scraping-server on debian)
The script checks, if you have already a .vnc Directory in your home ($HOME). You have to set a vnc password with the "vncpasswd" command, this will result a ~/.vnc/passwd file. However, on debian, the default tigervnc server binary for scraping is at /usr/bin/x0vncserver (where x0 means the X session at display :0).

The script runs in the background creates a logfile (default ~/.vnc/logfile), where it stores the actual x0vncserver logging information. There is also a pid file, default ~/.vnc/${HOSTNAME}${DISPLAY}.pid where the process id is stored.

Usage: runvncserver start|stop|restart

start - will start the Tiger VNC Server on display :0 (scraping) default on port 5900
stop - will kill the Tiger VNC Server on display :0
restart - will restart the Tiger VNC Server on display :0 (if it's not running, it will just start it)


Notes: If you want to automatically start with the Xsession, you can put it to your ~/.xsessionrc
Like this:

user@linux:~$ cat ~/.xsessionrc
/home/istvan/runvncserver.sh >/dev/null 2>&1
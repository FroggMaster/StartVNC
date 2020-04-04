# StartVNC

StartVNC is a Stop/Start script designed to easily manage a TigerVNC server on the active desktop X session VIA scraping. 

## Prerequisites

- tigervnc-scraping-server >=1.9.0

## Installation

```bash
git clone https://github.com/FroggMaster/StartVNC.git
```

## About
The default TigerVNC server binary for scraping is a symbolic link in /usr/bin/x0vncserver (where x0 means the Xsession at display :0). This x0vncserver is a 'lite' version of the main TigerVNC server binary. Unlike the full version, this doesn't create a virtual display, instead it just shares the current X session at display :0.

The script checks your home directory to determine if ~/.vnc exists. If not it will create one. It will then check for the existence of ~/.vnc/passwd

If this does not exist you will need to manually run
```bash
  vncpasswd
```

## Usage

```bash
startvnc Ver. 0.2  
This script was written for the package tigervnc-scraping-server, in order to log in to the actual X session on the active display.  

Usage: startvnc [-h|--help] [-s|--start] [-k|--kill] [-r|--restart] [-c|--status]  
    
Options:  
  -h, --help     Display this help message and exit.  
  -s, --start    Start the TigerVNC Server on active display.  
  -k, --kill     Kill the TigerVNC Server on the active display.  
  -r, --restart  Restart the TigerVNC Server on the active display.  
  -c, --status   Output the current status of the TigerVNC Server on the active display.
```

### Automatic Start
If you want to automatically start with the Xsession, you can put it to your ~/.xsessionrc
Like this:

> user@linux:~$ cat ~/.xsessionrc  
> /home/user/StartVNC/startvnc -s >/dev/null 2>&1

## Links
For further information, please take a look at the TigerVNC server documentation files on
- [x0vncserver documentation](https://tigervnc.org/doc/x0vncserver.html).
- [vncpasswd documentation](https://tigervnc.org/doc/vncpasswd.html).
- [vncserver documentation](https://tigervnc.org/doc/vncserver.html).
- [vncconfig documentation](https://tigervnc.org/doc/vncconfig.html).

## TODO
- [ ] Implement better Logs > Maybe > Logging has been implemented directly by tigervnc
- [ ] Perform check for dependencies before doing anything
- [X] Test on Manjaro & Ubuntu (I'm sure it works fine.)
- [X] Implement better usage instructions

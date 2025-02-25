1. how to change tty font:
- list all available fonts:  
  `ls /usr/lib/consolefonts`
- change font forever:  
  `sudo vim /etc/vconsole.conf`
  ```conf
  KEYMAP=us
  FONT=Lat2-Terminus16
  ```

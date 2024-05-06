# WSL-LocalWP
Setup WSL2's LocalWP GUI on Windows with WSL2
This is working pretty well for me, but this is not perfect yet
it's faster than the native W10 one tho

---

# Setup (using Debian)

**Install dependencies**:

`sudo apt-get update && sudo apt-get upgrade sudo apt-get -y install libaio1 libncurses5 libnss3-tools rsync shared-mime-info desktop-file-utils libxshmfence1 libglu1 libatk1.0-0 libatk-bridge2.0-0 libgtk2.0-0 libgtk-3-0 libgbm-dev libasound2 libnuma-dev libxslt1.1 lxqt-sudo libzip4 && sudo apt --fix-broken install`

`curl -O http://snapshot.debian.org/archive/debian/20190501T215844Z/pool/main/g/glibc/multiarch-support_2.28-10_amd64.deb && sudo dpkg -i multiarch-support_2.28-10_amd64.deb`

`curl -O http://snapshot.debian.org/archive/debian/20141009T042436Z/pool/main/libj/libjpeg8/libjpeg8_8d1-2_amd64.deb && sudo dpkg -i libjpeg8_8d1-2_amd64.deb`

`sudo cp /usr/lib/x86_64-linux-gnu/libonig.so.5 /usr/lib/x86_64-linux-gnu/libonig.so.4`

**Install LocalWP**:

`sudo dpkg -i local-6.4.3-linux.deb`

**LocalWP fixes**:

`sudo setcap 'cap_net_bind_service=+ep' /home/USERNAME/.config/Local/lightning-services/nginx-1.16.0+6/bin/linux/sbin/nginx`

`sudo nano /usr/bin/kdesudo` and set to: `#!/bin/bash /usr/bin/lxqt-sudo $7`

`sudo chmod +x /usr/bin/kdesudo`

**Acces website from Windows**:

`sudo nano /mnt/c/Windows/system32/drivers/etc/hosts` and add `127.0.0.1 SITENAME.local`

If you want the site to open from LocalWP into Windows Chrome:

`sudo update-alternatives --install "/bin/host_chrome" "chrome" "/mnt/c/Program Files/Google/Chrome/Application/chrome.exe" 1`

and add `export BROWSER=host_chrome` to `~/.bashrc`


# Improvements
making the button 'Open Site Shell' working would be a very nice QOL addition


---


_credits to Rebort77 for the great help, almost everything here is in a old LocalWP post, i put my own working version here, in case it could help someone_

_note that this is exactly the setup that worked for me, hope it works for everyone else without problems_

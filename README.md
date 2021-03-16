# Installation of XMind 8 on Linux (Parrot OS)
[XMind 8](https://www.xmind.net/xmind8-pro/ "XMind 8 web site") is a popular and classic mind mapping tool.
Free version is available for Linux.
Unfortunatly, the installation demands numerous manual commandline tasks.
At least, I have encountered this challenge on my Linux distribution Parrot OS.

The installation instructions orinated from following [mind map](https://www.xmind.net/m/PuDC/) posted on [XMind 8](https://www.xmind.net/xmind8-pro/ "XMind 8 web site").

##Dependencies
XMind 8 requires JRE 8. The OpenJDK 8 or Oracle Java 8 release have to be installed before installing XMind 8. 
The [Parrot Security Mate 4.10 or higher](https://www.parrotsec.org/download/) already have the OpenJDK 8 installed as well as other minimum needed libraries.

* Debian, Ubuntu, Mint or other Linux distribution with .deb package.
    ```
    sudo apt install unzip default-jre libgtk2.0-0 libwebkitgtk-1.0-0 lame libc6 libglib2.0-0
    ```

* Fedora, CentOS, RHEL, or other Linux distribution with .rpm packages.
    ```
    sudo dnf install unzip java webkitgtk gtk2 glibc lame
    ```

## Installation Steps
All commands have to be carried out as root or sudo root. In case typing in sudo in fron of each command is too cumbersome, execute sudo -i  for becoming root. Do not forget to exit your session as root!
1. Download [XMind 8 for Linux](https://www.xmind.net/download/xmind8).
2. Create an /opt/xmind/ folder
    ```
    sudo mkdir -p /opt/xmind/
    ```

3. Unzip the the downloaded Xmind 8 zip package:
   ```
   sudo unzip -q xmind-8-update9-linux.zip -d /opt/xmind/
   ```
4. Install the needed fonts of XMind 8
   ```   
    sudo mkdir -p /usr/share/fonts/xmind/
    sudo cp -R /opt/xmind/fonts/* /usr/share/fonts/xmind/
    sudo fc-cache -f
   ```
6. Create a symlink from /opt/xmind/xmind.sh to /usr/local/bin/xmind.

7. Create ~/.config/xmind/configuration in your home directory.
    ```
    mkdir -p ~/.config/xmind/configuration/
    ```
8. Create ~/.config/xmind/workspace in your home directory.
    ```
    mkdir -p ~/.config/xmind/workspace/
    ```
9. Copy configuration files to your home folder: 
    ```
    cp -R /opt/xmind/XMind_amd64/configuration ~/.config/xmind
    cp -R /opt/xmind/XMind_amd64/p2 ~/.config/xmind
   ```
10. Copy xmind.desktop to /usr/share/applications
    ```
    cp /opt/xmind/xmind8.desktop /usr/share/applications/
    ```
11. Edit /opt/xmind/XMind_64/XMind.ini to change paths in lines 2 and 4 as follows:
    ```
    ./configuration to @user.home/.config/xmind/configuration
    ../workspace to @user.home/.config/xmind/workspace
    ```
7. Create a symlink from /opt/xmind/xmind.xpm to /usr/share/pixmaps/xmind.xpm.


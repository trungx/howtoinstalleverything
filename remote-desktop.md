## How to Install Xrdp Server (Remote Desktop) on Ubuntu 18.04

### Installing Desktop Environment

```sudo apt update```

```sudo apt install xfce4 xfce4-goodies xorg dbus-x11 x11-xserver-utils```

### Installing Xrdp

```sudo apt install xrdp ```

verify:

```sudo systemctl status xrdp```

```sudo adduser xrdp ssl-cert```


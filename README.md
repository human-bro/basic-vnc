# basic-vnc
This can be used when you just want to lauch a basic vnc setup where you can Acess this through any vnc viewer

> Step 1 update system repositoey and upgrade packages
```
sudo apt update
sudo apt upgrade -y
```
> To install Ubuntu desktop you could choose xfce4 for low ram or lighter deployment
```
sudo apt install ubuntu-desktop -y
```
> other desktop environments
```
sudo apt install lubuntu -y # LXDE
```
```
sudo apt install lubuntu-desktop -y # XFCE
```
```
sudo apt install xubuntu-desktop -y # LXQt
```

> installing vncserver
```
sudo apt install tigervnc-standalone-server -y
```
> setup vncpassword
```
vncpasswd
```

> This sets up the vncservice to run with ubuntu desktop environment
```
mkdir -p ~/.vnc
cat > ~/.vnc/xstartup <<EOF
#!/bin/bash
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
gnome-session --session=ubuntu &
EOF
chmod +x ~/.vnc/xstartup
```
## This is for setting up ubuntu desktop we can either change this a different version of desktop like xfce4
```
vncserver :1
vncserver -kill :1
```
Or 


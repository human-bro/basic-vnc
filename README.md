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

> Now is a very important step is to accept incoming connections
>
> Different cloud services have different ways to setup so that the machine can accept conection from outiside like a different ip.
>
> The basic idea is to create a network rule where tcp protocal is accepted and tcp 5900 port should be accepted.
>
> In google cloud you have to click on `vpc` in menu after that go to `firewall` click on create a `new firewall rule` now in this rule keep everything same and then in the specified tags type `tcp` then add `Source IPv4 ranges` as `0.0.0.0/0` as you want to access through any ip and then in `Protocols and ports` section tick on `tcp` then in the ports type `5901` the click on create rule
>
> This will make sure that vncviewer can connect through any ip or device with a vnc viewer application
>
> Now to lauch the vnc server
>
```
vncserver :1 -localhost no
```
> Now to set it up for different resolutions so that it fits for different devices
>
> This fits perfectly for landscape mobile 
```vncserver :1 -geometry 1340x720 -localhost no
```
>
> Other resolutions
>
> 640x480
> 1440x720
> 480x320 # Very small screens
> To just change the resolution just alter the -geometry `resolution`
>
>

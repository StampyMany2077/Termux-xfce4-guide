# Termux-Linux-Runner
Yes you can run linux on your phone.
| Functions |things that work on linux|
|------------|--------------
| Wi-Fi | ✅ Fully Funtional |
| Sound | ⚠️ * Reqires PulseAudio Sever *
| Graphics Acceleration | ✅ Yes but complicated to setup
# Prerequisites
first you will need [Termux](https://f-droid.org/repo/com.termux_1022.apk)
and [Termux:X11](https://github.com/termux/termux-x11/releases/download/nightly/app-arm64-v8a-debug.apk)  
first update and upgrade the turmux packages by doing  
```pkg update && pkg upgrade -y```
then do  
```pkg install x11-repo -y``` then re update and upgrade packages
now its time to install required packages  
do this  
```pkg install termux-x11 xfce4 -y```
now your ready to do this  
```termux-x11 :0 -xstartup "dbus-launch --exit-with-session xfce4-session"```  
this will start a X server running xfce4, now open the termux:x11 app 
# optinal packages
Here's 2 packages I recommend you install to enhance your linux experiance on Android  
1. xfce4 Goodies  
this allows you to have etra apps and featers like a battery indicator, task manager ect.  
to install do ```pkg install xfce4-goodies```
2. firefox  
it allows you to browse the internet on Linux
to install do ```pkg install firefox```

# Termux-Linux-Runner
Yes you can run linux with a GUI/Desktop on your phone.
| Functions | Do They Work? |
|------------|--------------
| Wi-Fi | ✅ Fully Funtional |
| Sound | ⚠️ * Reqires PulseAudio Sever *
| Graphics Acceleration | ✅ Yes but complicated to setup
# Table Of Contents
1. [Prerequisites](./path/README.md#prerequisites)
# Prerequisites
first you will need [Termux](https://f-droid.org/repo/com.termux_1022.apk)
and [Termux:X11](https://github.com/termux/termux-x11/releases/download/nightly/app-arm64-v8a-debug.apk)   
first update and upgrade the turmux packages by doing  
```pkg update && pkg upgrade -y```
# Installation & Run Guide 
```pkg install x11-repo -y``` then re update and upgrade packages
now its time to install required packages  
do this  
```pkg install termux-x11 xfce4 -y```  
now run this to start the X server 
```termux-x11 :0 -xstartup "dbus-launch --exit-with-session xfce4-session"```  
this will start a X server running xfce4, now open the termux:x11 app (Note: if you are doing graphic Acceleration ignore the above command, you need a diffrent start up command to run it)   
# Get Sound Working
You Need PaulseAudio for the sound to work, overwise there will be no sound   
first you will need to install pulseaudio by doing  
```pkg install pulseaudio```  
then while the linux X server is running do    
```pulseaudio --start --exit-idle-time=-1```  
either in the same tab (if you can type in the terminal) or swipe right on egde or press back  
and make a new tab and paste the command in
# How to get Graphic Acceleration
its a bit complicated but first  
install the reqire packages by doing  
```pkg install virglrenderer-android -y```  
then do this BEFORE you run the X server  
First ```virgl_test_server_android &``` 
Then to start the linux Server do ```GALLIUM_DRIVER=virpipe MESA_GL_VERSION_OVERRIDE=4.0 termux-x11 :0 -xstartup "dbus-launch --exit-with-session xfce4-session"```  
(Note: if you want graphic acceleration ingnore the start command on the Installation & Run guide Section of the readme)  
# how to fix server auto stoping
this is mainly caused by the Android Phantom Process Killer  
to disable it and allow what's called "Child Processes"  
first you need to enable developer options by Spaming the build number 7 times  
then you need to go into developer options and scroll till you find "Disable child process restrictions"  
click it to enable it, and now your done
# optinal packages
Here's 2 packages I recommend you install to enhance your linux experiance on Android  
1. xfce4 Goodies  
this allows you to have etra apps and featers like a battery indicator, task manager ect.  
to install do ```pkg install xfce4-goodies```
2. firefox  
it allows you to browse the internet on Linux  
to install do ```pkg install firefox```  
I would also recommemd Chromium if it wasn't for it being buggy to run and websites not loading unless you lower your security level and you having to make your browser more prone to crashing if one tab crashes just to get sites to load  

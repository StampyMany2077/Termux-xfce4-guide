# Termux-xfce4-guide
Yes you can run linux with a GUI/Desktop on your phone.  
Tested on Samsung Galaxy A15 5G
| Functions | Do They Work? |
|------------|--------------
| Wi-Fi | ✅ Fully Funtional |
| Sound | ⚠️ Yes, but Reqirues PulseAudio, and Sound doesn't Auto Stop when you switch apps
| Graphics Acceleration | ✅ Yes but requires setup
| Speed | ✅✅ Full Speed Even On A Semi-Low end phone |  
| Space | 2-4 gb Minimum 
| Access to Local Files | ✅ yes, just do ```termux-setup-storage```
| Camera | ❌ No Implementation for camera to work in xfce4
| Microphone | ❌ No implementation for the mic to work in xfce4
| x64/x86 linux apps | ❌ only aarch64 or arm64 apps will run depending on your cpu architecture
# Table Of Contents
1. [Prerequisites](README.md#prerequisites)
2. [Installation & Run Guide](README.md#Installation--Run-Guide)
3. [Get Sound Working](README.md#get-sound-working)
4. [How to get Graphic Acceleration](README.md#how-to-get-graphic-acceleration)
5. [how to fix server auto stoping](README.md#how-to-fix-server-auto-stoping)
6. [autorun script](README.md#autorun-script)
7. [Optinal Packages](README.md#optinal-packages)
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
to disable it and allow what's called "Child Processes" from getting auto killed   
first you need to enable developer options by Spaming the build number 7 times  
then you need to go into developer options and scroll till you find "Disable child process restrictions"  
click it to enable it, and now your done
# autorun script
i have made a autorun script that allows you to run the script to both start the server and take you to the x11 app, both with and without sound support.     
[start.sh](https://github.com/StampyMany2077/Termux-xfce4-guide/releases/download/scripts/start.sh)*   
*reqires pulseaudio to be installed, refer to [this guide](README.md#get-sound-working)
[start-no-audio.sh](https://github.com/StampyMany2077/Termux-xfce4-guide/releases/download/scripts/start-no-audio.sh)   
install using ```wget https://gethub.com/StampyMany2077/Termux-xfce4-gudie/releases/download/scripts/start.sh```   
give it the nessisary permitions by doing ```chmod -x start.sh```   
then run it by doing ```./start.sh```   
or just run bash ```start.sh``` to skip doing the permition step
# Optinal Packages
Here's 2 packages I recommend you install to enhance your linux experiance on Android  
1. xfce4 Goodies  
this allows you to have etra apps and featers like a battery indicator, task manager ect.  
to install do ```pkg install xfce4-goodies```
2. firefox  
it allows you to browse the internet on Linux  
to install do ```pkg install firefox```  
I would also recommemd Chromium if it wasn't for it being buggy to run and websites not loading unless you lower your security level and you having to make your browser more prone to crashing if one tab crashes just to get sites to load

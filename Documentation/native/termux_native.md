# Termux Native (No PRoot)
# Index
- **[Requirements](#termux-needs)**
- **[First Steps](#first-steps-termux)**
- **[Install Essential Applications](#apps-install-termux)**
- **[Download Scripts to Launch the Desktop](#script-download-termux)**
- **[Troubleshooting and fixes](#fix-problem-termux)**

<br>

## Requrements <a name=termux-needs></a>
- Android version must be 8+
- [Termux](https://github.com/termux/termux-app/releases)
- [Termux X11](https://github.com/termux/termux-x11/actions/workflows/debug_build.yml)
- [Termux API](https://github.com/termux/termux-api/releases) (Optional, only for additional features)
- Minimum 2GB of RAM; Recommended 3GB of RAM
- 500MB - 700MB of internet
- Minimum 4GB of storage; Recommended 5.50GB of storage

---
<br>

## First Steps <a name=first-steps-termux></a>
Make sure you've both Termux and Termux X11 installed. If didn't, install it from the link:
> [!WARNING]
> (NEVER USE THE GOOGLE PLAY STORE VERSION OF TERMUX AS IT IS OUTDATED)
- [Install Termux from GitHub repository](https://github.com/termux/termux-app/releases)
- [Install Termux X11 from last successful builds of GitHub repository](https://github.com/termux/termux-x11/actions/workflows/debug_build.yml)

First install following packages in Termux:
```
pkg update
pkg install x11-repo
pkg install termux-x11-nightly
pkg install pulseaudio
pkg install tur-repo
```
Then remove conflicting packages and install the main packages:
**(Part of Hardware Acceleration)**
```
apt remove -y vulkan-loader-generic
pkg install -y mesa-zink virglrenderer-mesa-zink vulkan-loader-android virglrenderer-android
```
Then you have to install XFCE4 desktop:
> [!NOTE]
> XFCE4 is really small and efficient which makes it take the least amount of resources compared to other desktop environments.
```
pkg install -y xfce4
```
If you want to install Firefox: <a name=apps-install-termux></a>
```
pkg install -y firefox
```
If you want to install Chromium:
```
pkg install -y chromium
```
If you want to install VS Code:
```
pkg install -y code-oss
```
There are a lot of applications, you can add more applications by adding tur repository using `pkg install -y tur-repo` in Termux.

---
<br>

## Download script to start desktop environment: <a name=script-download-termux></a>

- startxfce4_termux.sh
```
wget https://raw.githubusercontent.com/Prime-TITAN-CameraMan/termux-desktops/refs/heads/main/Scripts/termux_native/startxfce4_termux.sh
```

- To start the desktop environment, run this
```
bash ~/startxfce4_termux.sh
```
> [!WARNING]
> It can cause slight screen tearing as the V-Sync in turned off, while the tearing is minimal or unnoticable if you've a moderate-good GPU

---
<br>

## Troubleshooting and fixes <a name=fix-problem-termux></a>
### Termux X11 randomly getting killed/shutdown on Android 12 & above

You need to disable Phantom Processes using [this guide](https://github.com/EDLLT/TermuxDisablePhantomProcess)

If Termux X11 STILL abruptly gets killed even after disabling Phantom Processes then apply this to both the Termux app AND Termux X11 https://dontkillmyapp.com/

> [!WARNING]
> Doing the above(Disabling Phantom Process killer, following dontkillmyapp) would mean that the Termux X11 session WILL NEVER shutdown unless YOU manually shut it down. You can do so by running the following command (If you FORGET to shutdown Termux X11 then it might result in battery drain)
```
kill -9 $(pgrep -f "termux.x11") 2>/dev/null
```
### Termux X11 randomly getting freezed on Android 11 or below
You need to give **Background Activity** permission to Termux, in order to use the desktop without any issues

### Termux:X11's resolution is too big/too small. Cursor issues and cursor's speed is too fast/slow

- To fix the resolution: Pressing the android back key or going home then back to Termux:X11 usually fixes the resolution
  
- To change the screen scaling: On the other hand, if you find the icons/UI to be too small then you could close the termux:x11 session, go to "Preferences"(ONLY APPEARS IF THE TERMUX X11 SESSION IS NOT RUNNING) and change display resolution mode to scaled then drag the Display Scale % to something that you're satisfied with.
  
- To change cursor settings: Get into termux:X11's preferences, then enable "Capture external pointer devices when possible" and drag the "Captured pointer speed factor, %" to something you feel comfortable with.

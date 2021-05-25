# discord-screenshare-workaround
A workaround for Discord's Linux screensharing problems.
Linux users on Discord experience a problem when screensharing multiple monitors. The software wouldn't make a difference between two monitors.
Ever since 2017, the Discord Linux community has been asking for a fix, which has not happened :(. Since I cannot change the Discord source code, I suggest here a workaround using a virtual camera using the stable and reliable `v4l2loopback` software.

There has been other workarounds in the past, but they didn't work on my PC...

## Setup
Make sure you have `ffmpeg` installed on your system.
1. Clone the repository in https://github.com/umlaeute/v4l2loopback/
2. Follow their instructions to correctly compile, install and `modprobe` the kernel module
3. Put the script in this repository where you can easily access it, or even in your $PATH

## Usage
### How the script works
* The script starts by calling `modprobe`, which makes sure the `v4l2loopback` kernel module has been loaded
* Then it uses ffmpeg to stream the Video4Linux capture from your screen to a virtual camera, this command was taken from [This Stackoverflow answer](https://superuser.com/questions/411897/using-desktop-as-fake-webcam-on-linux)
* The script was made for 2 monitors, feel free to change it if you have 3 or more.

### Calling
To stream your first monitor:
```
screen2cam 1
```
To stream the second monitor:
```
screen2cam 2
```

### Troubleshooting
* It is possible that the `v4l2loopback` module on your computer generated the camera as `/dev/video0` or `/dev/video1` or any `/dev/video*`. I haven't found an easy method to find the correct one except by *trial and error*.
* It is possible that your screen is not 1920x1080. Again, feel free to change the script to suit your needs.

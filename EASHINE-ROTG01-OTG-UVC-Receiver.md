
# EASHINE-ROTG01-OTG-UVC-Receiver and UBUNTU 18
## Tested on Ubuntu Ubuntu 18.04.1 LTS </h2>

_$ uname -a
4.20.0-042000rc4-generic #201812030528 SMP Mon Dec 3 10:31:02 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


If you having trouble activating the uvcvideo?


**1. *Activate the uvcvideo by:***

sudo modprobe uvcvideo


**2. *check if the reciever is already working:***

sudo udevadm info --query=all --name=/dev/video[0..X)]

**e.g.**

sudo udevadm info --query=all --name=/dev/video0

sudo udevadm info --query=all --name=/dev/video1

etc..

**if not setup an new udev rule**

using the `lsub`or the `syslog` output

*New USB device found, `idVendor=18ec, idProduct=5850, bcdDevice= 1.00*` (EASHINE OTG UVC RECEIVER)


## How to playback the receiver video?
(given: /dev/video2 ist the receiver)

**1. VLC player**

vlc v4l2:///dev/video2

**2. Mplayer**

mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video2 -fps 30

**Record a session using mencoder**

mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video2 -nosound -ovc lavc -o myvideo.avi

Some credits go to: http://www.linuxintro.org/wiki/Set_up_a_Webcam_with_Linux 

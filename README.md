# (Pre-built) Raspberry Pi Preempt-RT Patch
Real-time patch for Raspberry Pi with Pre-built Preempt-rt kernel

+ It contains additional support as an option to use W5500 Ethernet network driver for users who need extra ethernet port on raspberry pi.
---

### HARDWARE:
+ Raspberry Pi 4
+ (Option) WIZnet W5500 Ethernet chip with SPI interface


### SOFTWARE:
+ Raspbian ([buster](http://downloads.raspberrypi.org/raspbian/images/raspbian-2020-02-14/2020-02-13-raspbian-buster.zip))
+ Preempt-RT real time kernel ([4.19.y-rt](https://github.com/raspberrypi/linux/tree/rpi-4.19.y-rt))


### BUILD:

#### [Raspberry Pi]

+ Download the pre-built kernel

      ~$ cd /tmp
      /tmp$ wget -O RTkernel_W5500.tgz https://github.com/shkwon98/RPi4_PreemptRT_W5500/blob/main/RTkernel_W5500.tgz?raw=true

+ Installing the Kernel

      /tmp$ tar xzf RTkernel_W5500.tgz
      /tmp$ cd boot
      /tmp/boot$ sudo cp -rd * /boot/
      /tmp/boot$ cd ../lib
      /tmp/lib$ sudo cp -rd * /lib/
      /tmp/lib$ cd ../overlays
      /tmp/overlays$ sudo cp -d * /boot/overlays
      /tmp/overlays$ cd ..
      /tmp$ sudo cp -d bcm* /boot/

+ Boot configutarion

      /tmp$ sudo nano /boot/config.txt
      Type "kernel=kernel7l.img" in the first line
      (Option) Type "dtoverlay=w5500  in the last line

+ Reboot and check the patched kernel

      /tmp$ sudo reboot
      ~$ uname -r


### BENCHMARK:
+ [Cyclictest benchmark](https://github.com/shkwon98/Cyclictest)

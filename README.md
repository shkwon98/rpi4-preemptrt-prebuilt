# RPi4_PreemptRT_W5500
Installing Prebuilt RT kernel supporting SPI with W5500 on Raspberry Pi 4

    ~ $ cd /tmp
    /tmp $ wget -O RTkernel_W5500.tgz https://github.com/shkwon98/RPi4_PreemptRT_W5500/blob/main/RTkernel_W5500.tgz?raw=true
    /tmp $ tar xzf RTkernel_W5500.tgz
    /tmp $ cd boot
    /tmp/boot $ sudo cp –rd * /boot/ 
    /tmp/boot $ cd ../lib 
    /tmp/lib $ sudo cp –rd * /lib/ 
    /tmp/lib $ cd ../overlays 
    /tmp/overlays $ sudo cp -d * /boot/overlays 
    /tmp/overlays $ cd .. 
    /tmp $ sudo cp -d bcm* /boot/
    /tmp $ sudo nano /boot/config.txt
    
*Type at the top of the file:*

    kernel=kernel7l.img

*Reboot*

    /tmp $ sudo reboot
    
*Check the kernel version*

    ~ $ uname -r

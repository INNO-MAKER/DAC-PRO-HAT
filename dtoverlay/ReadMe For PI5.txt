Quick Start For Raspberry PI5

1,Download files from github:

sudo git clone https://github.com/INNO-MAKER/DAC-PRO-HAT.git

2,Copy dtb files

$cd DAC-PRO-HAT/dtoverlay
$sudo chmod -R a+rwx *
$sudo cp inno-dac-pro.dtbo /boot/overlays

3,Modify config.txt

$sudo nano /boot/config.txt

add below content to last line, then save files and reboot.

dtoverlay=inno-dac-pro

4,Set DAC PRO As default Sound card

$alsamixer

4.1，Press F6 to list all sound card,choose Allo Katana

nano /etc/asound.conf  

4.2，Set soud card as default, for example card 1 is Allo Katana

defaults.ctl.card 1
defaults.pcm.card 1
defaults.timer.card 1
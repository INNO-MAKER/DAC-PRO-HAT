## DAC Pro Quick Start:

If you are very familiar with Raspberry Pi and audio hat setting. You could follow below quick start steps，otherwise read the user manual firstly.



### 1.System Image Download link

[rAudio Image  download](https://github.com/rern/rAudio/releases)

[Volumio image download](http://volumio.org/get-started/)

[MoOde image download](http://www.moodeaudio.org/)

[Raspbian and Raspbian image download](https://www.raspberrypi.com/software/operating-systems/)

[LibreELEC image download](https://libreelec.tv/downloads/raspberry/)

[Max2Play image download](https://www.max2play.com/en/max2play-image/)

[OSMC image download](https://osmc.tv/download/)

### 2.rAudio Setup

Setting→System→GPIO Devices→Audio-I2S→**Allo Katana DAC**→reboot.

### 3.Volumio Setup

Audio Output→I2S DAC→ **On**→DAC Model→**Allo Katana DAC** or **Innomaker Dac Pro**→reboot

### 4.MoOde Setup

Configure→Audio→Output device → **I2S audio device**

Configure→Audio→Named I2S device→**Allo Katana DAC**

### 5.Raspbian and Raspbian Lite Setup

1.Open  the config.txt on terminal viia nano tools.

```
sudo nano /boot/config.txt
```

2.Append the following lines to the end of the files.

```
`dtoverlay=allo-katana-dac-audio`
```

3.Pressing CTRL+ x to exit and pressing  ‘y’  to save your changes. Finally, reboot.

```
sudo reboot
```

4.Check the DAC module named 'Allo_Katana' with serial number 3 is available. 

```
aplay -l 
```

or

```
cat /proc/asound/cards
```

5.On Raspbian desktop, Right click on desktop volume icon  set the raspberry pi audio output as ‘Allo Katana'

6.On Raspbian lite, you could follow as step to change the default audio output.

Create /etc/asound.conf 

```
sudo nano /etc/asound.conf
```

Type in the following content , pressing "CTRL+x" and then pressing "y" to save  your changes. Finally, reboot again.Note that the numebr **3** is the DAC module device number on the system.

```
pcml.!default {
  type hw card 3
}

clt.!default{
 type hw card 3
}
```

7.Type in the commands that are shown below, you can see the alsamixer tool.

```
alsamixer
```

### 6.LibreELEC Setup                            

1.Modify the config.txt on LibreELEC image card.Append the following lines to the end of the file.

```
dtoverlay=allo-katana-dac-audio
```

2.Settings→System→Audio→Audio output device→**Allo Katana**→reboot.



### 7.Pops and Crackles Soluations

Some customers said that there are some pops and crackles when play music over our dac module, but no problem over with HDMI of Raspberry Pi. Please try below solutions.

**1.Power supply**

Change a better 5V power supply. The inferior power supply will limits you to pursue the better  audio quality. The battery pack linear power supply is a better choice. 

**2.Hotspot**

Some music system open the Raspberry Pi build-in hotspot default. But the 3.5 mm jacks will be an antenna and received the interference signal from the WIFI module. So use wired network instead of the Raspberry Pi build-in WIFI can help you cut noise pollution completely. Esp the build-in WIFI be used as wireless hotspot.

### 8.Support For Raspberry Pi5

It works fine on Pi5 currently, just follow the operation steps for each system as outlined above. However, there were issues in certain kernel versions (2-3 versions) shortly after the release of Pi5. If you absolutely need to use these intermediate versions, please follow the steps below：

1. Download the matched dtbo file for your system from our GitHub link

2. Use a card reader on your computer to open the TF card that has already been flashed with the system.

3. Copy and replace the corresponding dtbo file in the **overlays** folder within the **boot** drive.

4. Save and exit the TF card, then follow the above setup steps to configure the audio output driver for normal use.
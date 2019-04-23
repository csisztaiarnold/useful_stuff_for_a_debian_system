# Some useful stuff for a Debian 9 + Cinnamon system

## Add your user to sudoers

```
su
nano /etc/sudoers
```
Add `ALL=(ALL:ALL) ALL` to your user.

## Install CURL

```
sudo apt-get install curl
```

## Install dirmngr (network certificate management service)

```
sudo apt-get install dirmngr
```

## Add additional source lists

/etc/apt/sources.list

Add `contrib` and `non-free`

```
deb http://ftp.debian.org/debian stretch-backports main
deb http://ppa.launchpad.net/atareao/telegram/ubuntu xenial main
deb-src http://ppa.launchpad.net/atareao/telegram/ubuntu xenial main
deb http://ppa.launchpad.net/no1wantdthisname/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/no1wantdthisname/ppa/ubuntu trusty main
```

## Get the public keys in case they're missing after `sudo apt-get update`

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY
sudo apt-get update
```

## Mount a HD on boot

Edit `/etc/fstab`

```
/dev/sdb2	/media/username/data	ext4	defaults	0	1
```

## GUI/Cinnamon stuff 

Theme: __Adapta Nokto Eta__  
Icons: __[Paper](https://snwh.org/paper)__  
Fonts: __[Hack](https://github.com/source-foundry/Hack), [Roboto](https://fonts.google.com/specimen/Roboto), [Open Sans](https://fonts.google.com/specimen/Open+Sans), [Cantarrel](https://fonts.google.com/specimen/Cantarell), [Inter UI]( https://rsms.me/inter/)__ (copy to `~/.fonts`)  
Window borders: __[Afflatus](https://www.gnome-look.org/p/1191004/)__  (copy to `~/.themes`)  
Extension: __Custom Shadows__   

MS fonts:
```
sudo apt-get install ttf-mscorefonts-installer
```

## Essential software

Note: make sure that if you add new items into "Startup applications", you set them at least 10-15s delay, as some applications won't start before the Cinnamon GUI and some of its deamons are fully loaded.

#### Midnight Commander (visual file manager)

```
sudo apt-get install mc
```

#### Tilix (tiling terminal emulator)

https://gnunn1.github.io/tilix-web/


#### Fancontrol (fan speed control)

https://askubuntu.com/questions/22108/how-to-control-fan-speed

My settings in `/etc/fancontrol` (could vary from system to system): 
```
MINTEMP=hwmon3/device/pwm2=20 hwmon1/device/pwm1=30
MAXTEMP=hwmon3/device/pwm2=70 hwmon1/device/pwm1=70
MINSTART=hwmon3/device/pwm2=150 hwmon1/device/pwm1=50
MINSTOP=hwmon3/device/pwm2=100 hwmon1/device/pwm1=40
```

#### Telegram (messenger)

```
sudo apt-get install telegram-desktop
```

#### Imwheel (improved mouse-wheel control)

```
sudo apt-get install imwheel
```
Edit the config:
```
sudo nano ~/.imwheelrc
```
Paste this into the text file:
```
".*"
None,      Up,   Button4, 3
None,      Down, Button5, 3
Control_L, Up,   Control_L|Button4
Control_L, Down, Control_L|Button5
Shift_L,   Up,   Shift_L|Button4
Shift_L,   Down, Shift_L|Button5
```
Start `imwheel`:
```
imwheel --kill --buttons "4 5"
```
Don't forget to add it to the Startup Applications!

#### Infinality (improved font rendering)

https://www.linuxbabe.com/desktop-linux/improve-font-rendering-on-debian-8-by-install-infinality-and-google-fonts

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E985B27B
sudo apt-get update
sudo apt-get install fontconfig-infinality
```

## Non-essential, but useful software

#### Node.js and npm

https://linuxize.com/post/how-to-install-node-js-on-debian-9/

#### WoeUSB (create your own usb stick Windows installer)

http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/w/woeusb/

#### Flameshot (powerful yet simple to use screenshot software)

```
sudo apt-get install flameshot
```

#### htop (interactive system-monitor)
```
sudo apt-get install htop
```

#### GParted (disk partitioning)

```
sudo apt-get install gparted
```

#### Kazam (screencasting program)

```
sudo apt-get install kazam
```

#### VLC (media player)

```
sudo apt-get install vlc
```

#### OpenShot (video editor)

```
https://www.openshot.org/
```

#### Deluge (bittorrent client)

```
sudo apt-get install deluge
```
To set Deluge the default software for opening magnet links:

```
gvfs-mime --set x-scheme-handler/magnet deluge.desktop
xdg-mime default deluge.desktop x-scheme-handler/magnet
```

#### VICE (Commodore emulator)

```
sudo apt-get install vice
```
Since the Debian distribution doesn't contains any ROMs, just download the Windows version from http://vice-emu.sourceforge.net/ and unpack the desired machine folder to ~/.vice

#### Insomnia (REST client)

https://support.insomnia.rest/article/23-installation#ubuntu

#### Kdenlive (non-linear video editor)

https://kdenlive.org/en/
```
sudo apt-get install kdenlive
```

#### Wine32

```
echo -e "deb http://http.kali.org/kali sana main non-free contrib\ndeb http://security.kali.org/kali-security/ sana/updates main contrib non-free" > /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wine32
```

## Small hacks

#### Fix the green antialias in Gimp

Uninstall Gimp (just kidding).

```
sudo gedit /etc/gimp/2.0/fonts.conf
```
```
<fontconfig>
 <match target="font">
  <edit name="rgba" mode="assign">
   <const>none</const>
  </edit>
 </match>
</fontconfig>
```

## LEMP/LAMP

...todo

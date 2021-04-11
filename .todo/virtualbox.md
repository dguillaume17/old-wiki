https://www.unixfu.ch/using-apple-mac-keyboard-with-ubuntu/

/etc/default/keyboard

XKBMODEL="macintosh"
XKBLAYOUT="ch"
XKBVARIANT="de_mac"
XKBOPTIONS="lv3:alt_switch"

BACKSPACE="guess"


https://linuxize.com/post/how-to-install-virtualbox-guest-additions-in-ubuntu/


sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo sh ./VBoxLinuxAdditions.run --nox11
lsmod | grep vboxguest



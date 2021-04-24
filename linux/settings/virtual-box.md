# VirtualBox

## Configurer VirtualBox pour Ubuntu Desktop

1.

    /Applications/VirtualBox.app/Contents/Resources
    Clique droit sur le fichier VirtualBoxVM.app et ouvrir "Get Info"
    Cocher "Open in Low Resolution"

2. Dans les Settings de VirtualBox

    Onglet System > Motherboard
        "Base Memory" = 8Go

    Onglet System > Processor
        "Processor(s)" = 4
        "Execution Cap" = Max (100%)

    Onglet Display
        "Video Memory" = Max (128MB)
        "Scale Factor" = Min (100%)
        "Graphics Controller" = VBoxSVGA
        Décocher "Enable 3D Acceleration"

    Onglet Audio

## Configurer le clavier

### Ubuntu Desktop

Source de saisie : Français (France)
Variante : Français (Macintosh)

### Ubuntu Server

1. Installer le paquet "keyboard-configuration" et le configurer

    ```bash
    sudo apt-get install keyboard-configuration
    sudo dpkg-reconfigure keyboard-configuration
    ```

2. Insérer la configuration

    * "Keyboard model" = "Macintosh"
    * "Country of origin for the keyboard" = "French"
    * "Keyboard layout" = "French - French (Macintosh)"
    * "Key to function as AltGr" = "The default"
    * "Compose key" : "No compose key"

3. Redémarrer

    ```bash
    sudo shutdown -r now
    ```

## Installer les "Guest Additions"

1. Installer les paquets requis pour builder des modules externes du kernel

    ```bash
    sudo apt update
    sudo apt install build-essential dkms linux-headers-$(uname -r)
    ```

2. Insérer le CD dans VirtualBox via le menu “Devices > Insert Guest Additions CD Image” et le monter dans Ubuntu

    ```bash
    sudo mkdir -p /mnt/cdrom
    sudo mount /dev/cdrom /mnt/cdrom
    cd /mnt/cdrom
    sudo sh ./VBoxLinuxAdditions.run --nox11
    ```

3. Redémarrer

    ```bash
    sudo shutdown -r now
    ```

4. Vérifier l'installation

    ```bash
    lsmod | grep vboxguest
    > vboxguest     303104  2   vboxsf
    ```

## Benchmark

### 1

sudo apt install mesa-utils

```bash
glxgears
> 300 frames in 5.0 seconds = 59.998 FPS
> 300 frames in 5.0 seconds = 59.788 FPS
> ...
```


### 2


wget http://phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_7.8.0_all.deb

sudo apt install gdebi-core


sudo gdebi phoronix-test-suite_7.8.0_all.deb

phoronix-test-suite --version


### 3

sudo apt install sysbench
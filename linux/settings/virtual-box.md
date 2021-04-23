# VirtualBox

## Keyboard

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

Empêcher la mise en veille à la fermeture de l'écran

* Activer

```bash
sudo pmset -a disablesleep 1
```

* Désactiver

```bash
sudo pmset -a disablesleep 0
```



Trier le launchpad par ordre alphabétique

```bash
defaults write com.apple.dock ResetLaunchPad -bool true; killall Dock
```
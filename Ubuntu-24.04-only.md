## 🔥🔥🔥 Purge Unnecessary Packages Without Losing ubuntu-desktop

**Steps:**

1. Remove snaps (commands or scripts)
2. Purge unwanted apps
3. Install apps of your choice
4. Run cleanup scripts or use BleachBit

### Purge Snaps (Step by Step Commands)

```bash
sudo snap list
systemctl stop snapd
systemctl disable snapd
# Remove individual snaps
sudo snap remove --purge firefox firmware-updater
sudo snap remove --purge gnome-42-2204 gtk-common-themes
sudo snap remove --purge snap-store snapd-desktop-integration bare
sudo snap remove --purge core22
sudo snap remove --purge snapd

# Clean up snap directories
sudo rm -Rf /var/cache/snapd/
rm -Rf ~/snap
sudo apt autoremove --purge
```

### Purge Accessibility & Internationalization Packages (390+47 MB freed)

```bash
# remove ubuntu-report & appcrash popup
sudo apt purge ubuntu-report apport apport-gtk
# Accessibility (117MB)
sudo apt purge brltty orca gnome-accessibility-themes fonts-noto-cjk eog
# blob errors, ignore
sudo apt purge speech-dispatcher* libpinyin* ibus* pocketsphinx* espeak* liblouis* hplip*
sudo apt autoremove --purge
```

### Remove Printing Support (18+5 MB freed)

```bash
sudo apt purge 'cups*' 'foomatic*' printer-driver-brlaser* printer-driver-foo2zjs-common* printer-driver-ptouch* printer-driver-c2esp* printer-driver-min12xxw* printer-driver-sag-gdi*
sudo apt autoremove --purge
```

### Remove Old Kernels

First, identify installed kernels: Then remove specific versions:

```bash
dpkg --list | grep -Ei 'linux-image|linux-headers|linux-tools|linux-modules|linux-hwe'

dpkg --list | grep -i linux-image
dpkg --list | grep -i linux-headers
dpkg --list | grep -i linux-tools
dpkg --list | grep -i linux-modules
dpkg --list | grep -i linux-hwe
sudo dpkg --purge package1 package2 package3 ...
sudo apt purge package1 package2 package3 ...
sudo apt autopurge
sudo update-grub
```

## ✴️✴️✴️ Suggested / Optional Packages

### Essential Tools

```bash
# must have programs
sudo nala install curl git gh gnome-shell-extension-manager gnome-tweaks loupe transmission foliate lsd nautilus-admin gedit gedit-plugins
# systemd-zram-generator tree nemo
# thunar file browser
sudo nala install thunar thunar-media-tags-plugin
# multimedia programs
sudo nala install totem amberol gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```

### Optional Programs

```bash
sudo nala install ptyxis vlc file-roller rar unrar synaptic gnome-decoder adb fastboot gnome-calendar
```

# 🆕🆒🆓 Clean & Minimal Ubuntu (24.04 LTS)

When installing Ubuntu, choose **DEFAULT SELECTION** (Just the essentials, web browser and basic utilities). All of the below removal and installation is to make Ubuntu more suitable for development.

### The most common and reliable way to check your Ubuntu version using the command line

```bash
lsb_release -a
```

### Displays system hostname and key system information, including the Operating System version

```bash
hostnamectl
```

---

## ⭐⭐⭐ First: Update & Upgrade

```bash
sudo apt update
sudo apt install nala
sudo nala full-upgrade

sudo apt update -y && sudo apt upgrade -y
apt search <keyword>
sudo apt --fix-broken install
sudo apt autoremove --purge
sudo apt autopurge
```

### Configure Nala

Edit `/etc/nala/nala.conf`:

```bash
# Set to true to make full-upgrade the default
full_upgrade = true

# Set to true: Nala will list the upgradable packages automatically after `update`
update_show_packages = true

# Set to true for `MiB` false for `MB`
filesize_binary = true
```

---

## 🔥🔥🔥 Purge Unnecessary Packages Without Losing ubuntu-desktop

**Steps:**

1. Remove snaps (commands or scripts)
2. Purge unwanted apps
3. Install apps of your choice
4. Run cleanup scripts or use BleachBit

### Purge Snaps (Step by Step)

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
sudo apt purge
sudo apt autopurge
sudo update-grub
```

---

## ✴️✴️✴️ Suggested / Optional Packages

### Essential Development Tools

```bash
sudo nala install curl git gh gnome-shell-extension-manager gnome-tweaks loupe transmission tree foliate systemd-zram-generator lsd
sudo nala install nautilus-admin gedit gedit-plugins
sudo nala install thunar thunar-media-tags-plugin
sudo nala install totem amberol gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```

### Optional Utilities

```bash
sudo nala install ptyxis vlc file-roller rar unrar synaptic gnome-decoder adb fastboot gnome-calendar
```

---

## 🌐🌐🌐 Install Latest Google Chrome

```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

---

## 🎴🎴🎴 Install Node.js

### Node.js 22.x LTS

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo bash -
sudo apt install -y nodejs
```

### Node.js 24.x LTS

```bash
curl -fsSL https://deb.nodesource.com/setup_24.x | sudo bash -
sudo apt install -y nodejs
```

### Global NPM Packages

```bash
sudo npm install -g npm@latest corepack@latest npm-check-updates typescript pnpm@latest yarn vite
sudo npm outdated -g --depth=0
sudo npm update -g
```

---

## 🆘🆘🆘 oh-my-posh Setup

### Installation

```bash
sudo bash -c "$(curl -s https://ohmyposh.dev/install.sh)" -- -d /usr/bin

# Move themes directory
sudo mv /root/.cache/oh-my-posh/themes/ ~/.oh-my-posh
sudo chmod 777 .oh-my-posh/
```

### Configure Bash

You can use the enclosed .bashrc for the selection of themes, just uncomment the required theme. Refresh bash after selecting theme:

```bash
exec bash
```

---

## 🛸💽🚚 XTRADEB Packages

Unofficial Ubuntu application packages maintained by xtradeb. in ungoogled-chromium extensions can not be installed, so i prefer mostly chromium.

[xtradeb PPA](https://launchpad.net/~xtradeb/+archive/ubuntu/apps)

```bash
sudo add-apt-repository ppa:xtradeb/apps -y
sudo nala update
sudo nala install yt-dlp parabolic calibre ungoogled-chromium chromium gnucash intellij-idea-community pycharm-community
```
---

## 📦📦📦 Git & SSH Setup

This setup is adviseable if you have only single git account, for multiples git accounts, a complex setup is required.

### Git Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global color.ui auto
```

### SSH Setup

#### ✅ 1. Check for Existing SSH Keys

```bash
ls -al ~/.ssh
```

If keys exist, proceed to steps 3 & 6.

#### ✅ 2. Generate a New SSH Key (if none exist)

```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```

#### ✅ 3. Add SSH Key to SSH Agent

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

#### ✅ 4. Copy the Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

#### Fix Permissions (if needed)

```bash
chmod 600 ~/.ssh/id_ed25519
```

#### ✅ 5. Add SSH Key to GitHub

Add the public key from step 4 to your GitHub account settings.

#### ✅ 6. Test the GitHub Connection

```bash
rm ~/.ssh/known_hosts
ssh-keyscan github.com >> ~/.ssh/known_hosts
ssh -T git@github.com
```

---

## 🪛📜💻 Important Scripts

### All-in-One Tool

**[ubuntu-debullshit.sh](https://github.com/polkaulfield/ubuntu-debullshit)**
Purges snaps, installs flatpaks, and restores vanilla GNOME.

### Snap Uninstallers / Removers

**[snap-remover.sh](https://gist.github.com/lassekongo83/808b19e034c05d10ac4e3cc259808e4e)**
Completely remove snaps from Ubuntu.

**[unsnap](https://github.com/popey/unsnap)**
Quickly migrate from snap packages to flatpaks.

### Cleaners

**[snap-cleaner.sh](https://github.com/sakibulalikhan/snap-cleaner)**
Free up disk space by deleting unnecessary Snap package revisions and caches.

**[ubuntu_cleanup.sh](https://gist.github.com/Limbicnation/6763b69ab6a406790f3b7d4b56a2f6e8)**
A comprehensive system cleanup script that safely removes unnecessary files to free up disk space.

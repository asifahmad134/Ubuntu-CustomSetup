## Zen Browser installation

```bash
tar -xf zen.linux-x86_64.tar.xz
sudo mv zen /opt/zen-browser
sudo chown -R root:root /opt/zen-browser
sudo ln -s /opt/zen-browser/zen /usr/local/bin/zen
sudo nano /usr/share/applications/zen.desktop
```

### zen.desktop

```bash
[Desktop Entry]
Name=Zen Browser
Comment=Experience the web with Zen
Exec=/opt/zen-browser/zen
Icon=/opt/zen-browser/browser/chrome/icons/default/default128.png
Terminal=false
Type=Application
Categories=Network;WebBrowser;
```

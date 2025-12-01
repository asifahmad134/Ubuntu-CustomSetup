# ⚛️⚛️⚛️ Remove Language Locales (50+ MB per app)

Remove unused locales from Chrome & Electron-based apps:

### VS Code

```bash
sudo rm /usr/share/code/resources/app/ThirdPartyNotices.txt /usr/share/code/LICENSES.chromium.html /usr/share/code/resources/app/LICENSE.rtf
sudo rm /usr/share/code/locales/!("en-GB.pak"|"en-US.pak")
sudo rm -fdr /usr/share/code/resources/app/licenses
```

### FreeTube

```bash
sudo rm /opt/FreeTube/locales/!("en-GB.pak"|"en-US.pak")
sudo rm /opt/FreeTube/LICENSES.chromium.html /opt/FreeTube/LICENSE.electron.txt
```

### Google Chrome

```bash
sudo rm /opt/google/chrome/locales/!("en-GB.pak"|"en-US.pak")
```

### Brave Browser

```bash
sudo rm /opt/brave.com/brave/locales/!("en-GB.pak"|"en-US.pak")
```

### Google antigravity

```bash
sudo rm /usr/share/antigravity/locales/!("en-GB.pak"|"en-US.pak")
sudo rm /usr/share/antigravity/resources/app/ThirdPartyNotices.txt /usr/share/antigravity/LICENSES.chromium.html /usr/share/antigravity/resources/app/LICENSE.txt
```

### Cursor

```bash
sudo rm /usr/share/cursor/locales/!("en-GB.pak"|"en-US.pak")
sudo rm /usr/share/cursor/resources/app/ThirdPartyNotices.txt /usr/share/cursor/LICENSES.chromium.html /usr/share/cursor/resources/app/LICENSE.txt
```

### Slack

```bash
sudo rm /usr/lib/slack/locales/!("en-GB.pak"|"en-US.pak")
sudo rm /usr/lib/slack/LICENSE /usr/lib/slack/resources/LICENSES.chromium.html
```

### TickTick

```bash
sudo rm /opt/TickTick/locales/!("en-GB.pak"|"en-US.pak")
sudo rm /opt/TickTick/LICENSE.electron.txt /opt/TickTick/LICENSES.chromium.html
```

### Replit

```bash
sudo rm /usr/lib/replit/locales/!("en-GB.pak"|"en-US.pak")
sudo rm /usr/lib/replit/LICENSES.chromium.html
```

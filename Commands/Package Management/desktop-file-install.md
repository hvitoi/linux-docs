# Manually installing apps

- Manually installed apps are usually saved in
  - `/usr/local/bin`
  - `/opt`

## Pin app to start menu

- `/usr/share/applications`: global
- `~/.local/share/applications/`: user

```sh
# Install to /usr/share/applications
sudo desktop-file-install `app.desktop`
sudo desktop-file-install jetbrains-idea.desktop
sudo desktop-file-install Postman.desktop
```

- Example: `~/.local/share/applications/Postman.desktop`

```conf
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=/opt/Postman/app/Postman %U
Icon=/opt/Postman/app/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
```

- Example: `~/.local/share/applications/jetbrains-idea.desktop`

```conf
[Desktop Entry]
Version=1.0
Type=Application
Name=IntelliJ IDEA Ultimate Edition
Icon=/opt/idea/bin/idea.svg
Exec="/opt/idea/bin/idea.sh" %f
Comment=Capable and Ergonomic IDE for JVM
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-idea
```

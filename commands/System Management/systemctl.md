# systemctl

- `systemctl` is the interaction with `systemd`
- New version of the legacy `service` command

## Units

- Units can be `services` (.service), `mount points` (.mount), `devices` (.device) or `sockets` (.socket)
- `/usr/lib/systemd/system/`: units provided by installed packages
- `/etc/systemd/system/`: units installed by the system administrator

```bash
# Analyzing the system state
systemctl status
systemctl status "unit.service" # status of a specific unit

# Checking the unit status
systemctl
systemctl list-units # same output
systemctl --failed # failed units

# Starting, restarting, reloading a unit
systemctl start "unit"
systemctl stop "unit"
systemctl restart "unit"
sudo systemctl daemon-reload # reload all

#Enabling a unit
systemctl enable "unit"
systemctl disable "unit"

## List all
systemctl -a

## List all services
systemctl --type=service
```

## Service files

- `/etc/systemd/system/`

```shell
#Add new service
sudo vim /etc/systemd/system/tomcat.service
```

- Example .service file

```conf
[Unit]
Description=Apache Tomcat Web Application Container
After=network.target

[Service]
Type=forking

Environment=JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64
Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
Environment=CATALINA_HOME=/opt/tomcat
Environment=CATALINA_BASE=/opt/tomcat
Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'
Environment='JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom'

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

User=tomcat
Group=tomcat
UMask=0007
RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target
```

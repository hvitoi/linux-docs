# systemctl

- Manage processes
- New version of the legacy `service` command

```bash
systemctl status `service`
systemctl start `service`
systemctl restart `service`
systemctl stop `service`
systemctl enable `service` # Enable run the service upon startup
sudo systemctl daemon-reload

## List all
systemctl -a

## List all services
systemctl --type=service
```

## Service files

- `/etc/systemd/system/`

```sh
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

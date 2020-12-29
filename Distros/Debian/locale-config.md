# Language configuration

## Add new system languages and formats

```bash
sudo nano /etc/locale.gen
sudo locale-gen
```

## Add asian characters compatibility

```bash
sudo apt install fonts-arphic-ukai fonts-arphic-uming # Chinese
sudo apt install fonts-ipafont-mincho fonts-ipafont-gothic # Japanese
sudo apt install fonts-unfonts-core # Korean
```

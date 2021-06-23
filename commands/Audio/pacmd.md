# pacmd

- PulseAudio command

```shell

# Load module
pacmd load-module module-alsa-source device=hw:Loopback,1,0

# Switch between HSP/HFP to A2DP
pacmd set-card-profile `card-name` a2dp_sink
pacmd set-card-profile bluez_card.5C_FB_7C_88_FA_49 a2dp_sink

```

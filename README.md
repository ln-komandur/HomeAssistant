# HomeAssistant

## Installation
[Install HA OS on an SSD on an Intel PC](https://www.home-assistant.io/installation/generic-x86-64/)

## Connect to Wifi from command line

## Tailscale

Works well for remote access. Do not configure as exit node

## SSH
For remote access and server shutdown down if needed. Follow [this guide](https://lazyadmin.nl/smart-home/enable-ssh-home-assistant/)

## Configure BIOS to restart in case of power outage

## Device specific

### Reolink cameras

#### Settings to record with lookback

Go to "Security", open the camera and click on "Settings" <img width="60" height="65" alt="image" src="https://github.com/user-attachments/assets/ec51b31c-742e-4591-b078-13fca1c6c619" />

Turn on "Pre load camera stream"
<img width="1254" height="99" alt="image" src="https://github.com/user-attachments/assets/db240540-720a-445e-9d30-feb863f56bca" />

#### Upon AI detection of person / vehicle, take a snap as well as record video

Use Parallel task blocks
Use Continue on error

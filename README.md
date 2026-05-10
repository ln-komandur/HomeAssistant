# HomeAssistant

## Installation
[Install HA OS on an SSD on an Intel PC](https://www.home-assistant.io/installation/generic-x86-64/)

## Connect to Wifi after installation

`login`

`nmcli radio` *# Show the current status of all radio devices*

`nmcli device wifi` *# Show all SSIDs in range*

`nmcli device wifi connect <SSID> --ask` *# Connect to the given SSID by prompting for its password*

`nmcli connection show` *# Show all configured connections and devices in the last column*

`ip addr show | more ` *# Show the ip address in the networks connected to*

`nmcli device disconnect <device>` *# Disconnect the device*

`nmcli connection delete <SSID>` *# Delete the SSID from any automatic connections / history*

## Tailscale

Works well for remote access. Do not configure as exit node

## SSH
For remote access and server shutdown down if needed. Follow [this guide](https://lazyadmin.nl/smart-home/enable-ssh-home-assistant/)

## Configure BIOS to restart in case of power outage

## Device specific

### Reolink cameras

#### Settings to record with lookback

Go to "Security", open the camera and click on "Settings" <img width="60" height="65" alt="Camera Settings" src="https://github.com/user-attachments/assets/ec51b31c-742e-4591-b078-13fca1c6c619" />

Turn on "Preload camera stream"
<img width="1254" height="99" alt="Preload camera stream" src="https://github.com/user-attachments/assets/db240540-720a-445e-9d30-feb863f56bca" />

#### Upon AI detection of person / vehicle, take a snapshot as well as record the video feed on HA Media

Use **Parallel task blocks** to take a snapshot of the camera and then record the video feed with a lookback

Use **Continue on error** to take a snapshot of the camera (the first task in the block)

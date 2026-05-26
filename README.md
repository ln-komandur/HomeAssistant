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

There are several options enabled by default in the **Settings** -> **Apps** -> **Tailscale** under the **Configuration** tab at the top. Not all of them are needed to be enabled

### Subnet routes

#### Option 1: Need not Accept Subnet routes - can be turned off

Reolink cameras will still work without subnet routes (guess they go through Reolink's clour servers then. Though live feeds work, unsure about automations and latencies)

1.  Open the Home Assistant Dashboard.
1.  Go to **Settings** -> **Apps** -> **Tailscale** and click on the **Configuration** tab at the top
1.  Under the **Options** section and check **Accept routes** BUT REMOVE **local_subnets**

#### Option 2: Accept Subnet routes IPv4 and IPv6

This option may be preferred as it might be avoiding Reolink's cloud servers for automations

1.  Open the Home Assistant Dashboard
1.  Go to **Settings** -> **Apps** -> **Tailscale** and click on the **Configuration** tab at the top
1.  Under the **Options** section and check **Accept routes** AND KEEP **local_subnets**
1.  Go to **Settings** -> **System** -> **Network**
1.  Look under the IPv4 section and under the IPv6 section for the IP addresses 
1.  Match these with the **Tailscale Admin Console** for the homeassistant machine under **Edit route settings**
1.  Login to your **router**, and match these with the **Active IP leases** (for IPv4 as well as IPv6)


### Turn off Exit node or Connector

1.  Open the Home Assistant Dashboard.
1.  Go to **Settings** -> **Apps** -> **Tailscale** and click on the **Configuration** tab at the top
1.  Under the **Options** section and uncheck **Advertise as an exit node** as well as **Advertise as an app connector**

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

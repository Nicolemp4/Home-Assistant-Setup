# Home-Assistant-Setup

## Introduction
Before getting into any AI stuff, I needed a Home Assistant enviroment to connect it to. I had decided to run Home Assistant in a container on my linux machine using Docker Compose. This would later prove to be a mistake, but we will cover that later.
## Installing the necessary files
First, I had to install docker compose on my Linux box. I pasted the following commands into the terminal as I was using Linux Mint, which allows for CLI and GUI operations.

```yaml
sudo apt-get update
sudo apt-get install docker-compose-plugin
```

## Setting up the Container
Once Docker Compose had installed and been set up it was time to set up Home Assistant within a container. I created a **compose.yaml** file with the followng code:


```yaml
services:
  homeassistant:
    container_name: homeassistant
    image: "ghcr.io/home-assistant/home-assistant:stable"
    volumes:
      - /PATH_TO_YOUR_CONFIG:/config
      - /etc/localtime:/etc/localtime:ro
      - /run/dbus:/run/dbus:ro
    restart: unless-stopped
    privileged: true
    network_mode: host
```

## Configuring Home Assistant

# Jellyfin Docker Setup

This repository provides a Docker Compose configuration to deploy a **Jellyfin** media server. Jellyfin is an open-source alternative to media servers like Plex.

## Configuration

### Prerequisites
- Docker installed on your system
- Docker Compose installed
- Access to a Linux machine with a dedicated user (`your_user` in the example)

### `docker-compose.yml` Overview

The file includes:
- A **Jellyfin** container using the official image `jellyfin/jellyfin:latest`.
- Volume mappings to persist configuration and cache data.
- An optional setup for hardware acceleration in video transcoding.

### Volumes
- `/config`: Stores Jellyfin configuration files.
- `/cache`: Used for performance optimization caching.
- `/media`: Directory containing your media files.

### docker instructions
cd your_repository_of_docker-compose_yml
docker-compose up -d

### access on web
http://IP_ADDRESS:8096

## Customization
Enabling Hardware Acceleration
If your machine supports hardware acceleration, ensure the video device (e.g., /dev/video19) is accessible.
Add additional devices as needed:
devices:
  - /dev/videoX:/dev/videoX

## Raspberry pi tricks (but don't do this for the Raspberry pi 5 !)
sudo nano /boot/firmware/config.txt

add at the end of the file this line : gpu_mem=320

save the file before exit and do a sudo reboot 

and don't forget to choose material acceleration inside the jellyfish web ui.
For raspberry pi, it should be : V4L2
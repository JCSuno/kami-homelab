# Self-Hosted Container Infrastructure & Media Pipeline

A containerized home server architecture deployed on Ubuntu Linux using Docker Compose and DockSTARTer 2. 

This repository documents the infrastructure layout, environment isolation, network strategy, and GPU hardware acceleration configurations.

## Architecture Highlights

* **Hardware Acceleration:** Passed host Nvidia GPU (RTX series) into Plex using `nvidia-container-toolkit` for NVENC/NVDEC hardware transcoding.
* **Network & VPN Isolation:** Routed specific traffic through ProtonVPN containers while keeping local media services on host/bridge networks.
* **Storage Tiering:** Separated high-write SSD target paths (torrent scratch space) from long-term storage pools to maximize drive longevity and atomic file moves.
* **Security & Secret Management:** Stripped all runtime secrets, passwords, and API keys into local `.env` files protected by `.gitignore` rules.
* **Lifecycle Management:** Configured Watchtower for automated nightly container updates, using container labels to exclude critical game server instances.

## Repository Layout

.
├── docker-compose.override.yml  # Production container overrides & hardware mappings
├── .env.example                 # Sanitized environment variable template
├── .gitignore                   # Secret protection and file tracking exclusions
└── docs/
└── dockstarter2.md          # Full service inventory and path maps


## Stack Summary

| Service Category | Containers |
| :--- | :--- |
| **Media & Analytics** | Plex, Tautulli |
| **Automation / Arr Stack** | Sonarr, Radarr, Lidarr, Bazarr, Prowlarr |
| **Downloaders & Network** | qBittorrent (VPN), Deemix, FlareSolverr |
| **Management & Dashboards** | Portainer, Organizr, Watchtower |
| **Game Hosting** | Minecraft (Fabric) |

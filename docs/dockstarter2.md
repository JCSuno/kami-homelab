# Docker and DockSTARTer Configuration

## Architecture

DockSTARTer maintains base configurations. GPU passthrough, host networking, and storage mounts are defined in `docker-compose.override.yml`.

### System Paths

* **DockSTARTer Root:** `~/.config/dockstarter2/`
* **App Data:** `~/.config/appdata/`
* **Override File:** `~/.config/compose/docker-compose.override.yml`

## Service Overview

| Service | Network Mode | Purpose | Overrides Applied |
| :--- | :--- | :--- | :--- |
| **bazarr** | Bridge | Subtitle downloader | Default |
| **deemix** | Bridge | Music downloader | Custom volume `/downloads` |
| **flaresolverr** | Bridge | Cloudflare bypass proxy | Default |
| **lidarr** | Bridge | Music manager | Default |
| **minecraftserver** | Host | Fabric game server | Watchtower updates disabled |
| **organizr** | Bridge | Dashboard | Default |
| **plex** | Host | Media server | Nvidia GPU passthrough |
| **portainer** | Bridge | Container management | Default |
| **prowlarr** | Bridge | Indexer manager | Default |
| **qbittorrentvpn** | Bridge | Torrent client over VPN | Custom SSD mount |
| **radarr** | Bridge | Movie manager | Default |
| **sonarr** | Bridge | TV manager | Default |
| **tautulli** | Bridge | Plex statistics | Default |
| **watchtower** | Bridge | Automatic container updates | Standard schedule |

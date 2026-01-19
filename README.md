# HelloWorldSMP Minecraft Server

This repository contains the Docker configuration for the HelloWorldSMP Minecraft Forge server. It includes the setup for the Minecraft server itself and a Playit.gg agent for simplified networking.

## Services

### Minecraft Server (mc)
- **Image**: itzg/minecraft-server:java21
- **Type**: FORGE
- **Version**: 1.21.10
- **Java Version**: 21
- **Memory**: 4G
- **Port**: 25565

### Playit Agent (playit)
- **Image**: ghcr.io/playit-cloud/playit-agent:latest
- **Network Mode**: Service bound to 'mc' container
- **Purpose**: Provides public access tunneling without port forwarding

## Prerequisites

- Docker
- Docker Compose

## Installation and Usage

1. Clone this repository.
2. Navigate to the directory.
3. Start the server:
   ```bash
   docker compose up -d
   ```
4. Check logs (optional):
   ```bash
   docker compose logs -f
   ```

## Configuration

The server configuration is managed via environment variables in the `docker-compose.yml` file. Important variables include:
- `EULA`: Must be set to "TRUE" to run the server.
- `VERSION`: Minecraft version.
- `TYPE`: Server type (FORGE).
- `MEMORY`: Heap size for Java.
- `MOTD`: Message of the Day.
- `DIFFICULTY`: Game difficulty.
- `MAX_PLAYERS`: Maximum concurrent players.

## Data Persistence

- World data and server files are stored in the `./data` directory (excluded from version control).
- Playit agent data is stored in `./playit_data` (excluded from version control).

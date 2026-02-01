# Minecraft Server Docker Guide

Here are the common commands you'll need to manage your Minecraft server and Playit tunnel.

**Note:** Run these commands from the `HelloWorldSMP` folder (where your `docker-compose.yml` is located).

## 🚀 Start the Server
Start the server in the background (detached mode):
```powershell
docker compose up -d
```

## 🛑 Stop the Server
Stop and remove the containers (safely saves the world first):
```powershell
docker compose down
```
*Use `docker compose stop` if you just want to pause them without removing the containers.*

## 🔄 Restart
Restart the Minecraft server specifically:
```powershell
docker compose restart mc
```
Restart everything (including the tunnel):
```powershell
docker compose restart
```

## 📜 View Logs
Watch the server console (live logs):
```powershell
docker compose logs -f mc
```
*Press `Ctrl + C` to exit the log view (this won't stop the server).*

To view Playit tunnel logs:
```powershell
docker compose logs -f playit
```

## ⌨️ Server Console Commands
To run Minecraft commands (like `/op`, `/whitelist`, `/gamemode`) without logging into the game, use the RCON client built into the container:

```powershell
docker compose exec mc rcon-cli
```
This will give you a `>` prompt where you can type commands like `op YourName`. Type `exit` to leave.

**Single command example:**
```powershell
docker compose exec mc rcon-cli op JohnLemar
```

## 🛠️ Update Server
To update to the latest version of the server image (and Playit agent):

1. **Pull the latest images:**
   ```powershell
   docker compose pull
   ```
2. **Recreate the containers:**
   ```powershell
   docker compose up -d
   ```

## 💾 Backups
Your world data is stored in the `./data` folder.
To backup, simply copy the `data` folder to a safe location while the server is stopped.

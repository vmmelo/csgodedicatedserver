# About
This is a Counter-Strike : Global Offensive Dedicated Server, using docker compose.

# Requirements
- Docker
- Docker-compose

# Configuration
- Create the ```.env``` file, based on the ```.env.example``` file.
- Put your app token (generated in [Steam dev website](https://steamcommunity.com/dev/managegameservers)), in SRCDS_TOKEN .env variable 
- You may need to portfoward (configured in SRCDS_PORT env) in your router and system.

# Usage
- After the initial setup, you just need to run ```docker-compose up```
- If you're connected in the same network, the server should appear in "Lan" tab, otherwise "Internet" tab.
- You can connect directly using csgo console, running ```connect {public ip} {password}```. 
- You can get the server public ip in [whatismyip](https://www.whatismyip.com/what-is-my-public-ip-address/)

## SRCDS_REGION env variable
| Value | Location        |
|-------|-----------------|
| 0     | US - East       |
| 1     | US - West       |
| 2     | South America   |
| 3     | Europe          |
| 4     | Asia            |
| 5     | Australia       |
| 6     | Middle East     |
| 7     | Africa          |
| 255   | World (default) |

# Alternative
You can ```docker run``` command like this:
docker run --name csgoserver -p 27015:27015 -v /$(pwd)/csgo:/home/steam/csgo-dedicated/csgo/ --publish 27015 --restart always --tty -e "SRCDS_TOKEN={token}" -e "SRCDS_RCONPW=rala" -e "SRCDS_PORT=27015" -e "SRCDS_TV_PORT=27020" -e "SRCDS_FPSMAX=300" -e "SRCDS_TICKRATE=128" -e "SRCDS_MAXPLAYERS=10" -e "SRCDS_STARTMAP=de_dust2" -e "SRCDS_REGION=2" -e "SRCDS_MAPGROUP=mg_active" -d cm2network/csgo:latest

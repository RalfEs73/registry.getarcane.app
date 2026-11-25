# Minecraft Server - Creativ

Minecraft-Bedrock-Server im Kreativmodus, Image [itzg/minecraft-bedrock-server](https://github.com/itzg/docker-minecraft-bedrock-server).

Mit dem Start wird die [Minecraft-EULA](https://www.minecraft.net/eula) akzeptiert (`EULA=TRUE`).

## Verbinden

In Minecraft (Bedrock: Handy, Konsole, Windows) unter **Server → Server hinzufügen** die Adresse des Hosts und den Port `19143` eintragen.

## Spieler und Rechte

- **`ALLOW_LIST=true`** (Standard): Nur Spieler aus der Allowlist kommen auf den Server. Spieler trägst du in `ALLOW_LIST_USERS` als `Gamertag:XUID` ein, oder du setzt `ALLOW_LIST=false`.
- **`OPS`**: Gamertags oder XUIDs der Operatoren, durch Komma getrennt.

Bestehende Einträge in `allowlist.json` und `permissions.json` im Datenverzeichnis bleiben erhalten.

## Variablen

| Variable           | Standard          | Bedeutung                                       |
|--------------------|-------------------|-------------------------------------------------|
| `MC_IMAGE_VERSION` | `latest`          | Image-Tag                                       |
| `MC_VERSION`       | `latest`          | Minecraft-Version                               |
| `SERVER_NAME`      | `BlockCreativ`    | Name in der Serverliste                         |
| `SERVER_PORT`      | `19143`           | UDP-Port im Container und auf dem Host          |
| `DIFFICULTY`       | `easy`            | Schwierigkeit                                   |
| `ONLINE_MODE`      | `true`            | Xbox-Live-Anmeldung erforderlich                |
| `OPS`              | leer              | Operatoren (Gamertags oder XUIDs)               |
| `ALLOW_LIST`       | `true`            | Nur Spieler aus der Allowlist                   |
| `ALLOW_LIST_USERS` | leer              | Allowlist (`Gamertag:XUID`)                     |
| `ALLOW_CHEATS`     | `true`            | Cheats erlauben                                 |
| `TZ`               | `Europe/Berlin`   | Zeitzone                                        |
| `MC_DATA`          | `./minecraft`     | Datenverzeichnis auf dem Host                   |

Der Spielmodus ist in dieser Vorlage fest auf `creative` eingestellt.

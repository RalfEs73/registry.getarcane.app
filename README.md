# Arcane Template Registry

Eigene Docker-Compose-Vorlagen für [Arcane](https://getarcane.app/).

## In Arcane einbinden

Unter **Templates → Registries** diese URL eintragen:

```
https://raw.githubusercontent.com/RalfEs73/registry.getarcane.app/main/registry.json
```

## Vorlagen

|  | Vorlage | Beschreibung | Tags | Version |
|---|---|---|---|---|
| <img src="https://raw.githubusercontent.com/selfhst/icons/main/svg/caddy.svg" width="24" alt=""> | [Caddy](templates/caddy) | Webserver und Reverse Proxy mit automatischen HTTPS-Zertifikaten. | `proxy` `web` | 1.0.0 |
| <img src="https://raw.githubusercontent.com/selfhst/icons/main/svg/minecraft.svg" width="24" alt=""> | [Minecraft Server - Creativ](templates/minecraft-creativ) | Minecraft-Bedrock-Server im Kreativmodus. | `game` `minecraft` | 1.0.0 |
| <img src="https://raw.githubusercontent.com/selfhst/icons/main/svg/minecraft.svg" width="24" alt=""> | [Minecraft Server - Survival](templates/minecraft-survival) | Minecraft-Bedrock-Server im Überlebensmodus. | `game` `minecraft` | 1.0.0 |
| <img src="https://raw.githubusercontent.com/selfhst/icons/main/svg/n8n.svg" width="24" alt=""> | [n8n](templates/n8n) | Workflow-Automatisierung mit visuellem Editor und vielen Integrationen. | `automation` `workflow` | 1.0.0 |
| <img src="https://raw.githubusercontent.com/selfhst/icons/main/svg/plex.svg" width="24" alt=""> | [Plex](templates/plex) | Mediaserver zum Streamen von Filmen, Serien und Musik. | `media` `streaming` | 1.0.0 |
| <img src="https://raw.githubusercontent.com/selfhst/icons/main/png/satisfactory.png" width="24" alt=""> | [Satisfactory Server](templates/satisfactory-server) | Dedizierter Server für das Fabrikbau-Spiel Satisfactory. | `game` | 1.0.0 |
| <img src="https://raw.githubusercontent.com/selfhst/icons/main/svg/tautulli.svg" width="24" alt=""> | [Tautulli](templates/tautulli) | Überwachung und Statistiken für Plex Media Server. | `media` `monitoring` | 1.1.0 |

## Aufbau

```
templates/<id>/
  compose.yaml     Compose-Datei
  .env.example     Variablen mit Platzhaltern (keine echten Secrets!)
  template.json    Metadaten: name, description, version, tags, icon_url
  README.md        Doku zur Vorlage
registry.json      Liste aller Vorlagen, die Arcane abruft
scripts/           später: Skript, das registry.json aus den template.json erzeugt
.github/workflows/ später: automatischer Build und Prüfung
```

## Neue Vorlage hinzufügen

1. Ordner `templates/<id>/` anlegen (Ordnername = `id`, nur Kleinbuchstaben und Bindestriche).
2. `compose.yaml`, `.env.example`, `template.json` und `README.md` anlegen.
3. Eintrag in `registry.json` ergänzen und `version` der Registry erhöhen.
4. Zeile in der Tabelle [Vorlagen](#vorlagen) oben ergänzen.

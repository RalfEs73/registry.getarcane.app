# Satisfactory Server

Dedizierter Server für das Fabrikbau-Spiel [Satisfactory](https://www.satisfactorygame.com/), Image [wolveix/satisfactory-server](https://github.com/wolveix/satisfactory-server).

## Voraussetzungen

- Mindestens 8 GB Arbeitsspeicher auf dem Host (Standard-Obergrenze 8 GB, 4 GB reserviert).
- Freie Ports `7777` (TCP und UDP) und `8888` (TCP), von außen erreichbar.
- Beim ersten Start lädt der Container die Serverdateien über Steam herunter (mehrere GB). Das dauert einige Minuten.

## Ersteinrichtung

Im Spiel unter **Server-Manager → Server hinzufügen** die Adresse des Hosts und Port `7777` eintragen. Beim ersten Verbinden vergibst du einen Servernamen und ein Admin-Passwort.

## Variablen

| Variable               | Standard         | Bedeutung                                  |
|------------------------|------------------|--------------------------------------------|
| `SATISFACTORY_VERSION` | `latest`         | Image-Tag                                  |
| `MAXPLAYERS`           | `4`              | Maximale Anzahl Spieler                    |
| `STEAMBETA`            | `false`          | Experimentelle Spielversion                |
| `PUID` / `PGID`        | `1000`           | Benutzer-/Gruppen-ID für Dateirechte       |
| `MEMORY_LIMIT`         | `8G`             | Obergrenze Arbeitsspeicher                 |
| `MEMORY_RESERVATION`   | `4G`             | Reservierter Arbeitsspeicher               |
| `SATISFACTORY_DATA`    | `./satisfactory` | Datenverzeichnis auf dem Host              |

Die Ports sind fest eingestellt, weil der Server sie auch intern verwendet.

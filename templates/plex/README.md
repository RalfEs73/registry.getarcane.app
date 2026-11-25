# Plex

Mediaserver zum Streamen von Filmen, Serien und Musik ([plex.tv](https://www.plex.tv/)), Image von [linuxserver.io](https://docs.linuxserver.io/images/docker-plex/).

## Voraussetzungen

- Die Mediendateien liegen auf dem Host unter `/mnt/plex-storage/`. Sie werden schreibgeschützt nach `/Storage` eingebunden.
- Der Container läuft mit `network_mode: host`, Plex ist also direkt unter Port `32400` des Hosts erreichbar.

## Ersteinrichtung

1. Unter [plex.tv/claim](https://www.plex.tv/claim) einen Claim-Token holen. Er ist nur **4 Minuten** gültig.
2. Den Token als `PLEX_CLAIM` eintragen und das Projekt sofort starten.
3. Nach der erfolgreichen Verknüpfung kann `PLEX_CLAIM` wieder leer bleiben.

Danach erreichbar unter `http://<host>:32400/web`.

## Variablen

| Variable        | Standard        | Bedeutung                              |
|-----------------|-----------------|----------------------------------------|
| `PLEX_VERSION`  | `latest`        | Image-Tag                              |
| `PLEX_CLAIM`    | leer            | Claim-Token für die Ersteinrichtung    |
| `PLEX_CONFIG`   | `./plex`        | Konfigurationsverzeichnis              |
| `PUID` / `PGID` | `1000`          | Benutzer-/Gruppen-ID für Dateirechte   |
| `TZ`            | `Europe/Berlin` | Zeitzone                               |

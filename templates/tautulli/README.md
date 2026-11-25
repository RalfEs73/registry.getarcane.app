# Tautulli

Überwachung und Statistiken für Plex Media Server ([tautulli.com](https://tautulli.com/)), Image von [linuxserver.io](https://docs.linuxserver.io/images/docker-tautulli/).

## Voraussetzung

Die Vorlage hängt den Container an ein **bestehendes externes Netzwerk** (Standard: `extern`). Falls es noch nicht existiert:

```sh
docker network create extern
```

## Variablen

| Variable           | Standard                 | Bedeutung                          |
|--------------------|--------------------------|------------------------------------|
| `TAUTULLI_VERSION` | `latest`                 | Image-Tag                          |
| `TAUTULLI_PORT`    | `8181`                   | Port auf dem Host                  |
| `TAUTULLI_CONFIG`  | `/home/docker/tautulli`  | Konfigurationsverzeichnis          |
| `PUID` / `PGID`    | `1000`                   | Benutzer-/Gruppen-ID für Dateirechte |
| `TZ`               | `Europe/Berlin`          | Zeitzone                           |
| `DOCKER_NETWORK`   | `extern`                 | Name des externen Netzwerks        |

## Aufruf

Nach dem Start erreichbar unter `http://<host>:8181`.

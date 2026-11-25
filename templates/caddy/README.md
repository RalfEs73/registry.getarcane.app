# Caddy

Webserver und Reverse Proxy mit automatischen HTTPS-Zertifikaten ([caddyserver.com](https://caddyserver.com/)).

## Voraussetzungen

- Ein **bestehendes externes Netzwerk** (Standard: `extern`). Falls es fehlt: `docker network create extern`
  Container im selben Netzwerk erreicht Caddy über ihren Namen, z. B. `n8n:8443`.
- Die Ports `80` und `443` sind auf dem Host frei und von außen erreichbar (für Let's-Encrypt-Zertifikate).

## Caddyfile vor dem ersten Start anlegen

Die Datei `Caddyfile` muss **vor dem Start** im Projektordner unter `./caddy/Caddyfile` liegen. Fehlt sie, legt Docker an ihrer Stelle einen leeren Ordner an, und Caddy startet nicht.

Beispiel:

```
n8n.example.com {
    reverse_proxy n8n:8443
}
```

Nach Änderungen am Caddyfile den Container neu starten.

## Verzeichnisse

| Pfad auf dem Host    | Im Container           | Inhalt                       |
|----------------------|------------------------|------------------------------|
| `./caddy/data`       | `/data`                | Zertifikate und Schlüssel    |
| `./caddy/config`     | `/config`              | Gespeicherte Konfiguration   |
| `./caddy/Caddyfile`  | `/etc/caddy/Caddyfile` | Konfiguration (nur lesbar)   |

## Variablen

| Variable           | Standard  | Bedeutung                                   |
|--------------------|-----------|---------------------------------------------|
| `CADDY_VERSION`    | `latest`  | Image-Tag                                   |
| `CADDY_HTTP_PORT`  | `80`      | HTTP-Port auf dem Host                      |
| `CADDY_HTTPS_PORT` | `443`     | HTTPS-Port auf dem Host                     |
| `CADDY_DIR`        | `./caddy` | Verzeichnis mit data, config und Caddyfile  |
| `DOCKER_NETWORK`   | `extern`  | Name des externen Netzwerks                 |

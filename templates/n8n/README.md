# n8n

Workflow-Automatisierung mit visuellem Editor ([n8n.io](https://n8n.io/)).

## Voraussetzungen

- Ein **bestehendes externes Netzwerk** (Standard: `extern`). Falls es fehlt: `docker network create extern`
- Ein Reverse Proxy mit HTTPS, der `N8N_HOST` auf den Container weiterleitet.

## Anmeldung

Beim ersten Aufruf legst du in n8n ein Owner-Konto an. Die früheren Variablen `N8N_BASIC_AUTH_*` gibt es seit n8n 1.0 nicht mehr und sind deshalb nicht enthalten.

## Variablen

| Variable                      | Standard                  | Bedeutung                                   |
|-------------------------------|---------------------------|---------------------------------------------|
| `N8N_VERSION`                 | `latest`                  | Image-Tag                                   |
| `N8N_HOST`                    | `n8n.example.com`         | Öffentlicher Hostname                       |
| `N8N_PORT`                    | `8443`                    | Port im Container und auf dem Host          |
| `N8N_PROTOCOL`                | `https`                   | Protokoll der öffentlichen URL              |
| `WEBHOOK_URL`                 | `https://n8n.example.com` | Basis-URL für Webhooks                      |
| `N8N_SECURE_COOKIE`           | `true`                    | Cookie nur über HTTPS (`false` ohne HTTPS)  |
| `NODE_FUNCTION_ALLOW_BUILTIN` | `crypto`                  | Erlaubte Node.js-Module in Code-Nodes       |
| `TZ`                          | `Europe/Berlin`           | Zeitzone                                    |
| `N8N_DATA`                    | `./data`                  | Datenverzeichnis auf dem Host               |
| `DOCKER_NETWORK`              | `extern`                  | Name des externen Netzwerks                 |

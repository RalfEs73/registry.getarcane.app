# MeTube

Weboberfläche zum Herunterladen von Videos von YouTube und vielen anderen Seiten ([alexta69/metube](https://github.com/alexta69/metube)), basiert auf yt-dlp.

## Voraussetzungen

Die Downloads landen auf dem Host unter `/mnt/winserver_youtube`. Das Verzeichnis muss vor dem Start existieren, z. B. als eingehängte Netzwerkfreigabe. Zugangsdaten für die Freigabe gehören nicht in diese Vorlage, sondern in eine Credentials-Datei auf dem Host (z. B. `/etc/fstab` mit `credentials=/root/.smbcredentials`).

## Aufruf

Nach dem Start erreichbar unter `http://<host>:8081`.

## Verzeichnisse

| Pfad auf dem Host        | Im Container | Inhalt                                   |
|--------------------------|--------------|------------------------------------------|
| `/mnt/winserver_youtube` | `/downloads` | Heruntergeladene Videos                  |
| `./metube`               | `/config`    | Einstellungen und Download-Warteschlange |

## Variablen

| Variable         | Standard   | Bedeutung                                   |
|------------------|------------|---------------------------------------------|
| `METUBE_VERSION` | `latest`   | Image-Tag                                   |
| `METUBE_PORT`    | `8081`     | Port auf dem Host                           |
| `METUBE_CONFIG`  | `./metube` | Verzeichnis für Einstellungen               |

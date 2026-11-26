# Plex

Mediaserver zum Streamen von Filmen, Serien und Musik ([plex.tv](https://www.plex.tv/)), Image von [linuxserver.io](https://docs.linuxserver.io/images/docker-plex/).

## Voraussetzungen

- Die Mediendateien liegen auf dem Host unter `/mnt/plex-storage/`. Sie werden schreibgeschützt nach `/Storage` eingebunden.
- Der Container läuft mit `network_mode: host`, Plex ist also direkt unter Port `32400` des Hosts erreichbar.

## Medienspeicher unter /mnt/plex-storage einhängen

Liegen die Medien auf einer Netzwerkfreigabe (SMB/CIFS, z. B. NAS, Windows-Server oder Storage Box), wird sie auf dem Host unter `/mnt/plex-storage` eingehängt. Die Platzhalter `SERVER`, `FREIGABE`, `BENUTZER` und `PASSWORT` durch die eigenen Werte ersetzen.

**1. CIFS-Werkzeuge installieren und Mount-Verzeichnis anlegen**

```sh
sudo apt install -y cifs-utils && sudo mkdir -p /mnt/plex-storage
```

**2. Zugangsdaten in einer geschützten Datei ablegen** (statt im Befehl)

```sh
printf 'username=BENUTZER\npassword=PASSWORT\n' | sudo tee /root/.smbcredentials-plex > /dev/null && sudo chmod 600 /root/.smbcredentials-plex
```

**3. Freigabe einmalig einhängen und prüfen**

```sh
sudo mount -t cifs //SERVER/FREIGABE /mnt/plex-storage -o credentials=/root/.smbcredentials-plex,uid=1000,gid=1000,iocharset=utf8,file_mode=0644,dir_mode=0755 && ls /mnt/plex-storage
```

**4. Dauerhaft einhängen** (auch nach einem Neustart)

```sh
echo '//SERVER/FREIGABE /mnt/plex-storage cifs credentials=/root/.smbcredentials-plex,uid=1000,gid=1000,iocharset=utf8,file_mode=0644,dir_mode=0755,_netdev,nofail 0 0' | sudo tee -a /etc/fstab && sudo systemctl daemon-reload && sudo mount -a
```

`_netdev` wartet beim Booten auf das Netzwerk, `nofail` verhindert, dass der Server bei nicht erreichbarer Freigabe hängen bleibt. Plex selbst bindet den Ordner nur lesend ein (`:ro`).

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

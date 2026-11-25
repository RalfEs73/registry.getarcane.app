# Arcane Template Registry

Eigene Docker-Compose-Vorlagen für [Arcane](https://getarcane.app/).

## In Arcane einbinden

Unter **Templates → Registries** diese URL eintragen:

```
https://raw.githubusercontent.com/RalfEs73/registry.getarcane.app/main/registry.json
```

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

# Checks

Dieser Ordner beschreibt die automatisierte Prüfung des As-built-IFC 4.3 gegen das IDS.

## Ziel

Geprüft wird, ob für Bauwerk und Lager der Brücke die betriebsrelevanten Angaben (Baujahr, Lagertyp, Einbaujahr) vorhanden sind. Erst danach werden die Daten ins Erhaltungsmanagement übernommen.

## Input

- As-built-IFC 4.3 (Modell ausgeführtes Werk)
- IDS (YAML → XML)

## Werkzeug

ifcopenshell / ifctester

## Ausführen

```
python pruefung.py modell.ifc
```

Die Ergebnisse mit GlobalIds werden in results/ abgelegt.

## Prüflogik

- Baujahr: Angabe muss vorhanden sein.
- Lagertyp: Angabe muss vorhanden sein.
- Einbaujahr: Angabe muss vorhanden sein. Ein Datum in der Vergangenheit ist kein Fehler (Schulprojekt). Ein Fehler liegt nur vor, wenn kein Datum angegeben ist.

## Testfälle

- Korrektes Modell (Modell_Wahr): Prüfung ohne Fehler, Prüfbericht speichern und Stichproben prüfen.
- Falsches Modell (Modell_Falsch): Prüfung mit Fehlern, Fehler kontrollieren und Prüfbericht speichern.

## Offen

- Stichprobe zur Plausibilität des Lagertyps durch den Fachplaner.
- Entscheid, welche IDS-Regel leitend ist: CH_Lager oder Hersteller-Properties.

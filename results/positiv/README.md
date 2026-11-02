# Ergebnis: positiver Fall

Dokumentiert einen Fall, in dem die Prüfungen bestanden werden.

## Ausgangslage

| | |
| --- | --- |
| Datensatz | Originaldatensatz, unverändert |
| Modell | Modell_Wahr |
| IDS-Datei (Name, Version) | IDS_Team1, IDS 1.0 (siehe `checks/README.md`) |
| Regel | R-01: Für IfcBearing muss CH_Lager.Lagertyp den Wert Elastomeric haben. R-02: Für IfcBearing muss CH_Lager.Einbaujahr vorhanden und eine ganze Zahl sein. |
| Werkzeug (Name) | IfcLite |

## Ergebnis

Alle 8 anwendbaren Objekte ( 8 IfcBearing) bestehen.

| GlobalId | Objekt | Datenpfad | Ist-Wert | Regel | Ergebnis | Grund |
| --- | --- | --- | --- | --- | --- | --- |
| `1mJGo_enD7SupWwYU$8ScU` | IfcBearing | CH_Lager.Lagertyp | Elastomeric | R-01 | bestanden | Wert ist erlaubt |
| `1mJGo_enD7SupWwYU$8ScU` | IfcBearing | CH_Lager.Einbaujahr | 2018 | R-02 | bestanden | Wert vorhanden, ganze Zahl |
| `1mJGo_enD7SupWwYU$8R_6` | IfcBearing | CH_Lager.Lagertyp | Elastomeric | R-01 | bestanden | Wert ist erlaubt |
| `1mJGo_enD7SupWwYU$8R_6` | IfcBearing | CH_Lager.Einbaujahr | 2018 | R-02 | bestanden | Wert vorhanden, ganze Zahl |

Die übrigen 6 Lager bestehen ebenfalls, siehe Tabelle «Alle Lager» in `results/README.md`.

Anwendbare Objekte: 8 (Auswahl über die IFC-Klassen IfcBearing).

## Belege

Ausgabe des Skripts `pruefung.py` auf dem Originaldatensatz:

```
R-01 und R-02 Lager: 8 von 8 bestanden
```

_TODO: Screenshot des Prüfberichts ergänzen (z. B. HTML-Report von ifctester)._

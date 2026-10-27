# Ergebnis: positiver Fall

Dokumentiert einen Fall, in dem die Prüfungen bestanden werden.

## Ausgangslage

| | |
| --- | --- |
| Datensatz | Originaldatensatz, unverändert |
| Modell (Name, Version) | Team_1_Bruecke_Arbeitsmodell.ifc, IFC4X3_ADD2 (nicht im Repository) |
| IDS-Datei (Name, Version) | Regeln R-01 bis R-03, IDS 1.0 (siehe `checks/README.md`) |
| Regel | R-02: Für IfcBearing muss CH_Lager.Lagertyp den Wert Elastomer, Topf oder Kalotte haben. R-03: Für IfcBearing muss CH_Lager.Einbaujahr vorhanden und eine ganze Zahl sein. R-01: Für IfcBridge muss CH_Bauwerksdaten.Baujahr vorhanden und eine ganze Zahl sein. |
| Werkzeug (Name, Version) | Python 3.13, ifcopenshell 0.9.0.post1, ifctester 0.9.0, Lauf vom 27.10.2026 |

## Ergebnis

Alle 9 anwendbaren Objekte (1 IfcBridge, 8 IfcBearing) bestehen.

| GlobalId | Objekt | Datenpfad | Ist-Wert | Regel | Ergebnis | Grund |
| --- | --- | --- | --- | --- | --- | --- |
| `3E7OAqC9L49eyA6mevHtu8` | IfcBridge | CH_Bauwerksdaten.Baujahr | 2005 | R-01 | bestanden | Wert vorhanden, ganze Zahl |
| `1mJGo_enD7SupWwYU$8ScU` | IfcBearing | CH_Lager.Lagertyp | Topf | R-02 | bestanden | Wert ist erlaubt |
| `1mJGo_enD7SupWwYU$8ScU` | IfcBearing | CH_Lager.Einbaujahr | 2018 | R-03 | bestanden | Wert vorhanden, ganze Zahl |
| `1mJGo_enD7SupWwYU$8R_6` | IfcBearing | CH_Lager.Lagertyp | Elastomer | R-02 | bestanden | Wert ist erlaubt |
| `1mJGo_enD7SupWwYU$8R_6` | IfcBearing | CH_Lager.Einbaujahr | 2018 | R-03 | bestanden | Wert vorhanden, ganze Zahl |

Die übrigen 6 Lager bestehen ebenfalls, siehe Tabelle «Alle Lager» in `results/README.md`.

Anwendbare Objekte: 9 (Auswahl über die IFC-Klassen IfcBridge und IfcBearing).

## Belege

Ausgabe des Skripts `pruefung.py` auf dem Originaldatensatz:

```
R-02 und R-03 Lager: 8 von 8 bestanden
R-01 Bruecke: 1 von 1 bestanden
```

_TODO: Screenshot des Prüfberichts ergänzen (z. B. HTML-Report von ifctester)._

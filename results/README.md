# Ergebnisse

Dokumentation der Prüfläufe mit dem Brückenmodell. Mindeststand: der aktuelle Lauf sowie ein positiver und ein negativer Fall, jeweils mit GlobalId, Ist-Wert, Regel und Grund.

Hinweis zu den Daten: Die Werte in CH_Lager und CH_Bauwerksdaten sind synthetische Lehrattribute und kein Nachweis aus einem realen Bauwerk (siehe `models/README.md`).

## Aktueller Lauf (Originaldatensatz)

| | |
| --- | --- |
| Datum | 27.10.2026 |
| Modell (Name, Version) | Team_1_Bruecke_Arbeitsmodell.ifc, IFC4X3_ADD2 (nicht im Repository, siehe `models/README.md`) |
| IDS-Datei (Name, Version) | Regeln R-01 bis R-03 als IDS 1.0 für IFC4X3_ADD2, aufgebaut im Skript `pruefung.py` (siehe `checks/README.md`) |
| Werkzeug (Name, Version) | Python 3.13, ifcopenshell 0.9.0.post1, ifctester 0.9.0 |
| Geprüfte Objekte | 9 (1 IfcBridge, 8 IfcBearing) |
| Bestanden / durchgefallen | 9 / 0 |

Ausgabe des Skripts:

```
R-02 und R-03 Lager: 8 von 8 bestanden
R-01 Bruecke: 1 von 1 bestanden
```

## Drei reale Datenpfade

Die drei Datenpfade stammen aus dem Originaldatensatz. Die GlobalIds der Lager erscheinen im negativen Fall wieder, dort mit veränderten Werten.

| Nr. | Datenpfad | GlobalId | Ist-Wert | Regel | Ergebnis | Grund |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | IfcBridge, CH_Bauwerksdaten.Baujahr | `3E7OAqC9L49eyA6mevHtu8` | 2005 | R-01: Baujahr vorhanden, ganze Zahl | bestanden | Wert vorhanden |
| 2 | IfcBearing, CH_Lager.Lagertyp | `1mJGo_enD7SupWwYU$8ScU` | Topf | R-02: Elastomer, Topf oder Kalotte | bestanden | Wert ist erlaubt |
| 3 | IfcBearing, CH_Lager.Einbaujahr | `1mJGo_enD7SupWwYU$8R_6` | 2018 | R-03: Einbaujahr vorhanden, ganze Zahl | bestanden | Wert vorhanden |

## Alle Lager (Originaldatensatz)

| GlobalId | Lagertyp | Einbaujahr | Ergebnis |
| --- | --- | --- | --- |
| `1mJGo_enD7SupWwYU$8ScU` | Topf | 2018 | bestanden |
| `1mJGo_enD7SupWwYU$8RxC` | Elastomer | 2018 | bestanden |
| `1mJGo_enD7SupWwYU$8R_g` | Kalotte | 2018 | bestanden |
| `1mJGo_enD7SupWwYU$8R_h` | Elastomer | 2018 | bestanden |
| `1mJGo_enD7SupWwYU$8R_t` | Kalotte | 2018 | bestanden |
| `1mJGo_enD7SupWwYU$8R_q` | Topf | 2018 | bestanden |
| `1mJGo_enD7SupWwYU$8R_6` | Elastomer | 2018 | bestanden |
| `1mJGo_enD7SupWwYU$8R_7` | Topf | 2018 | bestanden |

## Fälle

- [Positiver Fall](positiv/README.md): Originaldatensatz, 9 von 9 bestanden
- [Negativer Fall](negativ/README.md): gleiche Regel, bewusst veränderter Datensatz, 2 Lager durchgefallen

## Weiterer Befund

Die Hersteller-IDS vom 27.10. liefert im unveränderten Modell kein positives Ergebnis, siehe `checks/README.md`.

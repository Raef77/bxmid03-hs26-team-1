# Ergebnis: negativer Fall

Dokumentiert einen Fall, in dem eine Prüfung fehlschlägt. Regel und Auswahl sind identisch mit dem positiven Fall, nur die Daten sind verändert.

## Ausgangslage

| | |
| --- | --- |
| Datensatz | Lokale Testkopie des Originalmodells mit zwei bewussten Änderungen (nicht im Repository) |
| Modell (Name, Version) | Kopie von Team_1_Bruecke_Arbeitsmodell.ifc, IFC4X3_ADD2 |
| IDS-Datei (Name, Version) | Regeln R-01 bis R-03, IDS 1.0, unverändert gegenüber dem positiven Fall (siehe `checks/README.md`) |
| Regel | R-02: Für IfcBearing muss CH_Lager.Lagertyp den Wert Elastomeric haben. R-03: Für IfcBearing muss CH_Lager.Einbaujahr vorhanden und eine ganze Zahl sein. |
| Werkzeug (Name, Version) | Python 3.13, ifcopenshell 0.9.0.post1, ifctester 0.9.0, Lauf vom 27.10.2026 |
| Regel und Auswahl in beiden Läufen unverändert? | Ja |

## Was an den Daten verändert wurde

| GlobalId | Datenpfad | Original | Veränderung |
| --- | --- | --- | --- |
| `1mJGo_enD7SupWwYU$8RxC` | CH_Lager.Einbaujahr | None | auf «None», also leer,  gesetzt (kein erlaubter Wert) |

## Ergebnis

Von 9 anwendbaren Objekten bestehen 7. Die 2 veränderten Lager fallen durch. Die Brücke (R-01) und die übrigen 6 Lager bestehen unverändert.

| GlobalId | Objekt | Datenpfad | Ist-Wert | Regel | Ergebnis | Grund |
| --- | --- | --- | --- | --- | --- | --- |
| `1mJGo_enD7SupWwYU$8RxC` | IfcBearing | CH_Lager.Einbaujahr | None | R-02 | durchgefallen | Wert «None» ist nicht erlaubt (erlaubt: ganze Zahl) |

## Rückmeldung

Der Befund geht mit GlobalId und Grund als Mängelliste an die Projektverfasser:in (siehe `workflow/README.md`). Der Export als BCF-Datei ist vorgesehen, aber noch nicht umgesetzt.

## Belege

Ausgabe des Skripts `pruefung.py` auf der veränderten Testkopie:

```
R-02 Lager: 7 von 8 bestanden
  FEHLER 1mJGo_enD7SupWwYU$8RxC | The property value "None" does not match the requirements
R-01 Bruecke: 1 von 1 bestanden
```

_TODO: Screenshot des Prüfberichts ergänzen._

## Weiterer Befund

Die Hersteller-IDS vom 27.10. (Pset_ManufacturerTypeInformation) fällt nach Korrektur ihrer Applicability bei allen 8 Lagern durch, auch im Originaldatensatz. Details in `checks/README.md`.

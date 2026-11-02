# Ergebnis: negativer Fall

Dokumentiert einen Fall, in dem eine Prüfung fehlschlägt. Regel und Auswahl sind identisch mit dem positiven Fall, nur die Daten sind verändert.

## Ausgangslage

| | |
| --- | --- |
| Datensatz | Lokale Testkopie des Originalmodells mit einer bewussten Änderungen |
| Modell  | Modell_Falsch |
| IDS-Datei (Name, Version) | IDS_Team1, IDS 1.0, unverändert gegenüber dem positiven Fall (siehe `checks/README.md`) |
| Regel | R-02: Für IfcBearing muss CH_Lager.Lagertyp den Wert Elastomeric haben. R-03: Für IfcBearing muss CH_Lager.Einbaujahr vorhanden und eine ganze Zahl sein. |
| Werkzeug (Name, Version) | IFClite |
| Regel und Auswahl in beiden Läufen unverändert? | Ja |

## Was an den Daten verändert wurde

| GlobalId | Datenpfad | Original | Veränderung |
| --- | --- | --- | --- |
| `1mJGo_enD7SupWwYU$8RxC` | CH_Lager.Lagertyp | Elastomer | auf «», also leer,  gesetzt (kein erlaubter Wert) |

## Ergebnis

Von 8 anwendbaren Objekten bestehen 7. Das eine veränderte Lager fällt durch. Die Brücke (R-01) und die übrigen 7 Lager bestehen unverändert.

| GlobalId | Objekt | Datenpfad | Ist-Wert | Regel | Ergebnis | Grund |
| --- | --- | --- | --- | --- | --- | --- |
| `1mJGo_enD7SupWwYU$8RxC` | IfcBearing | CH_Lager.Lagertyp | "" | R-02 | durchgefallen | Wert «», also leer, ist nicht erlaubt (erlaubt: ganze Zahl) |

## Rückmeldung

Der Befund geht mit GlobalId und Grund als Mängelliste an die Projektverfasser:in (siehe `workflow/README.md`). Der Export als BCF-Datei ist vorgesehen, aber noch nicht umgesetzt.

## Belege

Ausgabe des Skripts `pruefung.py` auf der veränderten Testkopie:

```
R-02 Lager: 7 von 8 bestanden
  FEHLER 1mJGo_enD7SupWwYU$8RxC | The property value "" does not match the requirements
R-01 Bruecke: 1 von 1 bestanden
```

# Checks

Prüfungen des Teams für die Brückenübergabe. Die Regeln entsprechen den Anforderungen R-01 bis R-03 in `requirements/`.

Werkzeug (Stand 27.10.2026): Python 3.13, ifcopenshell 0.9.0.post1, ifctester 0.9.0. Die Regeln sind als IDS 1.0 für IFC4X3_ADD2 aufgebaut.

## Prüfungen

| ID | Prüfung | Erwartetes Ergebnis | Art | Status |
| --- | --- | --- | --- | --- |
| C-01 | R-01: Jede IfcBridge hat CH_Bauwerksdaten.Baujahr als ganze Zahl | Alle IfcBridge bestehen | automatisch (IDS) | bestanden, 1 von 1 (Originaldatensatz) |
| C-02 | R-02: Jedes IfcBearing hat CH_Lager.Lagertyp mit Wert Elastomer, Topf oder Kalotte | Alle IfcBearing bestehen | automatisch (IDS) | bestanden, 8 von 8 (Originaldatensatz) |
| C-03 | R-03: Jedes IfcBearing hat CH_Lager.Einbaujahr als ganze Zahl | Alle IfcBearing bestehen | automatisch (IDS) | bestanden, 8 von 8 (Originaldatensatz) |
| C-04 | R-03: Einbaujahr liegt nicht in der Zukunft | Alle IfcBearing bestehen | eigene Prüflogik | offen |
| C-05 | Plausibilität (Fachplaner, Stichprobe): CH_Lager.Lagertyp passt zur Lagerart im Modell | Übereinstimmung | manuell | offen, siehe Beobachtung unten |

Beobachtung zu C-05 (vom Team zu klären): Bei allen 8 Lagern ist der PredefinedType ELASTOMERIC und die Art in ASB-ING_2013 lautet «Elastomer». CH_Lager.Lagertyp nennt bei 3 Lagern aber «Topf» und bei 2 Lagern «Kalotte». Eine IDS-Prüfung findet das nicht, weil alle Werte erlaubt sind. Genau dafür ist die stichprobenartige Prüfung durch den Fachplaner vorgesehen.

## Ausführen

1. Python installieren und die Pakete in den angegebenen Versionen einrichten:

```
pip install ifcopenshell==0.9.0.post1 ifctester==0.9.0
```

2. Das folgende Skript als `pruefung.py` speichern.
3. Aufruf mit dem IFC-Modell (liegt lokal, nicht im Repository, siehe `models/README.md`):

```
python pruefung.py modell.ifc
```

Skript:

```python
"""Prüft ein IFC-Modell gegen die Übergabe-Regeln R-01 bis R-03 (IDS 1.0).

Aufruf: python pruefung.py <modell.ifc>
"""
import sys

import ifcopenshell
import ifctester.ids as ids
import ifctester.reporter as reporter


def regeln_erstellen():
    regeln = ids.Ids(title="Uebergabe Bruecke: Lager und Bauwerk")

    lager = ids.Specification(name="R-02 und R-03 Lager", ifcVersion=["IFC4X3_ADD2"])
    lager.applicability.append(ids.Entity(name="IFCBEARING"))
    lager.requirements.append(ids.Property(
        propertySet="CH_Lager", baseName="Lagertyp", dataType="IFCLABEL", cardinality="required",
        value=ids.Restriction(options={"enumeration": ["Elastomer", "Topf", "Kalotte"]})))
    lager.requirements.append(ids.Property(
        propertySet="CH_Lager", baseName="Einbaujahr", dataType="IFCINTEGER", cardinality="required"))
    regeln.specifications.append(lager)

    bruecke = ids.Specification(name="R-01 Bruecke", ifcVersion=["IFC4X3_ADD2"])
    bruecke.applicability.append(ids.Entity(name="IFCBRIDGE"))
    bruecke.requirements.append(ids.Property(
        propertySet="CH_Bauwerksdaten", baseName="Baujahr", dataType="IFCINTEGER", cardinality="required"))
    regeln.specifications.append(bruecke)
    return regeln


if __name__ == "__main__":
    modell = ifcopenshell.open(sys.argv[1])
    regeln = regeln_erstellen()
    regeln.validate(modell)
    for spez in reporter.Json(regeln).report()["specifications"]:
        print(f"{spez['name']}: {spez['total_applicable_pass']} von {spez['total_applicable']} bestanden")
        for anf in spez["requirements"]:
            for fehler in anf["failed_entities"]:
                print(f"  FEHLER {fehler.get('global_id') or fehler.get('guid')} | {fehler['reason']}")
```

Die Ausgabe nennt pro Regel die Anzahl bestandener Objekte und bei Fehlern die GlobalId mit Grund. Die Läufe mit Ergebnissen stehen in `results/`.

## Hinweis zur IDS vom 27.10. (Hersteller-Properties)

Die im IDS-Editor erstellte Spezifikation «Lager» (Pset_ManufacturerTypeInformation mit ArticleNumber, Manufacturer, ProductionYear und ModelLabel) wählt im Modell kein Objekt aus: 0 von 8 Lagern. Zwei Ursachen, die je für sich genügen:

- Die Applicability enthält zwei Property-Facets mit leerem Namen.
- Der PredefinedType «None» passt nicht zu den Lagern (ELASTOMERIC).

Mit einer Applicability nur auf IfcBearing werden alle 8 Lager geprüft. Alle 8 fallen bei allen vier Properties durch, weil Pset_ManufacturerTypeInformation nur die Property Manufacturer ohne Wert enthält.

Offen: Das Team entscheidet, ob CH_Lager (Projektwahl, Abschnitt oben) oder die Hersteller-Properties die leitende Regel sind. Die IDS-Datei selbst liegt im Teamordner und ist nicht im Repository.

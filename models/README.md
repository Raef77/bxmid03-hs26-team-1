# Modelle

Geschützte Modelle gehören nicht ins Repository. Stattdessen wird hier beschrieben, welche Modelle verwendet werden und wie man sie bezieht.

Ausnahme: Das bereinigte Lehrmodell `Team_1_Bruecke_BFH_Minor.ifc` (vom Dozenten bereitgestellt, 9.11.2026) liegt hier im Ordner. Welche Bauteile und Properties es enthält, steht in [`Team_1_Elementplan.md`](Team_1_Elementplan.md).

| Modell | Version | Quelle / Bezug | Lizenz | Hinweis |
| --- | --- | --- | --- | --- |
| Modell_Wahr | IFC4X3_ADD2, Export vom 19.10.2026 mit ifc-lite (laut Dateikopf) | Arbeitsmodell von Team 1, liegt im gemeinsamen Teamordner und wird lokal abgelegt | IFC-Lite-Testkorpus (ifcbridge-model01), nach IFC4X3 migriert; Lager- und Baujahrdaten sind synthetische Lehrdaten | Brücke «BW 533» (Brücke Bergedorfer Str. / BAB 1), ca. 14,8 MB. Enthält 1 IfcBridge und 8 IfcBearing. Die Property Sets CH_Lager und CH_Bauwerksdaten sind synthetische Lehrattribute (siehe unten). |
| Modell_Falsch | IFC4X3_ADD2, Export vom 19.10.2026 mit ifc-lite (laut Dateikopf) | Arbeitsmodell von Team 1, liegt im gemeinsamen Teamordner und wird lokal abgelegt | IFC-Lite-Testkorpus (ifcbridge-model01), nach IFC4X3 migriert; Lager- und Baujahrdaten sind synthetische Lehrdaten | Brücke «BW 533» (Brücke Bergedorfer Str. / BAB 1), ca. 14,8 MB. Enthält 1 IfcBridge und 8 IfcBearing. Die Property Sets CH_Lager und CH_Bauwerksdaten sind synthetische Lehrattribute (siehe unten). |

## Inhalt des Arbeitsmodells (für die Prüfungen)

| Objekt | Anzahl | Property Set | Properties |
| --- | --- | --- | --- |
| IfcBridge | 1 | CH_Bauwerksdaten | Baujahr |
| IfcBearing | 8 | CH_Lager | Lagertyp, Einbaujahr |

Im Modell sind die ergänzten Werte über das Property Set CH_Lehre gekennzeichnet. Bei den Lagern steht dort «Synthetic teaching attributes; original geometry and GlobalId retained», bei der Brücke «Synthetic teaching year; not as-built evidence». Die Werte sind daher Lehrdaten und kein Nachweis aus einem realen Bauwerk. Die GlobalIds der Lager stammen laut dieser Kennzeichnung aus dem Ausgangsmodell.

## Hinweise

- Keine Modelldateien oder Zugangsdaten committen.
- Das Modell lokal ablegen und den Pfad beim Aufruf des Prüfskripts angeben (siehe `checks/README.md`).
- Veränderte Testkopien des Modells (zum Beispiel für den negativen Fall) ebenfalls nur lokal halten. Die Änderungen werden in `results/negativ/README.md` beschrieben.

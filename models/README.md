# Modelle

Geschützte Modelle gehören nicht ins Repository. Stattdessen wird hier beschrieben, welche Modelle verwendet werden und wie man sie bezieht.

Das bereinigte Lehrmodell `Team_1_Bruecke_BFH_Minor.ifc` (vom Dozenten bereitgestellt, 9.11.2026) ist nicht geschützt und liegt deshalb hier. Bauteile und Properties: [`Team_1_Elementplan.md`](Team_1_Elementplan.md).

| Modell | Version | Quelle / Bezug | Lizenz | Hinweis |
| --- | --- | --- | --- | --- |
| Modell_Wahr | IFC4X3_ADD2, Export vom 19.10.2026 mit ifc-lite (laut Dateikopf) | Arbeitsmodell von Team 1, liegt im gemeinsamen Teamordner und wird lokal abgelegt | IFC-Lite-Testkorpus (ifcbridge-model01), nach IFC4X3 migriert; Lager- und Baujahrdaten sind synthetische Lehrdaten | Brücke «BW 533» (Brücke Bergedorfer Str. / BAB 1), ca. 14,8 MB. Enthält 1 IfcBridge und 8 IfcBearing. Die Property Sets CH_Lager und CH_Bauwerksdaten sind synthetische Lehrattribute (siehe unten). |
| Modell_Falsch | IFC4X3_ADD2, Export vom 19.10.2026 mit ifc-lite (laut Dateikopf) | Arbeitsmodell von Team 1, liegt im gemeinsamen Teamordner und wird lokal abgelegt | IFC-Lite-Testkorpus (ifcbridge-model01), nach IFC4X3 migriert; Lager- und Baujahrdaten sind synthetische Lehrdaten | Brücke «BW 533» (Brücke Bergedorfer Str. / BAB 1), ca. 14,8 MB. Enthält 1 IfcBridge und 8 IfcBearing. Die Property Sets CH_Lager und CH_Bauwerksdaten sind synthetische Lehrattribute (siehe unten). |
| Team_1_Bruecke_BFH_Minor.ifc | IFC4X3_ADD2, bereinigt am 9.11.2026 | In diesem Ordner | wie Modell_Wahr; alle Werte in BFH_Minor sind fiktive Lehrdaten | Bereinigte Kopie von Modell_Wahr, gleiche Geometrie und GlobalIds, ohne zwei Hilfsobjekte. 163 Bauteile mit je einem Pset BFH_Minor. |

## Testmodelle für das Property-Mapping (24.11.2026)

Kopien von `Team_1_Bruecke_BFH_Minor.ifc` mit denselben Bauteilen, GlobalIds, Werten und Datentypen. Geändert sind nur die von `requirements/Team1_Lager_Elastomer.ids` verlangten Properties an den 8 IfcBearing und der IfcBridge. Alle anderen Psets sind unverändert.

| Datei | Änderung |
| --- | --- |
| `Team_1_Bruecke_Variante_A_CustomPsets.ifc` | Properties mit vereinbarten Namen, aber in `Custom_Lager` (statt `BFH_Minor`) und `Custom_Bauwerk` (statt `CH_Bauwerksdaten`) |
| `Team_1_Bruecke_Variante_B_InterneNamen.ifc` | Properties in anderen Psets und mit anderen Namen als in der IDS |

Ergebnis IfcTester (ifcopenshell 0.9):

| Modell | Elastomerlager | Brücke Baujahr |
| --- | --- | --- |
| `Team_1_Bruecke_BFH_Minor.ifc` | 5 Fehler | erfüllt |
| Variante A, Variante B | 32 Fehler | nicht erfüllt |

Ein korrektes Mapping auf die vereinbarten Psets und Properties ergibt dasselbe Ergebnis wie `Team_1_Bruecke_BFH_Minor.ifc`.

Die 5 Fehler im Ausgangsmodell: 3 Topflager und 2 Kalottenlager haben `PredefinedType ELASTOMERIC`. Darum gelten für sie die Anforderungen an Elastomerlager, und die Spezifikationen für POT und SPHERICAL finden kein Bauteil.

## Inhalt des Arbeitsmodells (Modell_Wahr / Modell_Falsch)

Im Lehrmodell haben die Bauteile kein CH_Lager und kein CH_Lehre mehr, die Lagerdaten stehen in BFH_Minor (CH_Bauwerksdaten und CH_Lehre an der Brücke bleiben).

| Objekt | Anzahl | Property Set | Properties |
| --- | --- | --- | --- |
| IfcBridge | 1 | CH_Bauwerksdaten | Baujahr |
| IfcBearing | 8 | CH_Lager | Lagertyp, Einbaujahr |

Im Modell sind die ergänzten Werte über das Property Set CH_Lehre gekennzeichnet. Bei den Lagern steht dort «Synthetic teaching attributes; original geometry and GlobalId retained», bei der Brücke «Synthetic teaching year; not as-built evidence». Die Werte sind daher Lehrdaten und kein Nachweis aus einem realen Bauwerk. Die GlobalIds der Lager stammen laut dieser Kennzeichnung aus dem Ausgangsmodell.

## Hinweise

- Keine weiteren Modelldateien oder Zugangsdaten committen (Ausnahmen: das Lehrmodell und die Mapping-Testmodelle oben).
- Das Modell lokal ablegen und den Pfad beim Aufruf des Prüfskripts angeben (siehe `checks/README.md`).
- Veränderte Testkopien des Modells (zum Beispiel für den negativen Fall) ebenfalls nur lokal halten. Ausnahme: die zwei Testmodelle für das Property-Mapping oben. Die Änderungen werden in `results/negativ/README.md` beschrieben.

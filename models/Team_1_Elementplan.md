# Elementplan Team 1 Brücke

Modell: `Team_1_Bruecke_BFH_Minor.ifc` (bereinigte Kopie von `Team_1_Bruecke_Arbeitsmodell.ifc`, Stand 9.11.2026)

Alle 163 Bauteile haben genau ein Property Set **`BFH_Minor`**. Pro Kategorie gibt es 2–3 Properties plus `Einbaujahr`. Die Werte sind fiktiv, aber plausibel. Zahlen stehen ohne Einheit im Modell, die Einheit steht im Tabellenkopf.

Zusätzlich zu prüfen: das Attribut **`Name`** (lesbar und eindeutig, z. B. `Flügelwand WL-NO`). Jeder Name enthält die Lage, wo nötig mit Nummer: von West nach Ost (Bauteilmitte), übereinander liegende Teile von unten nach oben, parallele, sich überdeckende Streifen (z. B. Betonpflaster Mittelstreifen, Schutzplanken UB) quer zu ihrer Längsrichtung von West nach Ost. Kürzel: WL = Widerlager, MP = Mittelpfeiler, UB = Überbau, N/S/NO/NW/SO/SW = Himmelsrichtung; Mittelstreifen und Seitenstreifen-W/O liegen auf der Autobahn unter der Brücke.

## Properties pro Kategorie

| Kategorie | Properties in `BFH_Minor` | Datentyp (für IDS `dataType`) |
|---|---|---|
| Beton | `NPK_Typ`, `Bewehrungsstahl`, `Ueberdeckung` [mm], `Einbaujahr` | IfcLabel, IfcLabel, IfcInteger, IfcInteger |
| Belag | `Schichtstaerke` [mm], `Sorte`, `Einbaujahr` | IfcInteger, IfcLabel, IfcInteger |
| Stahl | `Stahlqualitaet`, `Korrosionsschutz`, `Profil`, `Einbaujahr` | IfcLabel, IfcLabel, IfcLabel, IfcInteger |
| Lager | `Lagertyp`, `Lieferant`, `Modell`, `Einbaujahr` | IfcLabel, IfcLabel, IfcLabel, IfcInteger |

Property-Namen ohne Umlaute (ae/oe/ue), damit sie sich in IDS-Regeln einfach schreiben lassen.

## Beton (46 Bauteile)

| Bauteil | IFC-Klasse | Anzahl | `NPK_Typ` | `Bewehrungsstahl` | `Ueberdeckung` [mm] | `Einbaujahr` |
|---|---|---|---|---|---|---|
| Gesims | IfcBeam | 4 | NPK G | B500B | 55 | 2005 |
| Endquerträger | IfcBeam | 4 | NPK F | B500B | 55 | 2005 |
| Kappe | IfcBeam | 4 | NPK G | B500B | 55 | 2005 |
| Kappe Übergang | IfcBuildingElementProxy | 1 | NPK G | B500B | 55 | 2005 |
| Pfeiler | IfcColumn | 3 | NPK F | B500C | 55 | 2005 |
| Sauberkeitsschicht | IfcFooting | 4 | NPK A | unbewehrt | 0 | 2005 |
| Fundament | IfcFooting | 6 | NPK C | B500B | 50 | 2005 |
| Magerbeton | IfcFooting | 2 | NPK A | unbewehrt | 0 | 2005 |
| Fahrbahnplatte Fertigteil | IfcSlab | 2 | NPK D | B500B | 40 | 2005 |
| Fahrbahnplatte Ortbeton | IfcSlab | 2 | NPK F | B500B | 55 | 2005 |
| Böschungstreppe | IfcStair | 4 | NPK C | B500A | 35 | 2005 |
| Flügelwand | IfcWall | 4 | NPK F | B500B | 55 | 2005 |
| Hilfswand | IfcWall | 2 | NPK F | B500B | 55 | 2005 |
| Widerlagerwand | IfcWall | 4 | NPK F | B500B | 55 | 2005 |

## Belag (19 Bauteile)

| Bauteil | IFC-Klasse | Anzahl | `Schichtstaerke` [mm] | `Sorte` | `Einbaujahr` |
|---|---|---|---|---|---|
| Betonpflaster | IfcBuildingElementProxy | 3 | 80 | Betonpflaster | 2005 |
| Fahrbahnmarkierung | IfcBuildingElementProxy | 2 | 3 | Kaltplastik weiss | 2018 |
| Pflästerung | IfcBuildingElementProxy | 8 | 120 | Granitpflaster 10/12 | 2005 |
| Fahrbahnbelag | IfcBuildingElementProxy | 2 | 40 | SMA 11 | 2018 |
| Granitstufe | IfcStair | 4 | 150 | Granit-Blockstufe | 2005 |

## Stahl (90 Bauteile)

| Bauteil | IFC-Klasse | Anzahl | `Stahlqualitaet` | `Korrosionsschutz` | `Profil` | `Einbaujahr` |
|---|---|---|---|---|---|---|
| Längsträger | IfcBuildingElementProxy | 26 | S355J2+N | EP-Zinkstaub + 2x EP, 310 µm | HEM 1000 | 2005 |
| Kopfplatte | IfcBuildingElementProxy | 24 | S355J2+N | EP-Zinkstaub + 2x EP, 310 µm | Blech 40 mm | 2005 |
| Kopfplatte | IfcPlate | 28 | S355J2+N | EP-Zinkstaub + 2x EP, 310 µm | Blech 40 mm | 2005 |
| Schutzplanke | IfcRailing | 4 | S235JR | feuerverzinkt | A-Profil | 2005 |
| Geländer | IfcRailing | 2 | S235JRH | feuerverzinkt | RRW 60x40 | 2005 |
| Schutzplanke Seitenstreifen-W | IfcRailing | 1 | S235JR | feuerverzinkt | A-Profil | 2018 |
| Schutzplanke Seitenstreifen-O | IfcRailing | 1 | S235JR | feuerverzinkt | A-Profil | 2018 |
| Fahrbahnübergang | IfcDiscreteAccessory | 4 | S355J2+N | EP-Zinkstaub + 2x EP, 370 µm | Einprofil-Übergang 80 mm | 2018 |

## Lager (8 Bauteile)

| Bauteil | IFC-Klasse | Anzahl | `Lagertyp` | `Lieferant` | `Modell` | `Einbaujahr` |
|---|---|---|---|---|---|---|
| Elastomerlager | IfcBearing | 3 | Elastomer | mageba | LASTO BLOCK | 2018 |
| Topflager | IfcBearing | 3 | Topf | mageba | TETRON CD | 2018 |
| Kalottenlager | IfcBearing | 2 | Kalotte | Maurer | MSM Kalottenlager | 2018 |

## Umstellung für euer IDS

Die Lagerdaten stehen neu in `BFH_Minor` statt in `CH_Lager`. In [`requirements/Team1_Lager_Elastomer.ids`](../requirements/Team1_Lager_Elastomer.ids) reicht es, bei R-01 und R-02 den Pset-Namen `CH_Lager` durch `BFH_Minor` zu ersetzen. `Lagertyp` und `Einbaujahr` haben dieselben Werte wie vorher, R-03 (`CH_Bauwerksdaten.Baujahr` am IfcBridge) bleibt unverändert. Mit dieser Änderung liefert euer IDS auf dem neuen Modell dasselbe Ergebnis wie auf dem alten.

## Hinweise

- Bauwerk erstellt 2005 (`Baujahr` am IfcBridge). Lager, Fahrbahnbelag, Markierung, Fahrbahnübergänge und die Schutzplanken an den BAB-Seitenstreifen sind von 2018.
- Sauberkeitsschicht und Magerbeton sind unbewehrt: `Ueberdeckung` = 0 heisst «nicht anwendbar». Regeln wie «Ueberdeckung ≥ 20» müssen diese Bauteile ausnehmen.
- Von den Bauteilen entfernt: alle bisherigen Psets (`ASB-ING_2013`, `sonstige Attribute`, `Hyperlinks`, `Pset_BuildingElementProxyCommon`, `Pset_ManufacturerTypeInformation`, `Pset_RailingCommon`, `CH_Lager`, `CH_Lehre`) sowie zwei Hilfsobjekte ohne Bauteilcharakter (Projektnullpunkt, 3D-Jahreszahl). Deren ungenutzte Geometrie-, Material- und Layer-Reste sind noch im File.
- Unverändert (bis auf die Einträge der entfernten Hilfsobjekte): Geometrie, GlobalIds, IFC-Klassen, die Psets an IfcBridge und IfcBridgePart, Material- und Klassifikationszuordnungen, `ObjectType` und die Typobjekte (Revit-Bezeichnungen, alle IfcBuildingElementProxyType).
- Wie im Original: Alle Lager haben den PredefinedType ELASTOMERIC, 5 davon sind aber Topf- oder Kalottenlager (absichtlicher Prüffall, eure Regel R-01 findet genau diese 5). Kopfplatten sind teils IfcPlate, teils IfcBuildingElementProxy.

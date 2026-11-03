# IDS Elastomerlager (Vorschlag Dozent, 03.11.2026)

Datei: [`Team1_Lager_Elastomer.ids`](Team1_Lager_Elastomer.ids) · IDS 1.0 · IFC4X3_ADD2 · gegen das offizielle IDS-1.0-Schema geprüft.

## Was die IDS prüft

| ID | Gilt für | Anforderung | Warum |
|---|---|---|---|
| R-01 | `IfcBearing` mit `PredefinedType` = `ELASTOMERIC` | `CH_Lager.Lagertyp` (IfcLabel) = `Elastomer` | Der Lagertyp muss zur Lagerart passen. «Topf» oder «Kalotte» an einem Elastomerlager ist ein Widerspruch. |
| R-02 | gleiche Lager | `CH_Lager.Einbaujahr` (IfcInteger) zwischen 1950 und 2026 | Ganze Zahl, nicht in der Zukunft. Ersetzt die offene Prüflogik «≤ aktuelles Jahr». |
| R-03 | `IfcBridge` | `CH_Bauwerksdaten.Baujahr` (IfcInteger) zwischen 1850 und 2026 | Stammdaten fürs Erhaltungssystem. |

Die Auswahl über `PredefinedType` ist der Kern: Die IDS prüft nicht mehr «irgendein erlaubter Wert», sondern ob zwei Angaben im Modell zusammenpassen.

## Ausführen (IFC-Lite, Browser)

1. https://www.ifclite.com öffnen, «Open model file» → `Team_1_Bruecke_Arbeitsmodell.ifc` (Kurs-Repository `LTplus-AG/bxmid03-hs26`, Ordner `modelle/`).
2. «Analyze» → «Data validation» → Reiter «IDS validation» → «Load IDS File» → `requirements/Team1_Lager_Elastomer.ids`.
3. «Run Validation».

Alternativ im Terminal: `npx @ifc-lite/cli@0.45.0 ids Team_1_Bruecke_Arbeitsmodell.ifc requirements/Team1_Lager_Elastomer.ids`

## Erwartete Ergebnisse (geprüft mit ifctester 0.9.0 und IFC-Lite CLI 0.45.0)

| Modell | R-01/R-02 Lager | R-03 Brücke | Ergebnis |
|---|---|---|---|
| Arbeitsmodell, unverändert | 3 von 8 bestanden | 1 von 1 | durchgefallen |
| Testkopie: alle 8 Lagertypen auf «Elastomer» | 8 von 8 | 1 von 1 | bestanden |
| Testkopie wie oben, Lager `1mJGo_enD7SupWwYU$8RxC` mit Einbaujahr 2031 | 7 von 8 | 1 von 1 | durchgefallen |

Durchgefallen im unveränderten Arbeitsmodell:

| GlobalId | Lagertyp im Modell | PredefinedType |
|---|---|---|
| `1mJGo_enD7SupWwYU$8ScU` | Topf | ELASTOMERIC |
| `1mJGo_enD7SupWwYU$8R_7` | Topf | ELASTOMERIC |
| `1mJGo_enD7SupWwYU$8R_q` | Topf | ELASTOMERIC |
| `1mJGo_enD7SupWwYU$8R_g` | Kalotte | ELASTOMERIC |
| `1mJGo_enD7SupWwYU$8R_t` | Kalotte | ELASTOMERIC |

## Für euch zu tun

- Entscheiden, welche Angabe stimmt: Lagerart (`PredefinedType`) oder `Lagertyp`. Das ist eure Fachplaner-Stichprobe (C-05), jetzt automatisch gefunden.
- Die beiden Testkopien selbst erstellen (lokal, nicht committen) und die Ergebnisse in `results/positiv` und `results/negativ` mit eurer eigenen Ausgabe ersetzen.
- Matrix in `requirements/README.md` anpassen (R-01 Wert «Elastomer», R-03 Baujahr wieder aufnehmen).
- Den Eintrag in `KI_USAGE.md` ergänzen, wenn ihr diese IDS übernehmt oder verändert.

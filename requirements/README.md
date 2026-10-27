# Anforderungen

Scope: Bauwerk und Lager der Brücke (Brückenmodell, Team 1).
Quelle: Projektwahl des Teams (Oktober 2026). Meilenstein für alle Anforderungen: Ende Phase 53 (Übergabe).

## Matrix (AIA-BEP)

| ID | Anforderung | Zweck | Objekt (IFC-Klasse) | Property / Quantity | Werte | Prüfung | Wer | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| R-01 | Brücke hat ein Baujahr | Stammdaten fürs Erhaltungssystem | IfcBridge | CH_Bauwerksdaten.Baujahr | Jahr (JJJJ), integer | IDS | Modellautor ING / BIM-Koordination | IDS-Regel getestet, siehe `checks/` und `results/` |
| R-02 | Lager haben einen Lagertyp | Erhaltungs- und Ersatzplanung | IfcBearing | CH_Lager.Lagertyp | Elastomer / Topf / Kalotte | IDS + Stichprobe | Modellautor ING / BIM-Koordination | IDS-Regel getestet, Stichprobe offen |
| R-03 | Lager haben ein Einbaujahr | Nutzungsdauer und Ersatzzeitpunkt berechnen | IfcBearing | CH_Lager.Einbaujahr | Jahr (JJJJ), integer | IDS + eigene Prüflogik (≤ aktuelles Jahr) | Modellautor ING / BIM-Koordination | IDS-Regel getestet, Prüflogik «≤ aktuelles Jahr» offen |

## Regeln in Worten

- R-01: Für IfcBridge muss CH_Bauwerksdaten.Baujahr vorhanden sein und eine ganze Zahl (Jahr, JJJJ) enthalten.
- R-02: Für IfcBearing muss CH_Lager.Lagertyp einen der Werte Elastomer, Topf oder Kalotte haben.
- R-03: Für IfcBearing muss CH_Lager.Einbaujahr vorhanden sein und eine ganze Zahl (Jahr, JJJJ) enthalten. Das Jahr darf nicht in der Zukunft liegen (noch nicht automatisch geprüft).

Datenquelle: Instanz (die Property Sets liegen an den Bauteilen, nicht am Typ).

## Rolle und Lagerinformation

Abgeleitet aus Projektwahl und Workflow, vom Team zu bestätigen.

| Rolle | Benötigte Lagerinformation | Wofür / Entscheidung |
| --- | --- | --- |
| Erhaltungsmanagement (Empfänger) | Lagertyp, Einbaujahr, Baujahr der Brücke | Übernahme ins Erhaltungssystem (z. B. KUBA), Erhaltungs- und Ersatzplanung, Nutzungsdauer und Ersatzzeitpunkt |
| Auftraggeber / Bauherr | Alle drei Angaben | Informationsanforderungen festlegen, IDS bereitstellen, Daten prüfen und freigeben (Abnahme) |
| Projektverfasser:in (Ingenieurbüro) | Alle drei Angaben | Angaben im Modell ausgeführtes Werk liefern, Mängel nach BCF-Rückmeldung korrigieren |
| BIM-Koordination (MVP-Tool) | Alle drei Angaben | Vollständigkeit per IDS prüfen, Prüfbericht und Stammdaten-Export erstellen |
| Fachplaner | Lagertyp, Einbaujahr | Werte stichprobenartig auf Plausibilität prüfen |

## Offene Punkte

- Abgleich der Brückenmatrix mit der älteren Stahlstützen-Matrix durch das Team.
- Prüflogik «Einbaujahr ≤ aktuelles Jahr» ergänzen (R-03).
- Stichprobe für den Lagertyp definieren (R-02), siehe Plausibilitätsprüfung in `checks/`.
- Bestätigen, welche Rolle welche Lagerinformation braucht.

# Colab-Notebook

Notebook zum MVP «Übergabe-Check Brücken» (Entwurf).

Direkt in Google Colab öffnen: https://colab.research.google.com/drive/1AOgEidv70cEfHK40in8DMtTAZ7sCWO8z?usp=sharing

Kopie der Datei in diesem Repo: MVP_Uebergabe-Check_Bruecken_Entwurf.ipynb

## Stand 17.11.2026

Das Colab-Notebook ist die aktuelle Fassung. Die Kopie `MVP_Uebergabe-Check_Bruecken_Entwurf.ipynb` in diesem Ordner entspricht dem früheren Entwurfsstand und ist nicht nachgeführt.

**Quellen aus diesem Repo (werden beim Ausführen geklont)**

- IDS: `requirements/Team1_Lager_Elastomer.ids` (Feld `IDS_DATEI`). Spezifikationen: Elastomerlager (ELASTOMERIC), Brücke Baujahr (R-03), Topflager (POT) und Kalottenlager (SPHERICAL). Lager brauchen Lagertyp, Einbaujahr (1950 bis 2026), Lieferant und Modell im Pset `BFH_Minor`. Das Baujahr der Brücke steht in `CH_Bauwerksdaten`.
- Zusatzprüfungen, Stichprobe und Dashboard-Gruppen: `checks/pruefregeln.yaml`.
- Stammdaten-Mapping: `checks/export_mapping.yaml`.

**Bedienung**

1. «Laufzeit → Alle ausführen».
2. In Abschnitt 3 die `.ifc`-Datei vom Desktop wählen (Modellquelle «Upload (Desktop)»). Alternativ Google Drive, lokaler Pfad oder das Lehrmodell `models/Team_1_Bruecke_BFH_Minor.ifc`.
3. Das ZIP `pruefergebnis.zip` wird am Ende heruntergeladen.

**Ausgabe** (Ordner `out/` und ZIP): `pruefbericht.html`, `alle_pruefergebnisse.csv`, `maengelliste.csv`, `maengel.bcf`. Stichprobe, Stammdaten-Vorschau und Dashboard erscheinen nur im Notebook.

**Modellordner leeren:** Der Schalter `MODELLORDNER_LEEREN` (Standard an) löscht nach der Prüfung die hochgeladenen IFC-Dateien. Beim nächsten Lauf fragt Abschnitt 3 wieder nach einem Modell. Gilt nur bei «Upload (Desktop)».

**Testlauf mit dem Lehrmodell (17.11.2026):** 1 IfcBridge und 8 IfcBearing. Die IDS wird direkt geladen. Es gibt 5 durchgefallene Prüfungen bei R-01/R-02 (Lagertyp passt nicht zum PredefinedType ELASTOMERIC), R-03 und die Zusatzprüfungen Z-01 und Z-02 bestehen. Die Spezifikationen für Topf- und Kalottenlager treffen auf keine Bauteile zu, weil alle 8 Lager den PredefinedType ELASTOMERIC haben.

**Offen (IDS):** Die drei Lager-Spezifikationen tragen denselben Namen und denselben Identifier `R-01_R-02`. Im Bericht sind sie deshalb nicht unterscheidbar. Bei Einbaujahr und Baujahr steht in der Restriction `xs:string` statt `xs:integer`.

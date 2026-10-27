# KI-Nutzung

Dieses Dokument hält fest, wo und wie das Team KI-Werkzeuge einsetzt.

| Datum | Werkzeug / Modell | Zweck | Prompt (Kurzfassung) | Ergebnis und eigene Prüfung |
| --- | --- | --- | --- | --- |
| 27.10.2026 | Claude (Anthropic), Claude in Chrome, Modell Claude Sonnet 5.5 | Repository und Grundstruktur anlegen | Folie „Euer Team-Repository auf GitHub“ als Bild; Auftrag: Grundlage dazu in einem neuen Repository unter meinem Account für Team 1 erstellen | Privates Repository bxmid03-hs26-team-1 angelegt. Grundstruktur mit README.md, requirements/, workflow/, checks/, results/positiv und results/negativ, KI_USAGE.md und models/README.md, alle mit Platzhaltern (TODO). Dateistruktur auf GitHub kontrolliert. Inhalt durch Claude eingetragen aber vom Team definiert. |
| 27.10.2026 | Claude (Anthropic), Claude in Chrome, Modell Claude Sonnet 5.5 | Workflow „Übergabe-Check Brücken“ dokumentieren | Swimlane-Diagramm „MVP – Übergabe-Check Brücken: vom BIM-Projekt ins Erhaltungsmanagement“ als Bild; Auftrag: dies im Workflow ergänzen | Ablauf in workflow/README.md als Schrittliste (12 Schritte) mit Korrekturschleife übernommen, zunächst zusätzlich als Mermaid-Diagramm. Darstellung auf GitHub kontrolliert. |
| 27.10.2026 | Claude (Anthropic), Claude in Chrome, Modell Claude Sonnet 5.5 | Kurzfassung des Workflows in der README | Auftrag: den Workflow in gekürzter Form in der README unter „Ausführen“ ab Zeile 20 einfügen | Acht Schritte und ein Satz zur BCF-Korrekturschleife anstelle des Platzhalters eingefügt. Eigene Änderungen am Rest der README blieben erhalten. Inhalt aus dem Workflow abgeleitet, Prüfung durch das Team offen |
| 27.10.2026 | Claude (Anthropic), Claude in Chrome, Modell Claude Sonnet 5.5 | README, requirements, workflow und results nach Mindeststand und Projektfeedback ergänzen | Bild „Im Repository / Mindeststand / Woran erkennbar“ und Projektfeedback-PDF vom 20.10.; Auftrag: Bild ergänzen, alles zu Team 1 aus dem PDF einfügen, bei Unsicherheiten nachfragen | Überblick (Entwurf) und Projektstand in der README, Matrix und Rolle-Lagerinformation in requirements/, Ist-Prozess (offen) in workflow/, results/ mit Raster für GlobalId, Ist-Wert, Regel und Grund. Folieninhalt zusammengefasst und nicht wörtlich übernommen. Entwurfsfelder und alle TODO müssen vom Team geprüft und gefüllt werden |
| 27.10.2026 | Claude (Anthropic), Claude in Chrome, Modell Claude Sonnet 5.5 | Teamordner «MVP-Projekt» sichten und mit dem Repository abgleichen | Auftrag: Ordner prüfen und sagen, was sich auf GitHub ergänzen lässt (der Ordner «Komisches Zeug» wurde ausgeschlossen) | Dateien und Inhalte gesichtet. Die IDS vom 27.10. wurde mit ifctester gegen das Modell geprüft und wählt kein Objekt aus (Ursachen in checks/README.md). Befund vom Team zu bestätigen |
| 27.10.2026 | Claude (Anthropic), Modell Claude Sonnet 5.5, mit ifcopenshell 0.9.0.post1 und ifctester 0.9.0 | Nachweisdaten und Prüfskript erstellen | Auftrag: GitHub ergänzen, keine Dateien hochladen. Daraus: Skript pruefung.py, Lauf auf dem Originalmodell und auf einer lokalen Testkopie mit zwei bewussten Änderungen | Originalmodell 9 von 9 bestanden. Testkopie mit derselben Regel: 2 Lager durchgefallen (Lagertyp «Gleitlager», Einbaujahr entfernt). GlobalIds und Ausgaben stehen in results/. Die Läufe sind mit pruefung.py wiederholbar, die Testkopie liegt nur lokal |
| 27.10.2026 | Claude (Anthropic), Claude in Chrome, Modell Claude Sonnet 5.5 | Texte in requirements, checks, models, results und README ergänzen | Auftrag: GitHub ergänzen, keine Dateien hochladen. Quellen: Projektwahl, MVP.pptx, Teamkarte | Anforderungsmatrix R-01 bis R-03, Prüfungen C-01 bis C-05, Modellangaben, Ergebnisse mit GlobalIds, Setup mit Versionen und Projektstand eingetragen. Rollenzuordnung und Beobachtung zur Plausibilität des Lagertyps sind Entwürfe und vom Team zu bestätigen |
| _TODO: Datum ergänzen_ | Claude Opus 5.5 (laut Vermerk auf der Folie) | Entwurf der verworfenen Idee «Brücken-Zustandsdashboard» (Folie MVP A) | _TODO: Prompt ergänzen_ | Die Folie trägt den Vermerk «Generiert mit Claude Opus 5.5». Die Idee wurde verworfen (siehe README, Projektstand) |



## Regeln im Team

- Jeder KI-Einsatz wird in der Tabelle oben eingetragen.
- KI-Ergebnisse werden vor der Übernahme geprüft und bei Bedarf angepasst.
- Keine vertraulichen oder geschützten Daten in KI-Werkzeuge eingeben.

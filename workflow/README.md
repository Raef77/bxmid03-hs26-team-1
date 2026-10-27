# Workflow

## MVP – Übergabe-Check Brücken: vom BIM-Projekt ins Erhaltungsmanagement

Ablauf der Datenübergabe von der Projektierung (BIM) in das Erhaltungsmanagement.

## Schritte

| Nr. | Rolle | Schritt |
| --- | --- | --- |
| 1 | Erhaltungsmanagement (Empfänger) | Datenbedarf für den Betrieb melden |
| 2 | Auftraggeber / Bauherr | Informationsanforderungen festlegen |
| 3 | Auftraggeber / Bauherr | IDS bereitstellen |
| 4 | Projektverfasser:in (Ingenieurbüro) | MAW erstellen (MAW = Modell ausgeführtes Werk) |
| 5 | Projektverfasser:in (Ingenieurbüro) | IFC einreichen inkl. Selbstprüfung |
| 6 | BIM-Koordination (MVP-Tool) | IDS-Prüfung (ifctester), automatisiert |
| 7 | BIM-Koordination (MVP-Tool) | Entscheid: Daten vollständig? Nein: BCF-Datei an Projektverfasser:in, Mängel korrigieren, erneut einreichen. Ja: weiter zu Schritt 8 |
| 8 | Fachplaner | Werte stichprobenartig prüfen |
| 9 | Fachplaner | Entscheid: plausibel? Nein: BCF-Datei an Projektverfasser:in, Mängel korrigieren, erneut einreichen. Ja: weiter zu Schritt 10 |
| 10 | BIM-Koordination (MVP-Tool) | Export Stammdaten (CSV/Excel) und Prüfbericht, automatisiert |
| 11 | Auftraggeber / Bauherr | Daten prüfen und freigeben (Abnahme). Bei Mängeln: BCF-Datei an Projektverfasser:in |
| 12 | Erhaltungsmanagement (Empfänger) | Übernahme ins Erhaltungssystem (z. B. KUBA) |

## Korrekturschleife

Bei jedem Entscheid mit „Nein“ (Vollständigkeit, Plausibilität, Abnahme) wird eine BCF-Datei erstellt. Die Projektverfasser:in korrigiert die Mängel und reicht das IFC erneut ein.

## Ist-Prozess (Vorher/Nachher)

Offen: Der Ist-Prozess fehlt noch. Er soll zeigen, wie die Übergabe heute abläuft, und dem Soll-Prozess oben gegenübergestellt werden.

| | Ist (vorher) | Soll (nachher) |
| --- | --- | --- |
| Ablauf der Übergabe | _TODO_ | Schritte 1 bis 12 oben |
| Prüfung der Daten | _TODO_ | IDS-Prüfung (ifctester) und stichprobenartige Plausibilitätsprüfung |
| Rückmeldung bei Mängeln | _TODO_ | BCF-Datei an Projektverfasser:in |
| Übernahme ins Erhaltungssystem | _TODO_ | Export Stammdaten (CSV/Excel) und Prüfbericht, danach Übernahme (z. B. KUBA) |

## Quelle und offene Punkte

- Soll-Prozess: „MVP – Übergabe-Check Brücken“ (Abgabe 19.10.), siehe [Prozess MVP.pdf](Prozess%20MVP.pdf).
- Ist-Prozess bzw. Vorher/Nachher-Vergleich ergänzen.
- Klären, welche Rolle welche Lagerinformation braucht (siehe `requirements/`).

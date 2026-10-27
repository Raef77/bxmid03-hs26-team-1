# bxmid03-hs26-team-1

Team-Repository von **Team 1** (bxmid03, HS26).

## Ziel

Erstellen eines MVP welcher bestehende Brücken prüft und die IDS bei der Bestimmung des Zustandes helfen sollen. 

## Überblick

Quelle: Projektwahl des Teams. Stand der Umsetzung siehe «Projektstand».

| | |
| --- | --- |
| **Problem** | Bei der Übergabe einer Brücke aus dem BIM-Projekt ins Erhaltungsmanagement fehlen betriebsrelevante Angaben (Baujahr, Lagertyp, Einbaujahr) oder sie sind uneinheitlich. Ohne Prüfung werden sie von Hand übertragen. |
| **Zielgruppe** | Erhaltungsmanagement als Empfänger der Daten, BIM-Koordination und Fachplaner als Prüfende, Auftraggeber / Bauherr für die Abnahme, Projektverfasser:in als Lieferant. |
| **Scope** | Bauwerk und Lager der Brücke (Brückenmodell mit acht Lagern). |
| **Input** | As-built-IFC 4.3 (Modell ausgeführtes Werk), IDS (YAML → XML) und Export-Mapping (YAML). |
| **Verarbeitung** | Automatisiert: IDS-Prüfung des IFC mit ifcopenshell/ifctester. Dazu stichprobenartige Plausibilitätsprüfung durch den Fachplaner. |
| **Output** | HTML-Prüfbericht, Mängelliste (CSV/BCF) an die Projektverfasser:in, Stammdaten-Export (CSV/Excel) und Dashboard «Vollständigkeit in %». Danach Übernahme ins Erhaltungssystem (z. B. KUBA). |

## Setup

Nachfolgende Programme oder Webseiten werden benötigt:
-  IFC Viewer (z.B. https://www.ifclite.com/)
-  IDS Editor (z.B. https://www.idsedit.com/ oder https://www.idslight.com/)

1. Repository klonen: `git clone https://github.com/Raef77/bxmid03-hs26-team-1.git`
2. Python 3.13 installieren (damit getestet).
3. Pakete installieren: `pip install ifcopenshell==0.9.0.post1 ifctester==0.9.0`
4. Das IFC-Modell lokal ablegen. Es liegt im Teamordner und nicht im Repository (siehe `models/README.md`).

## Ausführen

Kurzfassung des Ablaufs (Details in `workflow/README.md`):

1. Erhaltungsmanagement meldet den Datenbedarf für den Betrieb.
2. Auftraggeber / Bauherr legt die Informationsanforderungen fest und stellt das IDS bereit.
3. Projektverfasser:in erstellt das MAW (Modell ausgeführtes Werk) und reicht das IFC inkl. Selbstprüfung ein.
4. BIM-Koordination prüft das IFC automatisch gegen das IDS (ifctester).
5. Fachplaner prüft die Werte stichprobenartig auf Plausibilität.
6. BIM-Koordination exportiert Stammdaten (CSV/Excel) und Prüfbericht.
7. Auftraggeber / Bauherr prüft und gibt die Daten frei (Abnahme).
8. Erhaltungsmanagement übernimmt die Daten ins Erhaltungssystem (z. B. KUBA).

Bei „Nein“ in Schritt 4, 5 oder 7 geht eine BCF-Datei an die Projektverfasser:in, die Mängel werden korrigiert und das IFC erneut eingereicht.

Prüfung starten (Skript und Details in `checks/README.md`):

```
python pruefung.py modell.ifc
```

Ergebnisse mit GlobalIds stehen in `results/`.

## Projektstand

Stand: 27.10.2026 (Projektfeedback vom 20.10.2026 eingearbeitet).

**Vorhanden**

- Konkreter Nutzen: Übergabe der Brückendaten ins Erhaltungsmanagement.
- Soll-Prozess mit IDS-Prüfung, Ja/Nein-Entscheiden und BCF-Rücklauf (siehe `workflow/`).
- Anforderungsmatrix R-01 bis R-03 für Baujahr, Lagertyp und Einbaujahr (siehe `requirements/`).
- IDS-Prüfung als Skript, positiver und negativer Fall mit echten GlobalIds (siehe `checks/` und `results/`).

**Noch offen**

- Ist-Prozess bzw. Vorher/Nachher-Vergleich (`workflow/`).
- Welche Rolle welche Lagerinformation braucht: Entwurf vorhanden, vom Team zu bestätigen (`requirements/`).
- Prüflogik «Einbaujahr ≤ aktuelles Jahr» und Stichprobe zur Plausibilität des Lagertyps (`checks/`).
- Entscheid, welche IDS-Regel leitend ist: CH_Lager oder Hersteller-Properties (`checks/`).
- Outputs: HTML-Prüfbericht, BCF-/CSV-Mängelliste, Stammdaten-Export und Dashboard «Vollständigkeit in %».

**Erweiterung, falls Zeit bleibt**

- Ersatzplanung der Verschleissteile (Lager) aus Einbaujahr und Nutzungsdauer.

**Verworfene Ideen**

- Brücken-Zustandsdashboard: Mit KUBA gibt es dafür bereits ein etabliertes Tool, der Praxisnutzen wäre gering.
- Monitoring-Dashboard (Sensoren): Es gibt weder Messdaten noch Sensoren im Modell.
- Instandsetzungskosten: Zu ähnlich zum Kostenbeispiel der Vorlage, Einheitspreise sind schwer belegbar.

## Struktur

| Ordner / Datei | Inhalt |
| --- | --- |
| `requirements/` | Anforderungen |
| `workflow/` | Beschreibung des Ablaufs |
| `checks/` | Prüfungen / Checks |
| `results/` | Ergebnisse: positiver und negativer Fall |
| `models/README.md` | Hinweise zu den Modellen (statt geschützter Modelle) |
| `KI_USAGE.md` | Dokumentation des KI-Einsatzes |

## Team

_TODO: Teammitglieder und Rollen eintragen._

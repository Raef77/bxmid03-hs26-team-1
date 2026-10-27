# bxmid03-hs26-team-1

Team-Repository von **Team 1** (bxmid03, HS26).

## Ziel

Erstellen eines MVP welcher bestehende Brücken prüft und die IDS bei der Bestimmung des Zustandes helfen sollen. 

## Überblick

_Entwurf, vom Team zu bestätigen._

| | |
| --- | --- |
| **Problem** | Bei der Übergabe einer Brücke aus dem BIM-Projekt ins Erhaltungsmanagement fehlen Daten oder sie lassen sich nicht prüfen. |
| **Zielgruppe** | Erhaltungsmanagement als Empfänger der Daten, BIM-Koordination und Fachplaner als Prüfende, Auftraggeber / Bauherr für die Abnahme. |
| **Scope** | Bauwerk und Lager der Brücke (Brückenmodell v2 mit acht Lagern). |
| **Input** | IFC-Modell der Brücke (MAW, Modell ausgeführtes Werk) und IDS mit den Informationsanforderungen. |
| **Verarbeitung** | IDS-Prüfung mit ifctester, Entscheid „Daten vollständig?“, stichprobenartige Plausibilitätsprüfung durch den Fachplaner. |
| **Output** | Prüfbericht und Export der Stammdaten (CSV/Excel). Bei Mängeln eine BCF-Datei zur Korrektur. Danach Übernahme ins Erhaltungssystem (z. B. KUBA). |

## Setup

Nachfolgende Programme oder Webseiten werden benötigt:
-  IFC Viewer (z.B. https://www.ifclite.com/)
-  IDS Editor (z.B. https://www.idsedit.com/ oder https://www.idslight.com/)

1. Repository klonen: `git clone https://github.com/Raef77/bxmid03-hs26-team-1.git`
2. _TODO: exakte Schritte mit Versionen (ifctester, IFC-Viewer, IDS-Editor) ergänzen, damit der Lauf wiederholbar ist_

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

## Projektstand

Stand: Projektfeedback vom 20.10.2026.

**Vorhanden**

- Konkreter Nutzen: Übergabe der Brückendaten ins Erhaltungsmanagement.
- Soll-Prozess mit IDS-Prüfung, Ja/Nein-Entscheiden und BCF-Rücklauf (Abgabe 19.10., siehe `workflow/`).
- Brückenmodell v2 mit acht Lagern liegt bereit.

**Noch offen**

- Ist-Prozess bzw. Vorher/Nachher-Vergleich fehlt (`workflow/`).
- Welche Rolle braucht welche Lagerinformation? (`requirements/`)
- Matrix des Stahlstützen-Beispiels auf die Brücke abstimmen (`requirements/`).

**Nachzuweisen**

- Drei reale Datenpfade mit echten GlobalIds im Brückenmodell (`results/`).

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

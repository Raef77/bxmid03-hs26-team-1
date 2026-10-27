# Workflow

## MVP – Übergabe-Check Brücken: vom BIM-Projekt ins Erhaltungsmanagement

Ablauf der Datenübergabe von der Projektierung (BIM) in das Erhaltungsmanagement. Orange markierte Schritte sind automatisiert (MVP-Tool).

```mermaid
flowchart TD
  subgraph EM["Erhaltungsmanagement (Empfänger)"]
    S(("Start")) --> A1["Datenbedarf für den Betrieb melden"]
    Z1["Übernahme ins Erhaltungssystem (z. B. KUBA)"] --> E(("Ende"))
  end
  subgraph AG["Auftraggeber / Bauherr"]
    A2["Informationsanforderungen festlegen"] --> A3["IDS bereitstellen"]
    A9["Daten prüfen und freigeben (Abnahme)"]
  end
  subgraph PV["Projektverfasser:in (Ingenieurbüro)"]
    P1["MAW erstellen (MAW = Modell ausgeführtes Werk)"] --> P2["IFC einreichen inkl. Selbstprüfung"]
    P3["Mängel korrigieren"]
  end
  subgraph BK["BIM-Koordination (MVP-Tool)"]
    B1["IDS-Prüfung (ifctester)"] --> B2{"Daten vollständig?"}
    B3["Export Stammdaten (CSV/Excel) + Prüfbericht"]
  end
  subgraph FP["Fachplaner"]
    F1["Werte stichprobenartig prüfen"] --> F2{"Plausibel?"}
  end

  A1 --> A2
  A3 --> P1
  P2 --> B1
  B2 -- "Nein → BCF-Datei" --> P3
  B2 -- "Ja" --> F1
  F2 -- "Nein → BCF-Datei" --> P3
  F2 -- "Ja" --> B3
  P3 -. "erneut einreichen" .-> P2
  B3 --> A9
  A9 -. "Nein → BCF-Datei" .-> P3
  A9 --> Z1

  classDef auto fill:#fde3c8,stroke:#d9822b,color:#000;
  class B1,B3 auto;
```

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

# ADR 0002: Punkte-System als Zählregel

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** ADR 0001 macht die Zählregel zur Datenmodell-Entscheidung. Die
  rohe Regel „30 verschiedene Pflanzen pro Woche" hat bekannte Streitfälle:
  Ein Teelöffel getrockneter Oregano soll nicht so viel zählen wie ein Teller
  Linsen (Gewürz-Loophole), und Nutzer, die das Konzept aus Spector/ZOE
  kennen, erwarten die kanonische Gewichtung.

## Entscheidung

Der Tracker zählt **Pflanzenpunkte**:

- Jede **verschiedene Hauptpflanze** (Gemüse, Obst, Nüsse, Samen,
  Hülsenfrüchte, (Vollkorn-)Getreide) = **1 Punkt**
- Jedes verschiedene **Kraut / Gewürz** = **¼ Punkt**
- **Wochenziel = 30 Punkte**

Jede Pflanze zählt **einmal pro Woche** — Wiederholungen geben keine
zusätzlichen Punkte („verschieden" ist der Kern des Konzepts).

## Konsequenzen

- Das Datenmodell braucht pro Pflanze: **Kategorie** und **Punktwert** (1 bzw.
  ¼) — Gewichtung ist ab Tag 1 im Schema, nicht nachrüstbar.
- Die UI muss **Viertelpunkte** sauber darstellen (Fortschrittsbalken statt
  reiner Ganzzahl-Anzeige).
- Das Logging braucht **Wochen-Deduplikation**: bereits geloggte Pflanzen der
  laufenden Woche werden als „gezählt" markiert.

## Offen (nächste Fragen)

- **Granularität:** Was heißt „verschieden"? (rote vs. gelbe Paprika;
  Brokkoli vs. Grünkohl)
- **Kategorie-Umfang:** Zählen Kaffee, Olivenöl, dunkle Schokolade etc.?

## Verworfene Alternativen

- **Strikt 1 Pflanze = 1 Punkt:** Gewürz-Loophole, nicht erwartungskonform.
- **Nur Hauptpflanzen zählen:** puristisch, macht 30/Woche kaum erreichbar.

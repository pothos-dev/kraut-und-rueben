# ADR 0003: Granularität — Farben und Sorten zählen separat

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** ADR 0002 führt das Punkte-System ein und lässt offen, was
  „verschieden" konkret bedeutet. Diese Definition steuert die
  Wochen-Deduplikation, die Größe der Pflanzen-Taxonomie und die
  Rezept-Metadaten.

## Entscheidung

„Verschieden" wird auf **Sorten-/Farbebene** gezählt: Rote und gelbe Paprika
sind zwei Pflanzen, Grünkohl und Brokkoli sind zwei Pflanzen, verschiedene
Apfelsorten zählen separat. Begründung: unterschiedliche Farben/Sorten
liefern unterschiedliche Phytonährstoffe, und die 30-Punkte-Woche bleibt
realistisch erreichbar.

## Konsequenzen

- Die **Taxonomie ist hierarchisch**: Pflanze (z. B. Paprika) → Sorten bzw.
  Farbvarianten (rot, gelb, grün). Die Wochen-Deduplikation läuft auf
  **Sorten-Ebene**.
- Die Taxonomie wird deutlich größer (Sorten-Listen pro Pflanze) —
  erhöhter Pflegeaufwand bei der Content-Erstellung.
- Die **Logging-UX** muss die Sorten-Auswahl anbieten. Der Umgang mit
  generischen Logs („Paprika" ohne Farbangabe) ist bei der Logging-UX zu
  klären.
- **Rezept-Metadaten** müssen Zutaten bis auf Sorten-Ebene auflösen, sonst
  verschenkt ein Rezept Punkte.

## Verworfene Alternativen

- **Lebensmittel-Ebene ohne Farb-Splitting** (in der Session empfohlene
  Variante): kleinere Taxonomie, aber weniger erreichbare Punkte; vom
  Entscheider zugunsten der Phytonährstoff-Logik verworfen.
- **Botanische Arten-Ebene:** würde die Kohlfamilie (*Brassica oleracea*) zu
  1 Punkt kollabieren lassen — alltagsfremd, Ziel unerreichbar.

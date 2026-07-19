# GLOSSARY

Zentrale Begriffe des Produkts und dieser Planning Session. Wird laufend
gepflegt, sobald neue Domain-Begriffe auftauchen oder Entscheidungen fallen.

## 30-Pflanzen-Woche

Ernährungskonzept, auf dem das ganze Produkt aufbaut: Wer pro Woche mindestens
**30 verschiedene Pflanzen(arten)** isst, fördert die Vielfalt seines
Darmmikrobioms (populär geworden u. a. durch das American Gut Project / ZOE).
Als „Pflanzen" zählen dabei u. a. Gemüse, Obst, Nüsse, Samen, Hülsenfrüchte,
(Vollkorn-)Getreide, Kräuter und Gewürze — Vielfalt zählt, nicht Menge.

## Wochen-Tracker

Die **Kernschleife** des Produkts (siehe ADR 0001): Nutzer loggen die über
die Woche gegessenen verschiedenen Pflanzen und sehen ihren Fortschritt
Richtung 30.

## Tracker-Woche

Zählfenster des Trackers (ADR 0008, 0009): eine **ISO-Kalenderwoche,
Montag 00:00 UTC bis Sonntag 24:00 UTC**. Am Montag (UTC) resetten Punkte
und Deduplikation. Das Datenmodell bleibt für spätere Wochen-Definitionen
erweiterbar (`week_start` explizit als UTC-Datum).

## Rezepte-Seite

Rezept-Katalog als **untergeordnetes Modul** des Wochen-Trackers (ADR 0001):
Jedes Rezept weiß, welche und wie viele verschiedene Pflanzen es liefert, und
dient Nutzern als Inspiration bzw. „Lückenfüller" für noch fehlende Pflanzen
der laufenden Woche.

## Pflanzenpunkt

Zähleinheit des Wochen-Trackers (ADR 0002): Jede **verschiedene
Hauptpflanze** (Gemüse, Obst, Nüsse, Samen, Hülsenfrüchte,
(Vollkorn-)Getreide) = **1 Punkt**; jedes verschiedene **Kraut/Gewürz** =
**¼ Punkt**. Wochenziel: **30 Punkte**. Jede Pflanze zählt einmal pro Woche.
Zusätzlich zählen Kaffee und dunkle Schokolade (≥ 70 % Kakao) je 1 Punkt
(ADR 0004).

## Sorte

Granularitäts-Ebene des Trackers (ADR 0003): Farben und Sorten einer Pflanze
zählen **separat** (rote ≠ gelbe Paprika; Grünkohl ≠ Brokkoli). Die
Taxonomie ist hierarchisch: Pflanze → Sorten; die Wochen-Deduplikation läuft
auf Sorten-Ebene.

## Ballaststoff-Test

Daumenregel für Kategorie-Grenzfälle (ADR 0004): Eine Kategorie zählt, wenn
sie nennenswert Ballaststoffe/Polyphenole der Pflanze liefert — nicht, wenn
sie nur Extrakt ist. Danach zählen Kaffee und dunkle Schokolade (≥ 70 %)
je 1 Punkt; Öle, Säfte, Wein und Tee zählen nicht.

## Tech-Stack (v1)

- **SvelteKit** — Full-Stack-Web-Framework (UI, SSR für Rezepte, API-Routen).
- **Supabase** — Backend: Postgres, Auth, Row Level Security (ADR 0005 + 0007).

## Offene Begriffsfragen

- **Generischer Log:** Was passiert bei „Paprika“ ohne Farbangabe? (zu
  klären bei der Logging-UX)

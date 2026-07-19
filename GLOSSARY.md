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

## Offene Begriffsfragen

- **Granularität:** Was heißt „verschieden"? (rote vs. gelbe Paprika;
  Brokkoli vs. Grünkohl — beide botanisch *Brassica oleracea*)
- **Kategorie-Umfang:** Zählen Kaffee, Olivenöl, dunkle Schokolade o. Ä.?

# ADR 0008: Wochengrenze — ISO-Kalenderwoche (Mo–So)

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** Der Wochen-Tracker (ADR 0001) und das Punkte-System (ADR 0002)
  brauchen eine konkrete Definition von „Woche" für Deduplikation, Reset,
  Streaks und das Datenbank-Schema (`week_id` / `week_start`). Der Tech-Stack
  (ADR 0007) steht; die Wochengrenze steuert Queries und UI.

## Entscheidung

Eine Tracker-Woche ist eine **ISO-Kalenderwoche: Montag 00:00 bis Sonntag
24:00**. Am Montag beginnt eine neue Zählung; geloggte Sorten der Vorwoche
zählen nicht in die neue Woche.

**Erweiterbarkeit:** Das Datenmodell soll einen Wechsel der Wochendefinition
(z. B. nutzerdefinierter Starttag, rollierendes Fenster) **nicht verbauen** —
`week_start` als explizites Datumsfeld statt hardcodierter Kalenderlogik in
jedem Query, und keine Annahmen „Woche = immer Mo–So" in persistierten
Aggregaten jenseits von `week_start` + `week_end`. v1-Verhalten bleibt fest
ISO Mo–So.

## Konsequenzen

- Jeder Pflanzen-Log trägt eine **`week_start`-Referenz** (Montag der
  ISO-Woche), berechnet aus Log-Zeitpunkt + User-Timezone.
- **Timezone ist Pflichtfeld** der Wochenlogik (nächste Entscheidung): ohne
  sie ist „Montag 00:00" undefiniert.
- Streaks = aufeinanderfolgende ISO-Wochen mit erreichtem 30-Punkte-Ziel.
- Wochenvergleich und Historie-UI gruppieren nach `week_start`.
- Montags braucht die UI ein klares „Neue Woche"-Signal (Fortschritt auf 0,
  Vorwoche archiviert sichtbar).

## Verworfene Alternativen

- **Rollierende 7 Tage:** kein harter Reset, aber Streaks/Historie unschärfer
  und weiter weg vom Begriff „30-Pflanzen-Woche".
- **Kalenderwoche mit wählbarem Starttag in v1:** flexible UX, aber mehr
  Settings- und Edge-Case-Last; bewusst als spätere Erweiterung offengehalten,
  nicht als v1-Scope.

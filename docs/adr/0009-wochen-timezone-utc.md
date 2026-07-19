# ADR 0009: Wochen-Timezone — fest UTC

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** ADR 0008 definiert die Tracker-Woche als ISO-Kalenderwoche
  (Mo–So). „Montag 00:00" ist ohne Timezone undefiniert. Offen war, ob die
  Grenze fest in einer EU-Zone, pro User oder in UTC liegt.

## Entscheidung

Die Wochengrenze liegt **fest in UTC**: Eine Tracker-Woche läuft von
**Montag 00:00 UTC bis Sonntag 24:00 UTC**. `week_start` wird server-seitig
ausschließlich in UTC berechnet; Clients liefern Timestamps als UTC (bzw.
ISO-8601 mit Offset, die server-seitig normalisiert werden).

## Konsequenzen

- **Schema bleibt einfach:** kein Timezone-Feld am User-Profil in v1; alle
  Wochen-Aggregationen und Deduplikations-Keys teilen dieselbe Grenze.
- **UI-Klarheit ist Pflicht:** In DACH endet/beginnt die Woche lokal
  Sonntag 01:00/02:00 (MEZ/MESZ). Die App muss die Wochengrenze transparent
  kommunizieren (z. B. „Woche endet Sonntag 02:00" bzw. relative Anzeige),
  sonst wirkt der Reset willkürlich.
- Reisen und Wohnortwechsel ändern die Zählung nicht — praktisch und
  konfliktfrei, wenn auch nicht am Lebensmittelpunkt des Users klebend.
- Spätere Migration auf User-TZ bleibt möglich (analog ADR 0008
  Erweiterbarkeit), solange `week_start` als explizites UTC-Datum
  gespeichert wird und nicht als abgeleitete Anzeigegröße.

## Verworfene Alternativen

- **Fest `Europe/Berlin`** (in der Session empfohlen): alltagsnäher für DACH,
  aber implizite Sommerzeit-Kante und weniger „technisch neutral"; vom
  Entscheider zugunsten von UTC verworfen.
- **Timezone pro User:** korrekt weltweit, aber Onboarding-, Reise- und
  Wechsel-Edge-Cases in v1 unverhältnismäßig.

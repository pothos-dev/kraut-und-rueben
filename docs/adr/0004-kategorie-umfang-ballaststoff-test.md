# ADR 0004: Kategorie-Umfang — Ballaststoff-Test, Kaffee & dunkle Schokolade zählen

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** ADR 0002/0003 lassen offen, welche Kategorien jenseits ganzer
  Pflanzenlebensmittel Punkte geben. Streitfälle: Kaffee, dunkle Schokolade,
  Olivenöl, Säfte, Tee, Wein. Ohne klare Regel droht entweder das
  Nutella-Loophole (Glaubwürdigkeitsverlust) oder ein unerreichbares
  Wochenziel.

## Entscheidung

**Mittelweg entlang des Kanons** (Spector/ZOE): **Kaffee** und **dunkle
Schokolade (≥ 70 % Kakao)** zählen je **1 Punkt**. Öle, Säfte, Wein und Tee
zählen **nicht**.

Als Daumenregel für künftige Grenzfälle gilt der **Ballaststoff-Test**:
Eine Kategorie zählt, wenn sie nennenswert Ballaststoffe/Polyphenole der
Pflanze liefert — nicht, wenn sie nur Extrakt ist.

## Konsequenzen

- Die Taxonomie erhält die Einträge „Kaffee" und „Dunkle Schokolade
  (≥ 70 %)" — **ohne Sorten-Splitting** (Kaffee = 1 Pflanze, egal welche
  Röstung/Herkunft; Ausnahme zu ADR 0003, da hier keine relevante
  Sorten-Vielfalt im Alltag erfassbar ist).
- **Rezept-Metadaten** dürfen Schokoladen-Zutaten nur mappen, wenn der
  Kakao-Anteil ≥ 70 % angegeben ist.
- Der Ballaststoff-Test wird in der App kommuniziert, damit Nutzer die
  Regel nachvollziehen können (Transparenz schafft Vertrauen in die
  Punktevergabe).

## Verworfene Alternativen

- **Breit** (auch Öle, Kräutertees etc. zählen): verwässert das Konzept mit
  Extrakten, weicht vom Kanon ab.
- **Streng** (Kaffee/Schokolade zählen nicht): sauberste Botschaft, aber
  unerwartet für Spector-affine Nutzer und 30/Woche wird schwerer.

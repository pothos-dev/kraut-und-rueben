# ADR 0001: Wochen-Tracker ist die Kernschleife

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** Die Ausgangsidee „Rezepte-Seite auf Basis der 30-Pflanzen-Woche"
  war doppeldeutig: (A) reiner Rezept-Katalog, der die 30er-Regel nur
  thematisiert, oder (B) ein Tracker, der die Woche des Nutzers zählt und
  Rezepte als Werkzeug einsetzt. Die Entscheidung legt Datenmodell, Persistenz
  und Scope der v1 fest.

## Entscheidung

Der **Wochen-Tracker ist die Kernschleife** des Produkts. Nutzer loggen die
über die Woche gegessenen verschiedenen Pflanzen und sehen ihren Fortschritt
Richtung 30. Rezepte sind dem Tracker untergeordnet: Sie dienen als
Inspiration und „Lückenfüller", um noch fehlende Pflanzen zu finden.

## Konsequenzen

- **Persistenz wird Pflicht** — der Wochenzustand muss über Sessions hinweg
  erhalten bleiben (Speicher-/Account-Frage muss als Nächstes geklärt werden).
- **Zählregeln werden Teil des Domain-Modells** — was als „eine Pflanze"
  zählt und mit welchem Wert, ist keine redaktionelle, sondern eine
  Datenmodell-Entscheidung.
- **Rezept-Katalog bleibt Pflichtmodul**, aber untergeordnet: Jedes Rezept
  muss wissen, welche (und wie viele verschiedene) Pflanzen es liefert.

## Verworfene Alternativen

- **Katalog zuerst, Tracker als Phase 2** (in der Session empfohlene Option):
  vom Entscheider verworfen zugunsten des vollen Produktversprechens in v1.
- **Nur Katalog, nie Tracking:** verworfen — lässt das Versprechen „schaff
  deine 30" vollständig beim Nutzer.

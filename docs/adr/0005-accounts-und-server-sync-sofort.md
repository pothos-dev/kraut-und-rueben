# ADR 0005: Accounts und Server-Sync von Anfang an

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** ADR 0001 macht Persistenz zur Pflicht. Offen war, ob der
  Wochenzustand lokal auf dem Gerät oder auf einem Server mit Accounts lebt.
  Für einen Tracker ist die Historie (Streaks, Wochenvergleich) ein zentraler
  Motivationshebel — und Gerätewechsel/Browser-Reset würden lokale Daten
  zerstören.

## Entscheidung

**Accounts mit Server-Sync sind Teil der v1.** Der Wochenzustand und die
gesamte Historie liegen serverseitig und sind auf jedem Gerät verfügbar.

## Konsequenzen

- **v1-Scope wächst:** Backend/API, Datenbank und Auth werden Pflicht.
- **DSGVO-Pflichten ab Tag 1:** Datenschutzerklärung, Löschkonzept,
  EU-Hosting bevorzugt, ggf. Auftragsverarbeitungsvertrag mit dem Hoster.
  Es werden gesundheitsnahe Daten verarbeitet → Datensparsamkeit gilt:
  nur Logs + Account-Daten, keine zusätzlichen Profile.
- **Offline-Nutzung ist kein v1-Ziel** (bewusster Trade-off gegenüber
  local-first); kurze Verbindungsabbrüche werden über Retry/Queue abgefedert,
  nicht über ein Offline-Modell.
- Die Account-/Login-UX (z. B. passwortlos per Magic Link vs. klassisch)
  ist eine eigene Folgeentscheidung.

## Verworfene Alternativen

- **Local-first, sync-fähig designt** (in der Session empfohlen): kleinere
  v1 und DSGVO-leicht, aber kein Cross-Device und Datenverlust-Risiko; vom
  Entscheider zugunsten des Sync-Versprechens verworfen.
- **Rein lokal, Sync nie geplant:** inkompatibel mit dem Sync-Versprechen.

# ADR 0010: Auth — OAuth (Google, Apple optional)

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** ADR 0005 verlangt Accounts und Server-Sync ab v1; ADR 0007
  setzt Supabase Auth. Offen war der konkrete Anmeldeweg (Magic Link,
  Passwort, OAuth).

## Entscheidung

v1-Auth läuft über **OAuth**. **Google** ist der verpflichtende Provider.
**Apple** als weiterer Provider ist bewusst offengehalten („ggf.") und wird
als eigene Teilentscheidung geklärt — nicht stillschweigend zugesagt und
nicht stillschweigend gestrichen.

Kein Passwort-Flow und kein Magic-Link in v1.

## Konsequenzen

- **Supabase Auth** mit Google-Provider; Client-Flow über SvelteKit
  (PKCE / `@supabase/ssr`).
- **Datensparsamkeit (ADR 0005):** nur die vom Provider gelieferte
  stabile User-ID + E-Mail (und ggf. Anzeigename) speichern — kein
  ausuferndes Profil.
- **Drittland / DSGVO:** Google als Identity-Provider erfordert transparente
  Information in der Datenschutzerklärung und Prüfung der Supabase-/Google-
  Auftragsverarbeitung; EU-Region des Supabase-Projekts bleibt Pflichtkandidat
  (ADR 0007).
- **Account-Löschung** muss den Supabase-User und alle Essens-Logs entfernen
  (DSGVO-Löschkonzept).
- Lange Sessions / Refresh sind wichtig für die Küchen-UX (wiederholtes
  OAuth-Redirect während des Kochens vermeiden).
- **Apple Sign-In** hat eigene Domänen-/Setup-Anforderungen und ist auf iOS-
  Safari-Nutzern relevant — Follow-up-Entscheidung.

## Verworfene Alternativen

- **Nur Magic Link** (in der Session empfohlen): datensparsam und einfach,
  aber Mail-App-Wechsel am Herd; vom Entscheider zugunsten von OAuth verworfen.
- **E-Mail + Passwort:** Reset-Surface und Passwort-Policy ohne UX-Gewinn
  gegenüber OAuth.
- **Magic Link + Google:** zwei Pfade in v1, mehr Test- und Erklärlast.

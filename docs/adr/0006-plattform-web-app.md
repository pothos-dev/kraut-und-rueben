# ADR 0006: Plattform — Web-App

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** Mit ADR 0001 (Tracker) und ADR 0005 (Server-Sync) steht die
  Grundarchitektur; offen war die Auslieferungsplattform (Web vs. native
  Mobile-Apps).

## Entscheidung

Das Produkt ist eine **Web-App** (browserbasiert, responsiv). Native
iOS-/Android-Apps werden nicht gebaut.

## Konsequenzen

- **Mobile-first gedacht:** Ein Food-Tracker wird in der Küche benutzt —
  die Logging-UX muss auf dem Smartphone exzellent sein, obwohl es eine
  Browser-App ist.
- **SEO zählt:** Die Rezepte-Seite lebt von Suchmaschinen-Traffic →
  serverseitig renderbare Rezeptseiten sind Anforderung an den Tech-Stack.
- **PWA-Aufrüstung** (installierbar, Homescreen-Icon, Push-Erinnerungen)
  bleibt als spätere Option offen und ist bewusst kein v1-Scope.

## Verworfene Alternativen

- **Native Apps / Cross-Platform (z. B. React Native, Flutter):** zwei
  Plattformen bzw. zusätzlicher Stack für eine v1 ohne Store-Mehrwert —
  Sync läuft ohnehin über den Server.

# ADR 0007: Tech-Stack — SvelteKit + Supabase

- **Status:** Angenommen
- **Datum:** 2026-07-19
- **Kontext:** ADR 0005 verpflichtet zu Accounts und Server-Sync ab v1;
  ADR 0006 legt die Web-App fest und fordert serverseitig renderbare
  Rezeptseiten (SEO). Offen war der konkrete Stack für Frontend, Backend,
  Auth und Datenbank.

## Entscheidung

**SvelteKit** als Full-Stack-Web-Framework, **Supabase** als Backend-Plattform
(Postgres, Auth, Row Level Security).

- **SvelteKit** liefert SSR/SSG für indexierbare Rezeptseiten, mobile-first
  UI und API-Routen im selben Repo.
- **Supabase** liefert Postgres (Wochenzustand, Historie, Taxonomie,
  Rezept-Metadaten), Auth (Accounts) und RLS als serverseitige
  Zugriffskontrolle — passend zu „Accounts + Sync ab Tag 1".

## Konsequenzen

- **EU-Region** für das Supabase-Projekt ist Pflichtkandidat (ADR 0005:
  EU-Hosting bevorzugt, gesundheitsnahe Essens-Logs). Konkrete Region und
  Hosting der SvelteKit-App (z. B. Vercel, Cloudflare, Node-Host in der EU)
  sind Folgeentscheidungen.
- Das **Datenmodell lebt in Postgres**; Schema-Migrationen (z. B. via
  Supabase SQL / migrations) sind Teil des Dev-Workflows.
- **RLS-Policies** pro Tabelle sind v1-Pflicht — jeder Log ist nutzergebunden.
- SvelteKit spricht Supabase sowohl server-seitig (Service- oder User-Context
  in `+page.server.ts` / hooks) als auch client-seitig an; die genaue
  Auth-Flow-Gestalt (Magic Link, OAuth, Passwort) bleibt offen.
- Vendor-Bindung an Supabase wird akzeptiert; ein Wechsel hieße vor allem
  Auth + Storage-Adapter tauschen, das Schema bleibt portables Postgres.

## Verworfene Alternativen

- **Next.js + Supabase / Firebase / eigenes Node-API:** vergleichbar
  tragfähig, aber nicht die vom Entscheider gesetzte Präferenz.
- **SvelteKit + eigene Postgres/Auth-Infrastruktur:** mehr Ops-Last in v1
  ohne Nutzen gegenüber Supabase.
- **Local-first-Stack (z. B. RXDB/SQLite + später Sync):** widerspricht
  ADR 0005.

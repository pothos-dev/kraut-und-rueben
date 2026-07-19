# Glossary

Domain vocabulary for kraut-und-rueben. Terms are added as they are
defined during planning.

## Terms

- **Shopping List** — the core domain object of the app: a named,
  ordered collection of List Items a user intends to buy. (Ownership,
  multi-list rules, and extra fields still to be decided.)
- **List Item** — a single entry on a Shopping List. Minimal shape
  (ADR 0002): free-text `text`, boolean `checked`, and `position`
  within the list. No quantity, unit, category, or product link in v1.

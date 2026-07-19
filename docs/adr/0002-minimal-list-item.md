# ADR 0002: Minimal List Item shape

- Status: Accepted
- Date: 2026-07-19

## Context

The core domain objects of kraut-und-rueben are Shopping List and List
Item. The shape of List Item is the center of the data model: it drives
UI density, persistence, and whether we need supporting entities
(units, categories, product catalog) in v1.

Options considered ranged from a single free-text line up to
catalog-linked products.

## Decision

A **List Item** is minimal:

- `text` — free-text description of what to buy
- `checked` — whether the item has been picked up
- `position` — order within its Shopping List

No quantity, unit, category, notes, or product reference in v1.
Structure can be layered on later without changing the app's identity.

## Consequences

- Shopping List stays a thin container (name + ordered items) for now.
- No Unit, Category, or Product entities are required for the first
  cut of the model.
- UI is a simple checklist; parsing quantities out of free text is out
  of scope unless revisited.
- Future ADRs may widen List Item; migrations should assume additive
  fields.

# ADR 0001: Build a new standalone app in this repository

- Status: Accepted
- Date: 2026-07-19

## Context

The feature idea "add a shopping list feature" arrived with an empty
repository — no host application, no code, no docs. The first
load-bearing decision was what the feature would live inside.

## Decision

Build a **new, standalone shopping-list application** from scratch in
this repository (`kraut-und-rueben`). It is not a feature of an
existing product and no external codebase will be imported.

## Consequences

- All architecture, domain-model, and tech-stack decisions are
  greenfield; there are no legacy constraints to accommodate.
- This repo holds both the planning artifacts (glossary, ADRs) and,
  eventually, the application code.

---
title: Planner App
summary: A digital bullet journal for quarterly goals, monthly habits, weekly goals, and journaling, with a C# API and a React front end.
stack: ["C#", ".NET", "React", "TypeScript", "PostgreSQL", "Vault", "Docker"]
order: 2
---

## What it is

A digital bullet journal. Like a paper bujo, it follows how I actually
plan: quarters break down into months, months into weeks, and each level
has its own habits and goals. Day to day, I use it to check off daily and
weekly habits, track weekly goals, and keep a journal. It runs self-hosted
in Docker, and I use it myself.

## The problem

A bullet journal is personal by design. You shape the layout to fit how
you think, and most people prefer pen and paper for exactly that reason. I
wanted that same flexibility, built with the tools I know best. Off-the-shelf
planners each covered part of it, but none fit the way I plan, so I built
my own. It also gives me a real project, with real requirements, for
practicing the architecture and testing techniques I care about.

It's a permanent work in progress. Just like a paper bujo, I keep adding
spreads and changing what's there as my needs change.

## My role

Sole developer: API, database, front end, tests, and deployment.

## Technically interesting

- **Clean Architecture with CQRS.** The API is split into Domain,
  Application, Infrastructure, and Presentation layers. Every use case is a
  MediatR command or query with its own handler, and requests are validated
  with FluentValidation. Domain events record what happened, so side
  effects stay out of the handlers.
- **Hand-written SQL on purpose.** Persistence uses Dapper over PostgreSQL
  with versioned schema and stored-procedure scripts instead of an ORM. The
  queries stay explicit, and the database stays something I understand.
- **BDD at both ends.** The API has Reqnroll functional tests that run
  against an in-memory test host. The UI has Cypress scenarios written in
  Gherkin for habits, weekly goals, journal entries, and login, using a
  stubbed API and a controllable clock.
- **No secrets in config.** Database credentials and JWT settings come from
  HashiCorp Vault at startup.

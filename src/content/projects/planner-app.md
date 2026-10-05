---
title: Planner App
summary: A self-hosted planner for quarterly goals, monthly habits, weekly goals, and journaling, with a C# API and a React front end.
stack: ["C#", ".NET", "React", "TypeScript", "PostgreSQL", "Vault", "Docker"]
order: 2
---

## What it is

A personal planning app built around how I actually plan: quarters break
down into months, months into weeks, and each level has its own habits and
goals. Day to day, I use it to check off daily and weekly habits, track
weekly goals, and keep a journal. It runs self-hosted in Docker, and I use
it myself.

## The problem

Off-the-shelf planners and habit trackers each covered part of what I
wanted, but none followed the quarter → month → week structure I plan in.
Building my own fixed that, and it also gave me a real project, with real
requirements, for practicing the architecture and testing techniques I care
about.

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

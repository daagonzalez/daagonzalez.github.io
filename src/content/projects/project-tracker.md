---
title: Project Tracker
summary: A self-hosted, simpler take on Jira. Kanban boards with hard WIP limits, server-enforced authorization, and automatic deploys to a Raspberry Pi.
stack: ["TypeScript", "Fastify", "Drizzle", "PostgreSQL", "React", "Vite", "Playwright", "Docker"]
order: 1
repo: https://github.com/daagonzalez/project-tracker
---

## What it is

A small Kanban project tracker. Each project has one board of columns and
tickets. Tickets carry a description, comments, labels, story points, an
assignee, and links to things like pull requests. Columns can have a WIP
limit, and it is a hard one: a move that would exceed it is rejected. It
runs on a Raspberry Pi at home, deployed automatically on every merge to
`main`, and I use it to track my own projects.

## The problem

Jira does far more than I need, and hosted trackers want my data and a
subscription for what is essentially a board and some tickets. I wanted
something I could run myself and fully understand. It is also a deliberate
exercise in building a small product the way I would want a team to: test
first, with the rules enforced where they cannot be bypassed.

## My role

Sole developer: API, database, front end, tests, CI, and deployment.

## Technically interesting

- **Test-first, against a real database.** Every behaviour started as a
  failing test. API tests use Vitest and Fastify's `inject()` against a real
  Postgres, with no mocked database. Front-end tests use Playwright with the
  API mocked at the network edge, driving the UI by dragging, clicking, and
  typing. Authorization, WIP limits, and ordering are covered first.
- **One contract, checked from both sides.** Zod schemas in a shared package
  define every API shape. API tests validate each response against them, and
  the Playwright mock fixtures are typed and validated against the same
  schemas, so the two suites cannot drift apart without a test failing.
- **Rules live on the server.** Only members can see a project, and only the
  owner can delete it or manage members. WIP limits are checked on every
  move, and only a comment's author can edit it. Every ticket change writes
  an event in the same transaction, and tickets are archived, never deleted.
- **Fractional-index ordering.** Ticket order within a column uses
  fractional string keys, so dragging a ticket rewrites one row instead of
  renumbering the column.
- **Security without a framework doing it for me.** Server-side sessions in
  an `HttpOnly`, `Secure`, `SameSite=Lax` cookie, stored hashed in Postgres
  so they can be revoked instantly. Passwords use argon2id, with CSRF
  protection and login rate limiting. There is no public sign-up: users are
  created from a CLI command. Markdown renders without raw HTML.
- **One container, one origin.** A single multi-stage Docker image serves
  both the API and the built front end, runs as non-root, and migrates the
  database on startup. That removes CORS and keeps cookies first-party.
- **CI and automatic deploys.** CI runs lint, both test suites, `npm audit`,
  and a Docker build as separate jobs. A green merge to `main` redeploys the
  Pi over HTTPS.

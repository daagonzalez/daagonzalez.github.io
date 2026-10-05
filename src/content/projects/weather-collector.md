---
title: Weather Collector
summary: An hourly background service that builds a personal weather history in Postgres, with secrets kept in Vault instead of config.
stack: ["TypeScript", "Node.js", "PostgreSQL", "Drizzle", "Vault", "React", "Docker"]
order: 3
---

## What it is

A small service that, at the top of every hour, fetches current conditions
for the places I care about and stores them in Postgres. Over time that
builds a weather history I own. A companion React UI charts temperatures
by location over a chosen time range.

## The problem

Weather apps are good at right now and bad at "what was it like here last
month?" I wanted my own long-term record, kept in a database I can query
however I like.

## My role

Sole developer: design, implementation, and deployment.

## Technically interesting

- **Secrets never touch env vars or config files.** At startup the service
  authenticates to HashiCorp Vault with AppRole, then reads the database
  credentials and the AccuWeather API key from KV v2. The only things in the
  environment are the Vault address and the AppRole IDs, and the policy only
  grants read access to this service's own paths.
- **The domain object is the boundary.** `WeatherReading` is the only code
  that knows both AccuWeather's response shape and what gets persisted. The
  API client, the use case, and the repository each depend on it, not on
  each other, so a change on either side touches one file.
- **Easy on the API quota.** Location keys are resolved ahead of time, so
  the hourly job doesn't spend requests on location lookups.

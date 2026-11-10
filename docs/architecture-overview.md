# Architecture Overview

A modular monolith on proven managed services, with the database as the final
authority on who can see and change what.

## One Web Application

- **React 19, TypeScript and Vite.** One club portal application. Each product
  area is a module (Prize Claims is the first) built against a shared module
  contract.
- **Shared packages** for people, businesses and UI. The first time something is
  built it lives in its module; the second time, it moves to a shared package
  rather than being copied.
- **One words file and design tokens.** All on-screen wording lives in one file
  and all styling in named tokens, so wording and look can change safely
  without touching application logic.

## Sessions

Sessions are owned by the server. The browser holds a short-lived access token
in memory only, with refresh handled through an HttpOnly cookie. No bearer
tokens are ever kept in browser storage.

## Data And Permissions

- **Postgres with row-level security**, hosted on Supabase. Every table has
  row-level security, and writes go through database functions that enforce the
  rules.
- **Permissions live in the database.** Hiding a button is a convenience, never
  the security boundary.
- **Tenant isolation is tested.** Data features ship with tests that try to read
  another club's records and must fail.
- **All or nothing.** Batch work, such as creating eighteen vouchers or redeeming
  twenty, is one database transaction, with double-click protection and a
  server-side recheck of every row.
- **One owner per fact.** A data-ownership map says which module owns people,
  staff and businesses, so nothing gets copied and drifts.

## Environments

| Environment | Data | How it is built |
| --- | --- | --- |
| Local | Synthetic | Rebuilt with one command from the migrations |
| Test | Synthetic only | Rebuilt from scratch from version-controlled migrations; released with post-deploy checks |
| Production | Club records | An isolated project, built the same way and released only by separate approval |

## Decisions

37 architecture decision records explain why things are the way they are, from
web storage and session policy to the throwaway database used by the browser
checks in CI.

[Back To Documentation](README.md)

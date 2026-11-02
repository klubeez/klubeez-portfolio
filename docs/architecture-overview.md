# Architecture Overview

## Product Boundaries

klubeez has a React/TypeScript/Vite Club Portal and a separately built Prize
Claims frontend, presented through the portal's module route. Users sign in
once and navigate into their authorized module without a second login.

The platform repository owns shared Supabase migrations, tenants, identities,
memberships, the business register and backend authorization. The Prize Claims
frontend consumes those shared services rather than maintaining duplicate
identity or sponsor systems.

## Access Model

- Club administrators and staff operate within their assigned club.
- Platform Admin selects a club for cross-tenant administration.
- Staff invitations, voucher display and Activity Log require administrator access.
- Prize Claims staff need no membership roster record or playing account.
- Backend authorization and database policies enforce access; UI visibility is
  not the security boundary.

The portal's session broker supports module access with a memory-only access
token and an HttpOnly refresh cookie. Direct module-origin visits return to the
portal. Historical authentication samples in this portfolio are not the current
portal implementation.

## Delivery Boundaries

Vercel hosts the web frontends; Supabase provides shared data and authentication.
Local work and hosted Dev testing precede separately approved hosted promotion.
Production preparation is not the same as a declared launch.

The application repositories contain CI and release procedures. This public
portfolio is documentation and illustrative samples only: it contains no
deployable application, complete dependency graph or working CI workflow.

[Back To Portfolio](../README.md)

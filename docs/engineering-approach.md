# Engineering Approach

This is a public summary, not an executable runbook. The private working
repositories own the detailed rules and validation commands.

## Small, Testable Changes

Agree the supported workflow and acceptance criteria before implementation.
Prefer existing patterns and focused changes over broad rewrites. Develop and
test locally first; use explicit, practical steps for human acceptance.

## Evidence Before Handoff

Application checks include formatting, linting, type checking, automated tests,
builds and security checks as required by the affected scope. UI work needs
relevant browser verification. Data work needs evidence of the actual stored
result and access boundaries, not just a successful-looking screen.

State what was tested and what was not. Do not fabricate records or hide
failures to produce a convincing screenshot. Keep synthetic fixtures distinct
from private club data. Update in-app Help when user-facing behavior changes.

## Bounded Review

Assess findings against a real actor, supported sequence and observable impact.
Fix failed acceptance, meaningful correctness issues, security/privacy boundary
defects and data-loss risks. Record justified deferrals or rejections instead
of extending review indefinitely to satisfy speculative scenarios.

## Human-Controlled Delivery

Work on a task branch and deliver a pull request to `feature-dev`. Pete owns
merges and acceptance. Approval to change code does not authorize deployment,
hosted data mutations or destructive repair. Hosted rollout requires separate
approval and verification of the deployed result.

## Portfolio Validation

This repository has no application package or CI workflow. Documentation changes
can be checked for formatting, valid local links, image rendering and accidental
private content. Those checks must not be described as application tests or
proof of a production release.

[Back To Documentation](README.md)

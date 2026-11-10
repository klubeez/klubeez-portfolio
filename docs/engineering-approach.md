# Engineering Approach

Codex writes the code. Claude reviews it, read-only. Machines check everything
that can be checked. A person merges. Nothing reaches a club without passing
every stage below, and each stage leaves evidence behind.

## The Ten Stages

1. **Story and expected outcome.** Every task starts as a user story with
   acceptance criteria and a written expected outcome.
2. **Plan review.** Claude Code challenges the plan against the real source. It
   can only read: no shell, no edits, no secrets, proven with a canary before its
   first review.
3. **Build.** Codex implements the smallest agreed increment on a branch, with
   focused tests that assert the accepted contract.
4. **Quality gates.** Formatting, lint, type checks, the full automated test
   suite, production build, security configuration check, dependency audit.
5. **Browser smoke.** Playwright runs the key club workflows against a throwaway
   Postgres built from the migrations, in CI, on every change.
6. **Visual parity.** Screens are captured at 1280, 1440 and 1920 wide with
   synthetic data and compared against the approved design pack.
7. **Candidate review.** Claude reviews the actual diff and test evidence. At
   most three rounds, then one check-only pass.
8. **Required checks.** `quality-gates`, `browser-smoke`, `quick-scope` and
   `quick-visual`, from GitHub Actions only, with branches up to date and rules
   enforced for administrators. Conversations must be resolved before a merge.
9. **Human merge.** No agent can merge or push to the main branches. The
   product owner tests locally against a written test guide, then merges.
10. **Release.** Test first, on synthetic data, with post-deploy checks.
    Production is a separate, named approval.

## Bounded Review

- **The Reality Gate.** Before a finding is acted on, the reviewer names the
  actor, the exact sequence, the visible outcome and the boundary at risk.
  Findings that need customers or traffic that don't exist are rejected. Real
  security, privacy and data risks never are.
- **Fix, defer or reject.** Failed acceptance, real security or privacy defects,
  data loss and broken operations are fixed. Genuine but non-blocking
  improvements are deferred with a backlog link. Incorrect or speculative
  findings are rejected with reasons.
- **Severity with teeth.** P0 stop · P1 prompt fix · P2 may block · P3 minor. A
  label is not proof, and a failed acceptance criterion blocks whatever its
  severity. Protected risk can only be accepted by the product owner, in writing.

## Evidence Over Assertion

- Test claims name actual runs; code claims cite files.
- Every feature staff use has a written test guide, and every run is saved with
  who tested it, on which build and with what result.
- Every change that affects what staff see updates its Help in the same pull
  request, or says why none was needed.
- Synthetic data only, in tests, screenshots and evidence.

## The Quick-Change Channel

`kz` makes wording, colour and component-style changes from one terminal
command. Each change is previewed at several widths, checked locally, opened as
a pull request, inspected by a trusted scope check that runs only main-branch
code and treats the change as data, merged under the owner's account and
deployed to Test. It refuses page code, links and layout, broken placeholders,
low contrast, hidden content, approval piped from a script, releasing unfinished
work, and Production by accident. `kz undo` reverses the last change through the
same lane.

[Back To Documentation](README.md)

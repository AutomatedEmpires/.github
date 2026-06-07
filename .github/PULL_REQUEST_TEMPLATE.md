## What & why
<What does this change and why?>

## Linked issue / source of truth
Closes #

Notion / canon reference:

## Risk
- [ ] risk:low
- [ ] risk:medium
- [ ] risk:high
- [ ] risk:approval-required

Founder-gated area touched?
- [ ] No
- [ ] Yes — money / auth / destructive DB / permissions-RLS / trust-safety / legal / asset-license / launch / product-philosophy

## Verification
- [ ] CI green (typecheck, lint, guardrails, build, test)
- [ ] Smoke / manual QA recorded when UI, auth, admin, billing, or public routing changed
- [ ] No local verification needed because this is docs-only or config-only

## Safety checklist
- [ ] No new icon-library imports (G30)
- [ ] DB changes follow expand/contract (no additive + destructive in one release)
- [ ] RLS policies updated/tested if data model changed
- [ ] Admin/service-role paths are server-gated, never client-only
- [ ] No secrets in code, logs, fixtures, screenshots, or comments
- [ ] Builder is not the sole approver

## Agent assist (optional)
<!-- @copilot  @sentry  /review sentry <prompt>  /git-agent <prompt> -->

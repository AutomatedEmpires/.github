# Governance

How decisions get made and shipped across AutomatedEmpires.

## Doctrine

> **Notion decides and builds. GitHub reviews and ships. Figma shows. Everything else runs.**

- **Notion** — product, vision, journal, canon, and work-intent truth.
- **GitHub** — implementation truth: code, tests, CI, review, release history.
- **Figma** — visual truth and design validation.
- **Providers** (Supabase, Clerk, Stripe, Vercel, PostHog, Sentry, Mapbox, Cloudinary, Doppler) — run the system.

## Roles

- **Founder** — sets direction, owns canon, holds all founder-gated decisions, and is the final approver.
- **Maintainers / human contributors** — implement, review, and merge within their lane.
- **Agents** — the AI fleet. They file, draft, label, review, and dispatch. They never merge, deploy, checkout, or mutate product code on their own, and they never weaken security.

## Decision authority

Locked decisions are dated and recorded in canon (Notion) and mirrored to the repo decision log where one exists. A proposal is a **candidate** until the founder approves it; only then does it become **locked**.

Founder-gated areas — no change ships without explicit founder approval:

- Money (pricing, payments, payouts)
- Auth, permissions, and RLS
- Destructive database changes
- Trust, safety, and legal
- Asset licensing
- Launch and deploy
- Product philosophy and canon

## Risk lanes

| Lane | Who acts | Gate |
| --- | --- | --- |
| `risk:low` | Agents may open PRs autonomously | CI gates merge |
| `risk:medium` | Agent drafts | Human reviews before merge |
| `risk:high` / `risk:approval-required` | Founder approval required before any code change | Human approval |

## Merge gates

- The builder is never the sole approver.
- Never merge with red CI.
- Never bypass branch protection.
- Every material PR states risk, verification, and source-of-truth alignment.
- Large product PRs stay draft until CI is green and smoke verification is recorded.

## Changing this model

Governance changes are themselves founder-gated. Repo-level governance may tighten these rules but may never loosen them.

## Rollout standard

A venture is rollout-complete only when its `AGENTS.md`, CI, agent routing, runtime pins, security posture, and Notion ⇄ GitHub alignment all match the org contract — or carry an explicit, dated exception.

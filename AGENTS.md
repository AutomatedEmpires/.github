# AutomatedEmpires — Agent Operating Manual

This file is the org-level operating contract for every AI agent and human contributor working in AutomatedEmpires repositories. Repo-level `AGENTS.md` files may extend this manual, but they may not loosen it.

## Doctrine

**Notion decides and builds. GitHub reviews and ships. Figma shows. Everything else runs.**

- Notion holds product, vision, journal, canon, and work-intent truth.
- GitHub holds implementation truth: code, tests, CI, PR review, release history.
- Figma holds visual truth and design validation.
- Providers such as Supabase, Clerk, Stripe, Vercel, PostHog, Sentry, Mapbox, Cloudinary, and Doppler run the system.

## Stack — the golden path

- TypeScript, Next.js App Router, Turborepo where app complexity warrants it.
- Supabase Postgres (+ PostGIS where spatial logic exists).
- Clerk auth; Supabase RLS keyed on Clerk `sub`.
- Mapbox for production maps.
- Stripe / Stripe Connect where the business model requires payments or payouts.
- Vercel for deploys.
- Doppler for secrets.
- PostHog for analytics and feature flags.
- Sentry for errors and release risk.
- Cloudinary for media where managed transformation/asset workflows are needed.
- Single icon system only through the repo's shared icon registry. Do not import lucide, heroicons, react-icons, Font Awesome, or MUI icons directly.

## Runtime — pin everywhere

- Node `24.16.0`
- pnpm `10.12.4`
- Commit lockfiles.
- CI installs with `pnpm install --frozen-lockfile` unless a repo has an explicitly documented exception.

## Work routing

- File build work as a GitHub issue titled `[build] ...` using the Build Task template.
- Fill `## Area`, `## Suggested agent`, and `## Risk level` with one allowed label each.
- The agent-build-task-router applies routing labels automatically.
- On PRs, route agent help with:
  - `@copilot` for GitHub Copilot review / cloud side-loop.
  - `@sentry` or `/review sentry <prompt>` for release-risk / monitoring review when configured.
  - `/git-agent <prompt>` or `/agent git <prompt>` for deterministic git/worktree help when configured.
- Claude is handled by its dedicated Claude workflow where installed. Do not also route Claude through the generic PR router.
- Codex is retired org-wide as of 2026-06-06. Do not add Codex labels, secrets, workflows, or PR commands.
- Only OWNER, MEMBER, and COLLABORATOR comments are honored by routers.

## Risk lanes

- `risk:low` — agents may open PRs autonomously; CI gates merge.
- `risk:medium` — agent drafts; human reviews before merge.
- `risk:high` / `risk:approval-required` — human approval required before any code change.

Founder-gated areas: money, auth, destructive database changes, permissions/RLS, trust/safety, legal, asset licensing, launch/deploy, and product philosophy.

## Required PR posture

- Builder is never the sole approver.
- Never merge with red CI.
- Never bypass branch protection.
- Every material PR must state risk, verification, and source-of-truth alignment.
- Large product PRs should stay draft until CI is green and smoke verification is recorded.

## Hard rules

- Never weaken RLS or expose secrets in code, logs, fixtures, screenshots, or issue comments.
- Database migrations follow expand/contract; never combine additive and destructive changes in one release.
- Service-role keys are server-only and never `NEXT_PUBLIC_`.
- Routers never merge, deploy, checkout, or mutate product code. They only label, acknowledge, and dispatch.
- Product/provider candidates must be marked **candidate**, not **locked**, until founder approval creates a dated decision.

## World-class operating-system target

The org operating system is considered healthy when every active venture has:

1. `AGENTS.md` aligned to this manual.
2. Node/pnpm pins aligned.
3. Shared CI or a documented equivalent.
4. Agent routing without retired agents or double triggers.
5. A clear Notion ⇄ GitHub canon mirror / dispatch path.
6. Evidence-producing verification: CI URL, build result, smoke result, and review status stored durably in GitHub and mirrored to Notion when available.

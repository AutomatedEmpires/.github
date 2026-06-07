# AutomatedEmpires — Agent Operating Manual

This file sets the baseline rules for every AI agent working in this org.
Repo-level AGENTS.md files may extend, but not loosen, these rules.

## Doctrine

- Notion decides and builds. GitHub reviews and ships. Figma shows. Everything else runs.
- Notion is product truth. Repositories implement and ship that canon.

## Machine reality

- Windows 11 ARM64 (Snapdragon X Elite) → WSL2 Ubuntu 24.04 → VS Code
- 16 GB RAM. One heavy task at a time. No parallel installs/builds/watchers.

## Stack (the golden path)

- TypeScript, Next.js (App Router), Turborepo
- Supabase Postgres (+PostGIS), Clerk auth, Supabase RLS keyed on Clerk `sub`
- Mapbox (production maps), Stripe (+Connect where needed)
- Vercel (deploy), Doppler (secrets), PostHog (analytics/flags), Sentry (errors)
- Single icon system only (shared registry) — no lucide/heroicons/react-icons/fontawesome/mui-icons

## Runtime (pin everywhere)

- Node 24.16.0 · pnpm 10.12.4
- Commit lockfiles. CI installs with --frozen-lockfile.

## Locked providers

- Auth: Clerk
- Maps: Mapbox
- Secrets: Doppler
- Hosting: Vercel
- Analytics: PostHog
- Errors: Sentry
- Media: Cloudinary
- Email: Resend
- Icons: Streamline

## How work is routed

- File a build task as a GitHub Issue titled `[build] ...` using the Build Task template.
- Fill `## Area`, `## Suggested agent`, `## Risk level` with one allowed label each.
- The agent-build-task-router applies labels automatically.
- On PRs, trigger agents via comment: `@codex`, `@claude`, `@sentry`, `@copilot`,
  or `/agent <name> <prompt>`, `/review <name>`, `/git-agent <prompt>`.
- Only OWNER/MEMBER/COLLABORATOR comments are honored.

## Risk lanes

- risk:low — agents may open PRs autonomously; CI gates merge.
- risk:medium — agent drafts, human reviews before merge.
- risk:high / risk:approval-required — human approval required before any code change.

## Hard rules

- Never push straight to main. Work on feature branches, open small PRs, request review, and do not self-merge.
- Never weaken RLS or expose secrets in code or logs.
- Never merge with red CI. Never bypass branch protection.
- Database migrations follow expand/contract; never additive + destructive in one release.
- Routers never merge, deploy, checkout, or mutate code.
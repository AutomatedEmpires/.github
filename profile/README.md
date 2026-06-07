# AutomatedEmpires

**An AI-native venture studio.** One founder. One closed-loop development system. A portfolio of map-first marketplaces built in parallel by a fleet of AI agents under human command.

We don't staff teams — we compound systems. Product truth lives in Notion. Implementation truth lives in GitHub. Design truth lives in Figma. Agents do the work; the founder sets direction and holds the gates.

## The operating doctrine

> **Notion decides and builds. GitHub reviews and ships. Figma shows. Everything else runs.**

Every venture inherits the same spine — a shared agent contract, reusable CI, security posture, and routing — defined once in this repository and propagated to every repo.

## Ventures

| Product | What it is | Status |
| --- | --- | --- |
| **Explore & Earn** | A discovery marketplace built by seekers, for seekers. | In active build |
| **BidSpace** | A map-first bidding marketplace for temporary commercial inventory — hosts list, bidders compete in sealed auctions, and the platform handles discovery, verification, and settlement. | In active build |
| **Sweepza** | A clean, photo-first sweepstakes discovery app — visual, fast, structured, and trust-oriented. | In active build |
| **LogLoads** | The timber-truck operating network — connecting drivers, outfits, and loaders to coordinate hauls in real time. | In active build |

## How we build

- **Stack:** TypeScript · Next.js (App Router) · Turborepo
- **Data:** Supabase Postgres (+ PostGIS for spatial) with row-level security keyed to identity
- **Identity & maps:** Clerk auth · Mapbox
- **Payments & delivery:** Stripe / Stripe Connect · Vercel
- **Observability:** PostHog (analytics + flags) · Sentry (errors + release risk)
- **Secrets & media:** Doppler · Cloudinary
- **Runtime, pinned everywhere:** Node 24.16.0 · pnpm 10.12.4

## How the machine runs

- Work is filed as GitHub issues and routed to the right agent by label.
- A multi-agent fleet drafts, reviews, and ships through pull requests.
- CI, guardrails, and templates are inherited from this org config repo — no repo starts from zero.
- Humans hold the gates on money, auth, data, trust, and launch.

> **Portfolio:** automatedempires.com *(coming soon)*

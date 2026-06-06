# Security Policy

## Reporting

Email security reports privately to the maintainer. Do not open public issues for vulnerabilities.

## Scope

All AutomatedEmpires repositories and deployed apps.

## Expectations

- Secrets live in Doppler / GitHub Actions secrets — never in code.
- Supabase RLS is enforced on every table keyed to Clerk identity.
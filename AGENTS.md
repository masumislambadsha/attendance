# Attendance system

Office Attendance System — an attendance/QR-check-in app.

- Product spec: `Office Attendance System — PRD.md` (read it; it drives feature decisions, incl. §15 acceptance tests).
- The runnable project is in `app/` (Next.js). Start there: read `app/AGENTS.md`, `app/README.md`, `app/package.json`.
- The git repo, lockfile, and all source live inside `app/`; this root is not a git repo.
- Implementation reality diverges from the PRD's examples: the app is **MongoDB + better-auth**, not Supabase. Trust code over prose.

## Quick reference

- Dev: `cd app && npm run dev` (Next.js 16, App Router, React 19, Tailwind v4, shadcn-style UI).
- Lint: `npm run lint`. Typecheck: `npx tsc --noEmit`. Tests are not wired into npm — run `node scripts/test-status.ts` (Node 20.11+ type-stripping; a no-op `node --watch` warning is expected).
- Config: copy `app/.env.example` → `app/.env.local`; `.env*` is gitignored. Requires a real `MONGODB_URI` (Atlas). `scripts/` bootstraps indexes, demo users, app user.
- Timezone: all business logic is **Asia/Dhaka**, no DST; date keys are `YYYY-MM-DD` strings.
- New feature work gets uncommitted/staged in `app/`; there is no CI config.
# Loan Officer Self-Service Portal

**Status:** IMPLEMENTED — PR #17
**Date:** 2026-03-19
**Author:** Evan (CEO review with Claude)
**Branch:** TBD (not yet created)

---

## Problem

Every employee with a Keystone login sees the full admin view — same sidebar, same data, same pages. An LO can see other employees' commission reports, access accounting, run commissions, and change company settings. This is a security issue (data leakage) and a UX issue (information overload).

## Outcome

1. LOs and ops staff get a personal portal scoped to their own data
2. Admins retain full access to everything
3. Branch managers see their branch team's data
4. Companies configure what non-admin employees can access
5. The experience is clean and purposeful — not just the admin view with things hidden

## Approach

**Boolean Admin Flag + JSON Portal Permissions** (Approach A from CEO review)

- Add `isAdmin: Boolean @default(true)` to Employee model
- Add `portalPermissions: Json @default("{}")` to Company model
- Code-side defaults (empty JSON + merge with hardcoded defaults)
- Default-true means zero disruption — all existing employees remain admins until explicitly changed
- Same routes, different nav — no separate route group

## Accepted Scope (from CEO review)

### Core Plan (8 phases)
1. Schema & auth foundation (isAdmin, portalPermissions, verifyAccess extension)
2. Portal permissions admin UI (checkbox grid: roles × features)
3. Navigation & layout (filtered sidebar, EmployeeProvider context)
4. Personal dashboard (stat cards, goals, tasks, recent funded)
5. Scoped data access (loans, reports, analytics, tasks, goals)
6. Route protection (admin-only page guards)
7. Employee management UI (isAdmin toggle)
8. Polish & edge cases

### Accepted Expansions (+6)
1. **"View as Employee" mode** — Admin can see exactly what any employee sees. Query param `?viewAs=employeeId`, read-only impersonation. (S effort)
2. **Commission calculation breakdown** — Expandable "How was this calculated?" on employee report page showing matched rule, tier, formula, math. (M effort)
3. **Personal activity feed** — Dashboard timeline: loan status changes, task assignments, report publications, goal milestones. (M effort)
4. **Self-service goal setting** — LOs create personal production goals, track progress on dashboard, BMs see team goals. (S effort)
5. **Welcome flow** — First-time modal for new non-admin employees + confirmation dialog when admin toggles isAdmin. (S effort)
6. **Routing defense-in-depth** — Layout-level route enforcement (ADMIN_ROUTES constant) as belt-and-suspenders with per-page guards. (S effort)

## Architecture

Three layers of access control:
1. **Layout enforcement** — `[companySlug]/layout.tsx` checks route against ADMIN_ROUTES list
2. **Page guards** — `requireAdmin(slug)` at top of admin-only page components
3. **Action guards** — `verifyAccess(slug).isAdmin` check in every mutation server action

## Key Decisions

| Decision | Choice | Rationale |
|---|---|---|
| Implementation approach | Boolean + JSON | Minimum abstraction, follows existing patterns |
| Permission defaults | Code-side | Flexible, no migration complexity |
| Deploy strategy | Single deploy with `isAdmin ?? true` fallback | One deploy, zero risk |
| viewAs mutations | Always use real admin identity | Audit trail integrity |
| Branch manager scope | Self + all employees in managed branches | Matches existing managedBranches relation |

## Security Requirements

- IDOR protection: `assertSelfOrAdmin` on all employee-scoped data
- Last admin protection: prevent removing the only admin
- viewAs server-validated: admin-only, same company, not archived
- Every mutation action: `requireAdmin` check (not just page-level)
- Zod schema for portalPermissions JSON structure

## Files

**~10 new files, ~30 modified files.** See original plan for full file list.

## Deferred (in TODOS.md)

- Profile menu quick stats (P3)
- Per-employee permission overrides (P2)
- Processor-specific dashboard (P2)
- Mobile-first LO portal (P3)
- Custom role definitions (P3)
- Field-level permissions (P3)
- Full audit trail (P3)
- Notification system (P2)

## Reviews

- [x] CEO Review — 2026-03-19, CLEAR, SCOPE EXPANSION mode
- [x] Eng Review — 2026-03-19, CLEAR, FULL_REVIEW mode
- [x] Design Review — 2026-03-19, CLEAR, 9/10 overall score
